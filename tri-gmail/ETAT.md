# État du tri — boîte Gmail de Tanguy Lys

Dernière mise à jour : 14 septembre 2026, fin de la seconde session.

## Objectif en cours : vider la réception principale

Tanguy a demandé que **tout sorte de la réception principale** — y compris ce
qui n'est pas de la publicité de démarchage — chaque fil restant accessible sous
son libellé. La Publicité reste groupée sous `Label_5` : c'est le lot dont la
suppression complète sera décidée plus tard.

Archiver n'est pas supprimer : le fil quitte la principale, reste sous son
libellé et dans « Tous les messages », et revient d'un clic.

Deux chemins, décrits dans `FILTRES-GMAIL.md` :

- **le plus rapide** : sur ordinateur, tout sélectionner dans la principale →
  Archiver. Une seconde pour les ~5 000 fils.
- **le durable** : les filtres, avec « Ignorer la boîte de réception » +
  « Appliquer aussi aux N conversations ». Traite l'historique *et* le courrier
  à venir.

Un archivage fil par fil via le connecteur est possible mais demande une
autorisation par appel dans Claude Code ; il faut d'abord répondre
« Yes, and don't ask again » à la demande d'autorisation, sinon c'est
inutilisable à cette échelle.

## Avancement de l'archivage au 28 septembre 2026

**59 fils archivés**, sortis de la réception principale. **51 nouveaux mails
reçus entre le 14 et le 18 septembre ont été étiquetés** (beaucoup de cours
d'économie et de droit échangés avec la promo, voir `METHODE.md` § 3).

L'archivage fil par fil via le connecteur Gmail **n'est pas viable à cette
échelle dans cette session** : le connecteur se déconnecte après chaque appel,
ce qui ramène le débit à un fil par tour et relance la demande d'autorisation à
chaque reconnexion. Il reste environ 5 000 fils.

Les deux chemins qui marchent, décrits en détail dans `FILTRES-GMAIL.md` :

1. **Tout sélectionner → Archiver**, sur ordinateur. Dix secondes pour les
   ~5 000 fils.
2. **Les huit filtres**, avec « Ignorer la boîte de réception (Archiver) » et
   « Appliquer aussi aux N conversations ». Traite l'historique *et* le courrier
   à venir, définitivement.

## Le tri est terminé

**La totalité de la boîte de réception est étiquetée.** La requête de contrôle

```
in:inbox has:nouserlabels
```

ne renvoie plus rien. Plus un seul fil de la boîte de réception n'est sans
libellé, du plus récent (septembre 2026) au plus ancien (février 2022).

Environ **3 100 fils** ont été traités à la main sur les deux sessions, en
plus des 88 de la session initiale.

## Compteurs finaux, par libellé

Chiffres relevés par `list_labels`, en nombre de **fils** (conversations).

| Libellé | Fils | Messages |
|---|---:|---:|
| Publicité | 1 461 | 1 470 |
| Abonnements | 1 401 | 1 581 |
| Pro | 1 050 | 1 353 |
| À vérifier | 410 | 456 |
| Fac | 358 | 416 |
| Banque | 289 | 298 |
| Famille | 271 | 400 |
| Assurance et Santé | 121 | 131 |
| Cours | 76 | 125 |

Libellés préexistants, inchangés :

| Libellé | Fils |
|---|---:|
| pole emploi | 21 |
| job | 20 |
| alternance chaudronnerie recherche | 20 |
| Perso | 16 |
| canada | 13 |
| CAF | 10 |
| administratif | 0 |

La boîte de réception compte 5 077 fils. La somme des colonnes ci-dessus est
supérieure : un même fil peut porter plusieurs libellés, c'est voulu.

## Comment le balayage a été mené

La boîte a été découpée en partitions natives Gmail, chacune traitée jusqu'à
épuisement, puis un ratissage final :

1. `in:inbox has:nouserlabels category:promotions` — épuisée
2. `in:inbox has:nouserlabels category:updates` — épuisée (2026-09 → 2022-06)
3. `in:inbox has:nouserlabels category:social` — épuisée (2026-09 → 2024-02),
   quasi exclusivement LinkedIn, Instagram, Facebook, Threads → Abonnements
4. `in:inbox has:nouserlabels category:forums` — vide
5. `in:inbox has:nouserlabels` — le reste, épuisé

Détail de la méthode dans `METHODE.md`.

## Deux règles de prudence appliquées partout

**En cas d'hésitation entre Publicité et Abonnements, le fil est allé dans
Abonnements.** Tanguy envisage de supprimer le lot Publicité : mieux vaut
garder un prospectus que perdre une facture.

**En cas de doute réel, le fil est allé dans À vérifier**, sans être tranché.

## Trois décisions qui attendent Tanguy

Rien ne sera fusionné, supprimé ni déplacé sans son accord explicite.

**1. Il manque une catégorie « engagement politique ».** Plus de 150 fils
(Rassemblement National et RN Jeunesse, Patriotes pour l'Europe, Les
Fédéralistes, Jérôme Sainte-Marie, délégué départemental jeunesse et démission
de cette fonction, plans d'action, événements). Cela n'entre dans aucune des
neuf catégories. Tout est garé dans À vérifier. Créer un libellé dédié, ou
verser dans Perso ?

**2. Il manque une catégorie pour le projet Canada / Québec.** Immigration
(IRCC, `cic.gc.ca`, `canada.ca`), MIFI, VFS Global, GCKey, Accès Études Québec,
Up North Immigration, Sûreté du Québec, CSSBJ. Un libellé `canada` existe déjà
mais ne porte que 13 fils. Faut-il y verser tout ce dossier, aujourd'hui dans
À vérifier ?

**3. Les libellés préexistants se recoupent avec les nouveaux.** `job`,
`pole emploi` et `alternance chaudronnerie recherche` couvrent le terrain de
**Pro**. `CAF` et `administratif` couvrent une partie de ce qui a été garé dans
**À vérifier**. Rien n'a été fusionné ni supprimé, conformément à la consigne.

## Le libellé À vérifier, 410 fils

À relire avec Tanguy. Il contient, par ordre de volume :

- **Engagement politique**, plus de 150 fils (voir décision 1)
- **Dossier Canada / Québec**, immigration et études (voir décision 2)
- **Administratif** : CAF, ANTS, permis de conduire (`interieur.gouv.fr`,
  stages de récupération de points ECF / Actiroute), Ciclade
- **Correspondants personnels non identifiés**, vus une ou deux fois, que le
  seul expéditeur ne permet pas de classer
- **Cas sensibles ou isolés**, notamment :
  - `1940cb6abf28bb84` — échange avec la gendarmerie, objet « Photo menace Lys »
  - `195edc9e94737fad` — CV à Olivier Alemany transféré au père
  - `187e7c6bc7d5b19a` — signalement à la plateforme Yubo
  - `19dbadd03bce6319` — envoi à un service de reprographie, contenu non identifié
- **Fils sans objet ni aperçu**, contenu uniquement en pièce jointe

Une imprécision connue : trois fils de `contact@exchange-college.com` sont dans
À vérifier alors que les suivants, une fois l'objet lu, sont partis dans **Fac**
(c'est une école de banque-finance-assurance). À corriger lors de la relecture.

## Consigne respectée

Rien n'a été supprimé, mis à la corbeille ou marqué comme spam, **à la seule
exception des messages que Tanguy a explicitement demandé de supprimer** lors
de la seconde session. Aucun libellé préexistant n'a été modifié ou supprimé.
Aucun message n'a été envoyé.
