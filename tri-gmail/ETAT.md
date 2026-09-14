# État du tri au 14 septembre 2026, fin de session Claude Code

## Compteurs de libellés, avant et après

| Libellé | Avant | Après | Gain |
|---|---:|---:|---:|
| Famille | 87 | 267 | +180 |
| Cours | 2 | 75 | +73 |
| Fac | 0 | 149 | +149 |
| Pro | 0 | 219 | +219 |
| Publicité | 0 | 99 | +99 |
| Abonnements | 1 | 9 | +8 |
| Assurance et Santé | 0 | 13 | +13 |
| Banque | 0 | 2 | +2 |
| À vérifier | 1 | 34 | +33 |
| Perso | 8 | 16 | +8 |
| canada | 11 | 13 | +2 |
| CAF | 9 | 10 | +1 |

Un même fil peut porter plusieurs libellés, les gains ne s'additionnent donc pas
en un nombre de fils distincts. L'ordre de grandeur est d'environ 600 fils
distincts traités dans cette session, en plus des 88 de la session précédente.

## Ce qui est terminé

**Famille.** Requête élargie aux six adresses des parents, épuisée jusqu'au
dernier fil. `has:nouserlabels` ne renvoie plus rien sur cette requête.

**SENT.** Les 391 fils envoyés ont tous été passés en revue et étiquetés. C'est
ce balayage qui a fait apparaître les cours envoyés à soi-même, les camarades
non listés, et la totalité de l'historique de recherche d'emploi.

**Cours.** Les 28 camarades de la passation, plus les 26 découverts, plus les
notes de cours auto-envoyées.

**Fac.** Université de Toulon, Université de Limoges, Parcoursup, CROUS, CVEC,
UNICEM, lycées, CNED, AFEV.

**Pro.** Intérim, forage, France Travail, candidatures, employeurs, formation
Canada. Environ 220 fils.

## Ce qui reste

**Publicité et Abonnements**, soit l'essentiel du volume restant, autour de
4 000 fils. Le recensement des annonceurs est fait et vérifié, il est dans
`FILTRES-GMAIL.md`. Ce reliquat se traite en quelques minutes avec sept filtres
Gmail natifs, pas en heures d'étiquetage fil par fil. C'est d'ailleurs ce que
recommandait déjà la passation.

Mesurer ce qui reste à tout moment :

```
in:inbox has:nouserlabels
```

## Deux décisions qui attendent Tanguy

**1. Une catégorie manque.** Une dizaine de fils relèvent d'un engagement
politique (Rassemblement National Jeunesse, fonction de délégué départemental
jeunesse et démission de cette fonction, plan d'action, événements). Cela
n'entre dans aucune des neuf catégories. Ils sont dans À vérifier. Créer un
libellé dédié, ou les verser dans Perso ?

**2. Les libellés préexistants se recoupent avec Pro.** `job` (20 fils),
`pole emploi` (21) et `alternance chaudronnerie recherche` (20) couvrent le même
terrain que Pro. Rien n'a été fusionné ni supprimé, conformément à la consigne.
À arbitrer.

## Le libellé À vérifier, 34 fils

Trois familles de cas :

- **Engagement politique**, une dizaine de fils, voir ci-dessus
- **Fils sans objet ni aperçu**, contenu uniquement en pièce jointe, impossible
  à classer sans ouvrir la pièce jointe
- **Cas sensibles ou isolés** : le CV à Olivier Alemany transféré au père
  (`195edc9e94737fad`), un échange avec la gendarmerie intitulé « Photo menace
  Lys » (`1940cb6abf28bb84`), un signalement à la plateforme Yubo
  (`187e7c6bc7d5b19a`), un envoi à un service de reprographie
  (`19dbadd03bce6319`)

## Consigne respectée

Rien n'a été supprimé, ni mis à la corbeille, ni marqué comme spam. Aucun
libellé préexistant n'a été modifié ou supprimé. Aucun message n'a été envoyé.
