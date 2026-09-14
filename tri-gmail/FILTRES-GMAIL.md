# Filtres Gmail — pour que le tri se maintienne tout seul

## À quoi sert ce fichier maintenant

L'historique est fait : la boîte de réception est entièrement étiquetée à la
main, fil par fil (voir `ETAT.md`). Ce fichier ne sert donc plus à rattraper
l'arriéré, il sert à **ce que le courrier qui arrive demain soit rangé tout
seul**, sans nouvelle session de tri.

Les listes d'expéditeurs ci-dessous sont le recensement réel de la boîte,
établi sur les ~3 100 fils traités. C'est de loin la partie la plus précieuse de
ce dépôt.

## Mode d'emploi

Dans Gmail, sur ordinateur :

1. Paramètres → **Filtres et adresses bloquées** → *Créer un filtre*
2. Coller le contenu du bloc dans le champ **De**
3. *Créer un filtre* → cocher **Appliquer le libellé** et choisir le libellé
4. Cocher **« Appliquer aussi le filtre aux N conversations correspondantes »**
   si on veut aussi rattraper d'éventuels fils archivés hors boîte de réception
5. *Créer un filtre*

Gmail limite la longueur d'un critère. Si un bloc est refusé, le couper en deux
filtres qui posent le même libellé, cela revient au même.

## Règle de prudence appliquée

Tanguy envisage de **supprimer** le lot Publicité. Donc, en cas d'hésitation
entre Publicité et Abonnements, l'expéditeur est classé en **Abonnements**.
Mieux vaut garder un prospectus que perdre une facture. C'est pourquoi Ulys,
Canal+ service client, Fnac, Apple, Airbnb, Patreon, Le Dauphiné et tous les
reçus d'achat sont en Abonnements même quand leur contenu est parfois
promotionnel.

---

## Filtre 1 — Publicité (`Label_5`)

Prospection commerciale et newsletters non sollicitées.

```
news.darty.com OR satisfaction@client.darty.fr OR mms.com OR marionnaud.paris OR emailing.bonnegueule.fr OR mailing.bonnegueule.fr OR diduenjoy.com OR nedm.asus.com OR news.asus.com OR macarte.giropharm.fr OR news.qare.fr OR studyrama.com OR partenaire.studyrama.com OR emailing.pagesjaunes.fr OR news.lecomptoirdemathilde.com OR email.memphis-restaurant.com OR fr-mail.canalplus.com OR emailing.canalplus.fr OR appstore@insideapple.apple.com OR applegames@insideapple.apple.com OR applepay@insideapple.apple.com OR email.claude.com OR e.leclerc OR satisfaction@client.fnac.com OR izac.fr OR discover@airbnb.com OR airbnb@express.medallia.com OR email.feverup.com OR lasergame-evolution.com OR cartejeunes.fr OR feedback.avis-verifies.com OR microsoftstore.com OR csa-votre-avis-client.laposte.fr OR academia-mail.com OR lifecycle.quizlet.com OR actu.mifassur.com
```

## Filtre 2 — Abonnements (`Label_6`)

Services souscrits, notifications de compte, reçus, sécurité, réseaux sociaux.
C'est le filtre le plus gros : le couper en deux si Gmail le refuse.

```
no_reply@email.apple.com OR noreply@email.apple.com OR noreply@apple.com OR appleid@id.apple.com OR News@insideapple.apple.com OR iCloud@insideapple.apple.com OR appleaccount@insideapple.apple.com OR accounts.google.com OR no-reply@google.com OR noreply-accounts@google.com OR google-maps-noreply@google.com OR gemini@google.com OR forms-receipts-noreply@google.com OR microsoft.com OR microsoftonline.com OR accountprotection.microsoft.com OR engage.microsoft.com OR github.com OR linkedin.com OR e.linkedin.com OR facebookmail.com OR mail.instagram.com OR mail.threads.net OR update.tiktok.com OR service.tiktok.com OR twitch.tv OR mail.tinder.com OR gotinder.com OR music.deezer.com OR spotify.com OR patreon.com OR nexusmods.com OR calendly.com OR asana.com OR supabase.com OR netlify.com OR mail.anthropic.com OR email.openai.com OR kimi.ai OR riseup.ai OR use.ai OR higgsfield.ai OR plaud.ai OR slidesgpt.com OR luminpdf.com OR web3forms.com OR typeform.com OR samsung-mail.com OR nintendo.com OR booking.com OR campanile.com OR kyriad.com OR planity.com OR resamania.com OR azeoo.com OR comptoirdelaforme.fr OR letreco.fr OR judge.me OR trustpilot.com OR shop.app OR wetransfer.com OR tomtom.com OR weezevent.com OR chronofresh.fr OR laposte.fr OR mail-digiposte.laposte.info OR clients.ulys.com OR vinci-autoroutes.com OR sncf-connect.com OR monidentifiant.sncf OR email.ledauphine.com OR servicesclients.canalplus.fr OR fnac.com OR izly.fr OR auto.unibet.fr OR automated@airbnb.com OR express@airbnb.com OR artexplora.org OR e-passjeunes.fr OR monnett.social OR etudes-online.fr OR yoo.paris OR joom.com OR hubspot.com
```

## Filtre 3 — Pro (`Label_8`)

France Travail, intérim, jobboards, employeurs, ATS de recrutement.
À couper en deux ou trois filtres.

```
francetravail.fr OR francetravail.net OR pole-emploi.fr OR noreply-pole-emploi.fr OR ipsos_pour_francetravail@medallia.com OR enquete-ipsos-poleemploi.fr OR jobleads.com OR emails.hellowork.com OR bebee.com OR indeed.com OR fr.jooble.org OR jobijoba.com OR talent.com OR lesjeudis.com OR ourjob.net OR jobfalcon.com OR best-jobs-online.com OR trabajo.org OR meteojob.com OR mytalentplug.com OR taleez.com OR softy.pro OR werecruit.io OR smartrecruiters.com OR humansourcing.fr OR digitalrecruiters.com OR beetween-software.com OR recruitmail.com OR jobs2web.com OR myworkday.com OR successfactors.com OR talent-soft.com OR profils.org OR proman-interim.com OR proman-emploi.fr OR proman-group.ch OR mypixid.eu OR ras-interim.fr OR myras.fr OR partnaire.fr OR adecco.fr OR manpower.fr OR randstad.fr OR samsic-emploi.fr OR startpeople.fr OR welljob.fr OR crit-job.com OR sovitrat.fr OR bpsinterim.net OR genesisrh.com OR jobconcept.fr OR alpemploi.fr OR coffreo.com OR interimairessante.fr OR interimairesinfo.fr OR fastt.org OR cibtp.fr OR orano.group OR arcelormittal.com OR invivo-group.com OR fayat.com OR razel-bec.fayat.com OR franki.fayat.com OR geolithe.com OR imerys.com OR nge.fr OR colasway.com OR spie.com OR spiebatignolles.fr OR keller.com OR envisol.fr OR hydrogeotechnique.com OR stabilisationprotection.fr OR solusol.fr OR geotec.fr OR geosonicfrance.fr OR sade-cgth.fr OR irsn.fr OR erg-sa.fr OR rocmine.fr OR garelli.fr OR beconfluence.com OR tsm-str.com OR bpmed.fr OR esbanque.fr OR bnpparibas.com OR ggvie.fr OR secomoc.fr OR naval-group.com OR tereos.com OR layan.eu OR lemonsoft.fr OR centraltest.com OR aksis.fr OR sengager.fr OR noreply.myhair.informatique@fiducial.fr OR alterneo.fr OR service-civique.gouv.fr
```

## Filtre 4 — Banque (`Label_9`)

```
caisse-epargne.fr OR cepac.caisse-epargne.fr OR notification.cepac.caisse-epargne.fr OR bcom.cepac.caisse-epargne.fr OR payzen.eu OR getalma.eu OR stripe.com OR mail.floa.fr OR paypal.fr OR communications.paypal.com OR link.com OR paybox.com OR sips-services.com OR payfip.gouv.fr OR e-transactions.fr OR moneris.com OR stancer.com OR payments@google.com OR sodexopass.fr
```

Le filtre Caisse d'Épargne couvre toutes les adresses rencontrées : `noreply@`,
`nepasrepondre@notification.cepac.`, `nepasrepondre@bcom.cepac.`,
`conseiller@pac.`, `AG_CEPAC@mail-ida.`, ainsi que les conseillers nommément
(Cerdan, Jondreville).

## Filtre 5 — Assurance et Santé (`Label_10`)

```
ameli.fr OR ces.ameli.fr OR doctolib.fr OR qare.fr OR probtp.com OR btpst.fr OR mifassur.com OR mma.fr OR coteclients.mma.fr OR inovie.fr OR labosinovie.fr OR lifen.fr OR medadom.com OR medispace.fr OR kalilab.fr OR eurofins.com OR apicil.com OR mesanalyses.fr OR rdvasos.fr OR monespacesante.fr OR ch-briancon.fr OR ch-embrun.fr OR uroclub.fr
```

Attention : `contact@actu.mifassur.com` est de la prospection et figure aussi
dans le filtre Publicité. Gmail applique les deux, le fil recevra les deux
libellés. Acceptable, mais si Tanguy veut supprimer la Publicité sans risque,
retirer `mifassur.com` du filtre Publicité plutôt que de celui-ci.

## Filtre 6 — Fac (`Label_11`)

```
univ-tln.fr OR unilim.fr OR crous-limoges@legavote.fr OR lescrous.fr OR messervices.etudiant.gouv.fr OR izly.fr OR parcoursup.fr OR cyclades.education.gouv.fr OR examens-concours.gouv.fr OR education.gouv.fr OR index-education.net OR ac-aix-marseille.fr OR ac-nancy-metz.fr OR ac-cned.fr OR atrium-sud.fr OR unicem.fr OR univ-amu.fr OR afev.org OR campus-espl.fr OR digital-college.fr OR digiforma.com OR ief2i.fr OR exchange-college.com OR studapart.com OR newsletters-brgm.fr
```

## Filtre 7 — à arbitrer : engagement politique

Aucun libellé n'existe pour cette catégorie, qui représente pourtant plus de
150 fils. Ils sont dans **À vérifier**. Si Tanguy veut un libellé dédié, le
créer puis appliquer :

```
rassemblementnational.fr OR r-n.info OR rnformations.fr OR patriotespourleurope.fr OR lesfederalistes.eu OR contactrn05 OR jsaintem@icloud.com
```

## Filtre 8 — à arbitrer : Canada / Québec

Un libellé `canada` existe déjà. Si Tanguy veut y verser tout le dossier
immigration et études, aujourd'hui dans **À vérifier** :

```
crmaeqatq.ca OR cic.gc.ca OR canada.ca OR mifi.gouv.qc.ca OR vfsglobal.com OR vfshelpline.com OR clegc-gckey.gc.ca OR cssbj.gouv.qc.ca OR upnorthimmigration.com OR surete.qc.ca
```

---

## Le reliquat

Aucune liste d'expéditeurs ne couvrira les correspondants vus une seule fois.
Pour balayer ce qui échappe aux filtres, la requête reste :

```
in:inbox has:nouserlabels
```

Elle renvoie `{}` aujourd'hui. Elle est aussi la mesure de ce qui reste à
traiter, à tout moment.

## Avant toute suppression

Ne rien supprimer sans relecture. Ouvrir `label:Publicité`, trier par
expéditeur, vérifier qu'aucun fil utile ne s'y est glissé. Les faux positifs
probables à contrôler en priorité :

- **MIF** : à la fois prospection et contrat d'assurance-vie réel
- **Ulys / Vinci Autoroutes** : badge télépéage réellement souscrit
- **Le Dauphiné Libéré** : abonnement payant, pas de la publicité
- **Fondation Saint-Pierre** : Tanguy y est donateur
- **Fnac, Darty, Apple** : les reçus d'achat sont mêlés aux offres
