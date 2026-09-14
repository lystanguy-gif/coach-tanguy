# Filtres Gmail à créer — Publicité et Abonnements

## Pourquoi ce fichier

Le connecteur Gmail pose un libellé sur **un fil à la fois**. Il reste environ
4 000 fils de publicité et d'abonnements. Même à 25 appels par tour, cela
représente des heures de traitement.

Un **filtre Gmail natif** fait exactement la même chose en une seconde, sur la
totalité des fils correspondants, passés et à venir. C'est la bonne façon de
finir le travail. Les listes d'expéditeurs ci-dessous ont été établies par
recensement réel de la boîte, et vérifiées sur une centaine de fils déjà
étiquetés à la main.

## Mode d'emploi

Dans Gmail, sur ordinateur :

1. Paramètres → **Filtres et adresses bloquées** → *Créer un filtre*
2. Coller le contenu du bloc dans le champ **De**
3. *Créer un filtre* → cocher **Appliquer le libellé** et choisir le libellé
4. Cocher impérativement **« Appliquer aussi le filtre aux N conversations
   correspondantes »** — c'est cette case qui traite l'historique
5. *Créer un filtre*

Compter une à deux minutes par filtre.

## Règle de prudence appliquée

Tanguy envisage de **supprimer** le lot Publicité. Donc, en cas d'hésitation
entre Publicité et Abonnements, le fil va dans **Abonnements**. Mieux vaut
garder un prospectus que perdre une facture. Les filtres ci-dessous suivent
cette règle : Ulys, Canal+ service client, Fnac, Apple, Airbnb, Patreon et les
reçus d'achat sont classés en Abonnements même quand leur contenu est parfois
promotionnel.

---

## Filtre 1 — Publicité (`Label_5`)

Prospection commerciale et newsletters non sollicitées.

```
marionnaud.paris OR news.darty.com OR mms.com OR emailing.bonnegueule.fr OR insideapple.apple.com OR nedm.asus.com OR news.asus.com OR fr-mail.canalplus.com OR emailing.canalplus.fr OR news.lecomptoirdemathilde.com OR emailing.pagesjaunes.fr OR actu.mifassur.com OR news.qare.fr OR studyrama.com OR lifecycle.quizlet.com OR academia-mail.com OR email.feverup.com OR lasergame-evolution.com OR macarte.giropharm.fr OR music.deezer.com OR engage.microsoft.com OR engagement.microsoft.com OR slidesgpt.com OR etudes-online.fr OR mail-digiposte.laposte.info OR email.memphis-restaurant.com OR newsletters-brgm.fr OR fondationsaintpierre.org OR artexplora.org OR yoo.paris OR feedback.avis-verifies.com OR email.fastt.org OR facebookmail.com OR discover@airbnb.com OR bebee.com OR hubspotemail.net
```

Les plus gros volumes de la boîte sont ici : Marionnaud, Darty, M&M'S,
BonneGueule, Apple marketing, Academia.edu, ASUS.

## Filtre 2 — Abonnements (`Label_6`)

Services souscrits, notifications de compte, reçus, sécurité.

```
no_reply@email.apple.com OR appleid@id.apple.com OR noreply@email.apple.com OR noreply@apple.com OR accounts.google.com OR noreply-accounts@google.com OR no-reply@google.com OR google-noreply@google.com OR noreply-findhub@google.com OR google-maps-noreply@google.com OR update.tiktok.com OR service.tiktok.com OR linkedin.com OR mail.tinder.com OR gotinder.com OR mail.instagram.com OR mail.threads.net OR supabase.com OR netlify.com OR mail.anthropic.com OR email.claude.com OR higgsfield.ai OR plaud.ai OR email.openai.com OR samsung-mail.com OR patreon.com OR planity.com OR resamania.com OR noreply.myhair.informatique@fiducial.fr OR kalendes.com OR communications.paypal.com OR izly.fr OR fnac.com OR servicesclients.canalplus.fr OR auto.unibet.fr OR automated@airbnb.com OR express@airbnb.com OR hubspot.com OR clients.ulys.com OR vinci-autoroutes.com OR email.ledauphine.com OR letreco.fr OR typeform.com
```

## Filtre 3 — Banque (`Label_9`)

```
caisse-epargne.fr OR getalma.eu OR paybox.com OR sips-services.com OR mail.floa.fr
```

Couvre toutes les adresses Caisse d'Épargne rencontrées : `noreply@`,
`noreply@cepac.`, `nepasrepondre@notification.cepac.`,
`nepasrepondre@bcom.cepac.`, `conseiller@pac.`, `AG_CEPAC@mail-ida.`, ainsi que
les conseillers nommément (Cerdan, Jondreville).

## Filtre 4 — Assurance et Santé (`Label_10`)

```
doctolib.fr OR monespacesante.fr OR rdvasos.fr OR lifen.fr OR medispace.fr OR ch-briancon.fr OR ch-embrun.fr OR uroclub.fr OR mifassur.com OR ameli.fr
```

Attention : `contact@actu.mifassur.com` est de la prospection et se trouve déjà
dans le filtre Publicité. Gmail applique les deux filtres, le fil recevra les
deux libellés. C'est acceptable, mais si Tanguy veut supprimer la Publicité sans
risque, retirer `mifassur.com` de ce filtre-ci.

## Filtre 5 — Pro (`Label_8`)

```
francetravail.fr OR francetravail.net OR pole-emploi.fr OR noreply-pole-emploi.fr OR ras-interim.fr OR myras.fr OR proman-interim.com OR proman-emploi.fr OR proman-group.ch OR jobconcept.fr OR alpemploi.fr OR sovitrat.fr OR adecco.fr OR manpower.fr OR mypixid.eu OR coffreo.com OR cibtp.fr OR hydrogeotechnique.com OR envisol.fr OR beetween-software.com OR talent-soft.com OR profils.org OR esbanque.fr OR partnaire.fr OR eol-interim.com OR bpsinterim.net OR geosonicfrance.fr OR keller.com OR garelli.fr OR beconfluence.com OR razel-bec.fayat.com OR franki.fayat.com OR emails.hellowork.com OR jobleads.com OR fr.jooble.org OR smadesep.com OR gendrylocation.com OR rhonealpesfondations.fr
```

## Filtre 6 — Fac (`Label_11`)

```
univ-tln.fr OR unilim.fr OR parcoursup.fr OR lescrous.fr OR messervices.etudiant.gouv.fr OR ac-aix-marseille.fr OR ac-nancy-metz.fr OR unicem.fr OR univ-amu.fr OR education.gouv.fr OR atrium-sud.fr OR studapart.com OR index-education.net OR ac-cned.fr OR afev.org
```

## Filtre 7 — à arbitrer : engagement politique

Aucun libellé n'existe pour cette catégorie. Les fils concernés sont pour
l'instant dans **À vérifier**. Si Tanguy veut un libellé dédié, le créer puis
appliquer :

```
rassemblementnational.fr OR r-n.info OR patriotespourleurope.fr OR contactrn05 OR jsaintem@icloud.com
```

---

## Après les filtres

Il restera un reliquat hétérogène : expéditeurs vus une seule fois, messages
d'inconnus, fils sans objet. Pour le balayer :

```
in:inbox has:nouserlabels
```

C'est aussi la requête qui permet de mesurer ce qui reste à traiter à tout
moment.

## Avant toute suppression

Ne rien supprimer sans relecture. Ouvrir `label:Publicité`, trier par
expéditeur, vérifier qu'aucun fil utile ne s'y est glissé. Les faux positifs
probables à contrôler en priorité :

- **MIF** : à la fois prospection et contrat d'assurance-vie réel
- **Ulys / Vinci Autoroutes** : badge télépéage réellement souscrit
- **Le Dauphiné Libéré** : abonnement payant, pas de la publicité
- **Fondation Saint-Pierre** : Tanguy y est donateur
