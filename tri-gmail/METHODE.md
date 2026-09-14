# Tri de la boîte Gmail de Tanguy Lys — méthode et état

Compte : `lystanguy@gmail.com`. Reprise de la passation du 14 septembre 2026.

## 1. Méthode qui marche (à réutiliser)

### Le connecteur Gmail ne sait poser un libellé que sur un fil à la fois
Pas de `batchModify`, pas de création de filtre Gmail via l'outil. En revanche,
Claude Code peut émettre **25 appels `label_thread` en parallèle dans un seul
tour**, et `label_thread` accepte **plusieurs libellés par appel**. Le débit réel
est donc d'environ 25 fils par tour, pas 1.

### `-label:Label_X` ne fonctionne pas dans la recherche
L'exclusion par identifiant de libellé est ignorée silencieusement : la requête
renvoie les fils déjà étiquetés. **Utiliser `has:nouserlabels`**, qui isole les
fils jamais traités.

Conséquence très utile : une fois un lot étiqueté, il sort de la requête. Il
suffit donc de **relancer la même requête sans `pageToken`** pour obtenir le lot
suivant. Le tri devient reprenable et sans état, et les jetons de pagination
non durables ne posent plus problème.

### Les catégories sont additives
Chaque catégorie se traite par une passe indépendante (par expéditeur ou par
mot-clé). Un fil qui relève de deux catégories reçoit naturellement ses deux
libellés au fil des passes. Inutile d'arbitrer les doubles appartenances d'avance.

### Quand une recherche dépasse le contexte
`search_threads` écrit alors le JSON dans un fichier et renvoie son chemin.
L'extraire avec `jq` plutôt que de le relire :

```
jq -r '.threads[] | .id + " | " + (.messages[0].subject // "(sans objet)") + " | " + (.messages[0].snippet // "")' FICHIER
```

C'est la voie à privilégier pour Publicité et Abonnements.

### Vues
`THREAD_VIEW_METADATA_ONLY` quand l'expéditeur suffit à trancher (léger).
`THREAD_VIEW_MINIMAL` quand il faut l'objet et l'aperçu.
`get_thread` en `MINIMAL` pour lever un doute sans charger les pièces jointes.

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

### Adresses famille, liste complétée
Aux cinq adresses connues s'ajoute **`isabelle.lys@maif.fr`** (la mère, encore
une autre adresse). La requête famille doit couvrir les six.

### Adresse secondaire de Tanguy
**`jeuxdetanguy@gmail.com`** est une adresse de Tanguy lui-même, pas un tiers.

### Tanguy s'envoie ses cours à lui-même
Plusieurs fils `lystanguy@gmail.com` → `lystanguy@gmail.com` sans objet sont des
**prises de notes de cours** (droit constitutionnel, juridictions, souveraineté).
Ne pas les confondre avec des brouillons : ils vont dans Cours.

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

## 4. Question ouverte pour Tanguy : une catégorie manque

Une dizaine de fils relèvent d'un **engagement politique** (Rassemblement
National Jeunesse, fonction de délégué départemental jeunesse, démission de
cette fonction, plan d'action RNJ, matériel et événements). Cela ne rentre dans
aucune des neuf catégories définies.

Ces fils sont pour l'instant dans **À vérifier**. Il faudrait soit créer un
libellé dédié, soit décider de les verser dans Perso.

## 5. Autres cas déposés dans À vérifier

- `195edc9e94737fad` CV à Olivier Alemany transféré au père (déjà signalé)
- `1940cb6abf28bb84` échange avec la gendarmerie, objet « Photo menace Lys »
- `19dbadd03bce6319` envoi à un service de reprographie, contenu non identifié
- fils sans objet ni aperçu, contenu uniquement en pièce jointe
