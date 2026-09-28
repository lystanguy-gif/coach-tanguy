# Tri de la boîte Gmail de Tanguy Lys — méthode

Compte : `lystanguy@gmail.com`. Méthode issue de la passation du 14 septembre
2026 et de deux sessions de traitement complet. Elle est réutilisable telle
quelle pour entretenir la boîte ou trier une autre boîte.

## 1. Méthode qui marche

### Le connecteur Gmail ne sait poser un libellé que sur un fil à la fois
Pas de `batchModify`, pas de création de filtre Gmail via l'outil. En revanche,
Claude Code peut émettre **50 appels `label_thread` en parallèle dans un seul
tour**, et `label_thread` accepte **plusieurs libellés par appel**. Avec un tour
de recherche pour un tour d'étiquetage, le débit réel est d'environ **50 fils
pour deux tours**.

### `-label:Label_X` ne fonctionne pas dans la recherche
L'exclusion par identifiant de libellé est ignorée silencieusement : la requête
renvoie les fils déjà étiquetés. **Utiliser `has:nouserlabels`**, qui isole les
fils jamais traités.

Même remarque pour la sélection : `label:Label_3` ne renvoie rien non plus. Pour
compter les fils d'un libellé, passer par **`list_labels`**, qui donne
`threadsTotal` et `messagesTotal` exacts pour chaque libellé.

### La boucle est sans état, donc reprenable
Une fois un lot étiqueté, il sort de `has:nouserlabels`. Il suffit donc de
**relancer la même requête sans `pageToken`** pour obtenir le lot suivant. Les
jetons de pagination ne servent jamais.

Effet secondaire précieux : **la boucle se répare toute seule**. Le connecteur
renvoie de temps en temps « The service is currently unavailable » sur un appel
isolé. Le fil concerné n'est simplement pas étiqueté, donc il réapparaît en tête
du lot suivant et sera repris. Rien à faire, ne pas réessayer à la main.

### Découper la boîte en partitions natives avant de ratisser
Traiter d'abord les catégories Gmail une par une, chacune jusqu'à épuisement,
puis le reste. C'est ce qui rend le volume tenable, car chaque partition est
homogène et se tranche presque toujours sur le seul expéditeur :

```
in:inbox has:nouserlabels category:promotions
in:inbox has:nouserlabels category:updates
in:inbox has:nouserlabels category:social
in:inbox has:nouserlabels category:forums
in:inbox has:nouserlabels
```

### Savoir quand une partition est épuisée
`resultCountEstimate` est **plafonné à 201**. Il ne descend en dessous que
lorsqu'il reste moins de deux cents fils. Une valeur inférieure à 201 est donc
le signal fiable de fin de catégorie ; la recherche suivante renvoie `{}`.

### Les catégories sont additives
Chaque passe est indépendante. Un fil qui relève de deux catégories reçoit
naturellement ses deux libellés au fil des passes. Inutile d'arbitrer les
doubles appartenances d'avance.

### Vues
`THREAD_VIEW_METADATA_ONLY` suffit pour les expéditeurs automatiques en masse :
l'adresse tranche seule, et la vue est légère.

**`THREAD_VIEW_MINIMAL` est indispensable pour la passe finale
`in:inbox has:nouserlabels`.** Ce reliquat contient de la correspondance
personnelle, où l'adresse ne dit rien. C'est en lisant l'objet et l'aperçu qu'on
découvre par exemple que `maisonfamille05160@gmail.com` signe « Maman » (voir
§ 3). Sans l'objet, ce fil serait parti dans À vérifier.

`get_thread` en `MINIMAL` pour lever un doute sans charger les pièces jointes ;
`FULL_CONTENT` seulement quand le détail est nécessaire (le contenu d'un reçu
Apple, par exemple, n'apparaît pas autrement).

### Quand une recherche dépasse le contexte
`search_threads` écrit alors le JSON dans un fichier et renvoie son chemin.
L'extraire avec `jq` plutôt que de le relire :

```
jq -r '.threads[] | .id + " | " + (.messages[0].subject // "(sans objet)") + " | " + (.messages[0].snippet // "")' FICHIER
```

### Deux règles de tranchage
**Hésitation entre Publicité et Abonnements → Abonnements.** Tanguy envisage de
supprimer le lot Publicité ; mieux vaut garder un prospectus que perdre une
facture.

**Doute réel → À vérifier.** Ne jamais deviner : politique, administratif,
correspondants inconnus, tout ce qui ne rentre pas proprement dans les neuf
catégories y est garé pour relecture avec Tanguy.

## 2. Libellés

| Nom | ID |
|---|---|
| Famille | `Label_3` |
| Cours | `Label_4` |
| Publicité | `Label_5` |
| Abonnements | `Label_6` |
| À vérifier | `Label_7` |
| Pro | `Label_8` |
| Banque | `Label_9` |
| Assurance et Santé | `Label_10` |
| Fac | `Label_11` |
| alternance chaudronnerie recherche | `Label_1056626620922916008` |
| canada | `Label_2781539145621125201` |
| pole emploi | `Label_381039744810206638` |
| job | `Label_650244966076941553` |
| Perso | `Label_7861695343511741030` |
| administratif | `Label_7919117525769367201` |
| CAF | `Label_8093676200740780489` |

## 3. Corrections et découvertes par rapport à la passation

### `maisonfamille05160@gmail.com` est la mère
Cette adresse, qui ne ressemble à rien, **signe « Maman »**. Elle ne figurait
dans aucune des listes de la passation. Elle va dans **Famille**.

### Adresses famille, liste complétée
Aux cinq adresses connues s'ajoutent **`isabelle.lys@maif.fr`** (la mère, encore
une autre adresse) et `maisonfamille05160@gmail.com` ci-dessus.

### Piège signalé par la passation, confirmé
**`isa.said5690@gmail.com` n'est pas la mère**, c'est une camarade de droit.
Ne pas la classer en Famille.

### Adresse secondaire de Tanguy
**`jeuxdetanguy@gmail.com`** est une adresse de Tanguy lui-même, pas un tiers.

### Tanguy s'envoie ses cours à lui-même
Plusieurs fils `lystanguy@gmail.com` → `lystanguy@gmail.com` sans objet sont des
**prises de notes de cours** (droit constitutionnel, juridictions, souveraineté).
Ne pas les confondre avec des brouillons : ils vont dans Cours. Idem pour
`math.dugelay@orange.fr`, objet « Cours ».

### Léa Brun n'est pas de la famille
**`brunlea32@gmail.com`** (Léa Brun) est la compagne de Tanguy. Classée Perso,
pas Famille, la catégorie Famille étant définie comme la correspondance avec les
parents.

### Il a étudié à Limoges avant Toulon
Les camarades en `@etu.unilim.fr` (Université de Limoges) sont des camarades de
L1 droit 2025-2026. La passation ne mentionnait que Toulon.

### Camarades de cours absents de la liste de la passation
```
hanaecazorla@gmail.com        erwanchevalier530@gmail.com
Chevaliererwan972@gmail.com   ksaid280290@gmail.com
mazet.francois@gmail.com      schaeferpierre18@gmail.com
titiniho@outlook.com          mariontissier@outlook.fr
romain.mania312006@gmail.com  salytogola8@gmail.com
malandajustine593@gmail.com   malandajustine.ads@gmail.com
daouya87@gmail.com            laura.chtl21@gmail.com
INES081207@gmail.com          Sepulcremarie7@gmail.com
fatimachikhi2006@gmail.com    gloria.johnson63207@gmail.com
lacrouxlena3@gmail.com        issa.said@etu.unilim.fr
lilou.julliard@etu.unilim.fr  layreloupe@gmail.com
auroredelavet@gmail.com       samira.meziani0111@gmail.com
vergizovmark@gmail.com        Yeray.b81@gmail.com
```

### Camarades découverts en septembre 2026
Tanguy a diffusé ses cours de L1 droit en PDF à toute sa promo, et reçoit en
retour des cours d'économie. Ces adresses vont dans **Cours** :
```
leyna.trk11@gmail.com          lynamlant@gmail.com
plottonclara@gmail.com         fmadadelhadda@gmail.com
nell.lfrt@gmail.com            quentinmiraglio@gmail.com
milanasarma123@gmail.com       valentine22062008@gmail.com
elysa.malki@gmail.com          elora.loyseau@outlook.fr
riachi.lea@gmail.com           bertillerichard16@gmail.com
martelstella26@gmail.com       lolakahal30@gmail.com
anaspro.nouir@gmail.com        louis.ratajski2607@gmail.com
gaetan.jouard83@gmail.com      jujudesana@gmail.com
malikrejraji@gmail.com         calybarnous@yahoo.com
emmalouise.munoz@gmail.com     mariabsntana@gmail.com
ambretheosic@gmail.com         melinanys1804@gmail.com
roubachesonia22@gmail.com      jade.sev26@gmail.com
annaoddone2607@gmail.com       yasminemchichou609@gmail.com
nfti.sarah@gmail.com           ilyess080608@yahoo.com
alicia.valenzou@gmail.com      andynapoleon11@gmail.com
Julie27058@gmail.com           davidmusset05@gmail.com
missaouiines342@gmail.com
```

### `drive-shares-dm-noreply@google.com` va dans Cours, pas dans Abonnements
Ces messages sont les demandes d'accès au dossier Drive **« Révisions Droit L1
(PDF) »** envoyées par les camarades. C'est du partage de cours, pas une
notification de service.

### Autres expéditeurs nouveaux
- `contact@helloasso.com` → **Abonnements** ; le mail de paiement d'adhésion
  (« Tous en droit nouvelle génération », association étudiante de droit) porte
  en plus **Banque** et **Fac**
- `invoice+statements@stripe.com` → **Banque** (reçus Eleven Labs)
- `no-reply@softy.pro` → **Pro** (Genesis RH, suppression de données de
  candidature)
- `annonce@compte.lesjeudis.com` → **Pro**

### Une erreur de routage à corriger
`contact@exchange-college.com` a d'abord été envoyé dans À vérifier sur la seule
foi de l'adresse. Les objets (« formations en banque, finance et assurance »,
« session d'information et d'admission ») montrent que c'est **une école** : les
fils suivants sont partis dans Fac. Trois fils restent à déplacer.

## 4. État et questions ouvertes

Voir `ETAT.md` : compteurs finaux, et les trois décisions qui attendent Tanguy
(catégorie politique manquante, catégorie Canada / Québec manquante, recoupement
des libellés préexistants `job` / `pole emploi` / `alternance chaudronnerie
recherche` / `CAF` / `administratif` avec les nouveaux).
