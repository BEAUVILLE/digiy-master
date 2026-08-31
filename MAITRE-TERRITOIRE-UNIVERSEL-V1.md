# 🦅 DIGIYLYFE — MAÎTRE TERRITOIRE UNIVERSEL V1

**Statut : VALIDÉ — AUTORITÉ TERRITORIALE UNIVERSELLE**

Ce MAÎTRE fixe les invariants de toute future implantation territoriale DIGIYLYFE.

Il s’appuie sur les validations croisées de Dakar, Bordeaux, Sarlat / Vallée de la Dordogne et Saly / Petite Côte.

Le moule opérationnel correspondant est :

`BEAUVILLE/digiy-master-modeles/MASTER-TERRITOIRE-UNIVERSEL-V1/`

## 1. Invariants sacrés

Ces règles ne varient pas d’un territoire à l’autre :

**MODULE = PORTE**  
**SUPABASE = AIGUILLEUR / SOURCE DE VÉRITÉ**  
**PROFESSIONNEL = SA PROPRE VITRINE**  
**EXEMPLE = PROJECTION TEMPORAIRE**  
**LA VOIX = RECHERCHE TRANSVERSALE**

Et :

**LE VIDE NE S’AFFICHE PAS. IL SE PROJETTE.**

## 2. Le réel passe devant

Toute donnée réelle de production éligible est prioritaire sur les exemples.

Un exemple ne peut jamais :

- être compté comme professionnel réel ;
- recevoir une fausse identité ;
- recevoir un faux téléphone ;
- recevoir de faux avis ;
- simuler une disponibilité réelle ;
- être présenté comme adhérent.

Le vrai professionnel conserve toujours son ancrage réel, sa propre vitrine et son `public_url`.

## 3. Le territoire configure, il ne recrée pas le moteur

Un territoire peut varier :

- pays ;
- nom ;
- type urbain / saisonnier / autre validé ;
- zones ;
- exemples ;
- textes ;
- ordre local des portes ;
- identité visuelle ;
- route locale ;
- paramètres commerciaux hérités du pays.

Il ne doit pas recréer :

- les besoins du CORE ;
- la vérité Supabase ;
- le contrat professionnel ;
- la logique de couverture ;
- le système de statut actif / suspendu ;
- les principes de contact direct ;
- le moteur PWA commun.

## 4. ANNONCES = porte chaude

La découverte terrain de Saly / Petite Côte est désormais universalisée :

**une annonce perd de sa valeur si le visiteur doit parcourir toute la page pour découvrir qu’elle existe.**

Lorsque `announcements` est activé, la surface territoriale doit lui donner un accès chaud près du haut : premier bouton, CTA HERO, bloc chaud, ou combinaison adaptée.

Cependant un filtre explicite comme `need=artisan` reste prioritaire : on ne remplace jamais la demande du visiteur par ANNONCES.

## 5. LA VOIX

LA VOIX n’est jamais une profession et n’a jamais de fiche adhérent dédiée.

Parcours canonique :

`VOIX → INTENTION → TERRITOIRE / ZONE / BESOIN → PROFESSIONNELS RÉELS → OUVRIR`.

## 6. Empreinte visuelle locale

L’identité locale est configurable, le moteur ne l’est pas.

Formule :

**MÊME MOTEUR · MÊME ADN DIGIYLYFE · EMPREINTE LOCALE DISTINCTE.**

Une ville future ne copie pas automatiquement les couleurs, zones ou exemples d’une ville précédente.

Les territoires déjà validés démontrent le principe, pas des palettes obligatoires.

## 7. PWA — clause de non-régression

`digiylyfe.com` reste une PWA tant qu’aucune décision humaine explicite n’en décide autrement.

Toute évolution de l’index principal doit préserver :

- manifest ;
- icônes ;
- métadonnées mobile / Apple ;
- enregistrement du service worker ;
- cohérence de cache/version ;
- installabilité lorsque supportée.

**Une refonte visuelle ou territoriale n’a pas le droit de casser silencieusement le PWA.**

Toute suppression volontaire d’un élément PWA exige validation humaine explicite.

## 8. RUBAN DU MONDE — autorité de navigation mondiale

Le Ruban du Monde est la couche future de navigation géographique globale de DIGIYLYFE.

Hiérarchie canonique :

**MONDE → PAYS → RÉGION / TERRITOIRE → VILLE / ZONE → BESOIN → PROFESSIONNEL**

Il ne doit jamais être alimenté par une liste géographique écrite à la main dans l’index. Sa source doit rester la configuration validée du CORE, des MASTER PAYS et des MASTER TERRITOIRE.

### Règle de vérité géographique

- `active` = peut apparaître ;
- `pilot` = peut apparaître seulement après validation publique ;
- `planned` = invisible ;
- `inactive` / `suspended` = invisible ;
- toute nouvelle apparition publique exige validation humaine.

### Règle d’interface

Sur mobile, le modèle privilégié est une bande horizontale tactile et déroulante. Sur écran large, elle peut devenir un ruban ou un sélecteur compact sans changer la hiérarchie.

Un lien profond explicite (`zone`, `local`, `need`) garde la priorité. Le Ruban du Monde ne doit jamais écraser une intention déjà exprimée par le visiteur.

### Loi du Ruban du Monde

**LE MONDE NE S’AFFICHE PAS PAR PROMESSE. IL S’AFFICHE À MESURE QU’IL S’OUVRE.**

Le Ruban du Monde est **validé structurellement mais non activé publiquement à ce stade**. Son activation sur l’index principal exige une décision humaine explicite et doit préserver intégralement le PWA.

Le contrat technique correspondant est :

`BEAUVILLE/digiy-master-modeles/MASTER-TERRITOIRE-UNIVERSEL-V1/config/world-ribbon-contract.json`

## 9. Parcours sans cul-de-sac

Prospect professionnel :

`TERRITOIRE → EXEMPLE → DÉMO → ADHÉSION → VALIDATION HUMAINE → VRAIE PRÉSENCE`

Client final :

`TERRITOIRE → BESOIN → ZONE → PRO RÉEL → VITRINE → CONTACT DIRECT`

LA VOIX :

`REQUÊTE → INTENTION → RÉSULTATS RÉELS → OUVRIR`

## 10. Prix

Le territoire n’invente pas son prix.

Le prix public autorisé vient du MASTER PAYS / runtime commercial pays.

Un territoire peut afficher le prix autorisé, mais ne crée jamais une grille parallèle.

## 11. Validation humaine

Une règle locale ne devient universelle qu’après preuve suffisante et validation humaine.

Une nouvelle ville ne doit jamais être propagée automatiquement depuis une ville précédente.

Ordre recommandé :

`OBSERVATION TERRAIN → CORRECTION LOCALE → VALIDATION VISUELLE → EXTRACTION DE LA RÈGLE UNIVERSELLE → MASTER / MAÎTRE`.

Pour le Ruban du Monde :

`TERRITOIRE VALIDÉ → STATUT PUBLIC VALIDÉ → ÉLIGIBLE AU RUBAN → ACTIVATION HUMAINE`.

## 12. Règle de fabrication d’un nouveau territoire

**ON HÉRITE DU MOTEUR. ON RECONSTRUIT LE TERRITOIRE.**

Le MASTER universel fournit le moule. Le pays fournit les règles nationales. Le territoire fournit son identité, ses zones et ses projections. Supabase fournit le réel.

## 13. Formule finale MAÎTRE

**LE MODULE OUVRE. SUPABASE AIGUILLE. LE PRO POSSÈDE SA VITRINE. L’EXEMPLE PROJETTE. L’ANNONCE REMONTE. LA VOIX CHERCHE. LE PWA RESTE. LE MONDE S’AFFICHE À MESURE QU’IL S’OUVRE.**

## 14. CARTE DE VISITE DIGIY — SOCLE ADHÉRENT

La carte de visite DIGIY est la **surface minimale de l'adhérent** dans l'écosystème. Elle ne doit pas être confondue avec une fiche adhérent enrichie ni avec un site individuel.

Un professionnel réel peut être visible dans le territoire sans être adhérent. Un adhérent validé peut choisir de disposer uniquement de sa carte de visite DIGIY dans le site / territoire DIGIYLYFE.

Invariant universel minimal :

**QR STABLE → CARTE ADHÉRENT / PWA → CONTACT DIRECT → RELATION CLIENT**

La carte doit pouvoir offrir, lorsque les coordonnées existent et sont autorisées :

- **Appeler** via le téléphone normal ;
- **WhatsApp** en accès direct ;
- **Copier le numéro** dans le presse-papiers ;
- numéro public lisible et réutilisable manuellement.

Le QR déjà posé chez l'adhérent ne doit pas changer lorsque sa présence s'enrichit.

Lorsque la technologie du navigateur le permet, la carte adhérent peut être installée ou ajoutée à l'écran d'accueil comme PWA, toujours par action volontaire du client. Le scan du QR ne doit jamais être présenté comme une installation automatique.

## 15. FICHE ET SITE — LIBERTÉ DE L'ADHÉRENT

La **fiche adhérent enrichie est facultative**. Le **site individuel est facultatif**.

L'adhésion n'oblige jamais l'adhérent à acheter une fiche, un catalogue, une boutique, un moteur métier ou un site.

L'adhérent peut rester durablement avec sa seule carte de visite DIGIY si cela correspond à son besoin.

DIGIYLYFE reste compétent pour lui proposer plus tard, à sa demande ou lorsque le besoin devient évident :

- une fiche enrichie ;
- des produits ou services ;
- un catalogue ;
- une réservation ;
- une boutique ;
- un site individuel ;
- d'autres capacités utiles.

Ces enrichissements sont des prestations ultérieures et volontaires. Ils ne conditionnent ni l'adhésion ni la présence minimale de l'adhérent.

**LOI UNIVERSELLE : LA CARTE EST LE SOCLE. LA FICHE ET LE SITE SONT UN CHOIX. L'ADHÉRENT RESTE LIBRE.**

## 16. SIGNATURE DE MARQUE UNIVERSELLE

La signature de marque canonique est :

**DIGIYLYFE.COM · L’empreinte numérique du professionnel**

Elle constitue la signature transversale de la maison DIGIYLYFE et peut accompagner les cartes de visite adhérents, fiches, sites, territoires et autres surfaces publiques lorsqu’elle est pertinente.

Elle ne remplace jamais le nom, l’identité ni la marque propre du professionnel. Elle signe l’infrastructure DIGIYLYFE derrière une présence dont le professionnel reste au premier plan.

---

**DIGIYLYFE — Le moteur reste commun. Le territoire devient reconnaissable. Le professionnel reste propriétaire de sa présence. Le monde n’apparaît que lorsqu’il devient réel.**
