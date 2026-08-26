# DIGIYLYFE — MASTER TERRITOIRE 🧭

**Statut : DOCTRINE VALIDÉE — V1**

Le MASTER TERRITOIRE définit la couche locale située sous le MASTER PAYS.

Références supérieures :
- [`MASTER-CORE.md`](./MASTER-CORE.md)
- [`MASTER-PAYS.md`](./MASTER-PAYS.md)

Références universelles validées :
- [`MAITRE-TERRITOIRE-UNIVERSEL-V1.md`](./MAITRE-TERRITOIRE-UNIVERSEL-V1.md)
- `BEAUVILLE/digiy-master-modeles/MASTER-TERRITOIRE-UNIVERSEL-V1/`
- `BEAUVILLE/digiy-master-modeles/MASTER-TERRITOIRE-UNIVERSEL-V1/config/world-ribbon-contract.json`

## Arbre maître

**CORE MONDIAL → PAYS → TERRITOIRE → ZONE → BESOIN → PROFESSIONNEL → OUVRIR**

Le pays organise. Le territoire rapproche.

## 1. Rôle du TERRITOIRE

Un territoire regroupe des zones locales cohérentes pour l'usage terrain.

Il ne crée pas un nouveau moteur. Il configure le moteur commun avec :
- un `country_id` ;
- un `territory_id` stable ;
- un nom public ;
- un slug ;
- une liste de zones ;
- un statut d'activation ;
- des règles locales éventuelles strictement isolées.

## 2. Loi de non-duplication

**Un nouveau territoire = données + configuration.**

Il est interdit de copier le moteur territorial complet pour ouvrir une nouvelle zone géographique.

Toute règle universelle remonte dans le CORE. Toute règle pays reste dans le MASTER PAYS. Toute exception réellement locale reste dans le territoire.

## 3. ZONES

Une zone est une unité de terrain utile au visiteur et au professionnel : ville, commune, quartier, aéroport, station, bassin de vie ou autre découpage cohérent.

Chaque zone possède au minimum :
- un `zone_id` canonique stable ;
- un `territory_id` ;
- un nom public ;
- un slug ;
- un statut.

Le `zone_id` doit être mondialement non ambigu. Format recommandé :

`PAYS-TERRITOIRE-ZONE`

Exemple : `SN-PETITE-COTE-SALY`.

Le slug reste la clé humaine. Une production existante peut conserver ses UUID ou identifiants historiques : un adaptateur peut relier `source_zone_id` ou `source_zone_slug` au `zone_id` canonique. Le MASTER ne force jamais une migration brutale des données vivantes.

Les zones ne doivent pas mélanger plusieurs pays ni plusieurs territoires sans raison explicite.

### 3.1 Zone de base et zones d'intervention

La **zone de base** indique où le professionnel est principalement rattaché. Elle porte son ancrage territorial public.

Les **zones d'intervention** indiquent où ce professionnel accepte de se déplacer, livrer, intervenir ou servir.

Ces deux notions ne doivent jamais être confondues :

- un professionnel possède une seule `base_zone_id` principale ;
- il peut posséder zéro, une ou plusieurs `service_zone_ids` ;
- il peut aussi déclarer un ou plusieurs `service_territory_ids` lorsqu'il couvre un territoire entier ;
- une zone d'intervention ne change jamais automatiquement la zone de base ;
- servir Mbour, AIBD ou Thiès ne transforme pas un professionnel basé à Saly en professionnel basé à Mbour, AIBD ou Thiès ;
- une couverture hors du territoire principal doit être explicitement déclarée et validée, jamais déduite comme changement d'identité.

La lecture canonique devient :

`base_zone_id = ancrage`  
`service_zone_ids / service_territory_ids = couverture`

Pour compatibilité avec les données existantes, un champ historique `zone_id` peut être adapté en `base_zone_id` sans modifier immédiatement la production.

### 3.2 Couverture effective

La zone de base est toujours considérée comme desservie, même si aucune ligne de zone d'intervention n'existe en production.

La couverture effective est donc :

`base_zone_id + service_zone_ids + zones actives couvertes par les service_territory_ids validés`

Règles :

- les `service_zone_ids` ajoutent de la couverture ; ils ne remplacent jamais la zone de base ;
- un marqueur de territoire entier représente un `service_territory_id`, pas une zone ;
- un `service_territory_id` validé peut rendre le professionnel éligible dans les zones actives de ce territoire ;
- une destination extérieure encore planifiée, inconnue ou non structurée reste une référence de couverture en attente ;
- une référence extérieure non validée ne doit pas étendre automatiquement les résultats publics ;
- aucune extension de couverture ne réattribue l'identité territoriale du professionnel.

### 3.3 Éligibilité dans une zone cible

Pour une zone cible donnée, un professionnel peut apparaître si au moins une condition est vraie :

`target_zone_id == base_zone_id`

ou

`target_zone_id ∈ service_zone_ids`

ou

`target_zone_id appartient à un service_territory_id validé`.

Dans tous les cas :

- le résultat conserve la `base_zone_id` réelle du professionnel ;
- le résultat conserve son territoire d'ancrage réel ;
- une présence venue d'un autre territoire n'est jamais « relogée » dans la zone cible ;
- une couverture inter-territoire doit être explicite et validée ;
- un même professionnel ne doit apparaître qu'une fois dans la liste finale : déduplication par `professional_id`.

## 4. BESOINS

Les besoins viennent du MASTER CORE. Ils ne sont pas recréés territoire par territoire.

Le territoire peut seulement décider quels besoins sont visibles selon les données réellement disponibles.

## 5. CONTRAT PROFESSIONNEL

Les professionnels réels appartiennent à la donnée de production, pas au coffre MASTER.

Chaque présence publique doit pouvoir être reliée au minimum à :

`country_id → territory_id → base_zone_id → need_id → professional_id → public_url`

Le contrat peut aussi porter, selon le besoin : `activity_label`, `category`, téléphone, WhatsApp, capacités, poids de classement, `service_zone_ids`, `service_territory_ids` ou des références extérieures en attente de validation.

La production reste la source de vérité. Le MASTER décrit la forme de raccordement et les identifiants canoniques attendus.

Le territoire ne révèle jamais le niveau commercial acheté par le professionnel.

L'action générique reste **OUVRIR**.

## 6. Capacités

DRIVER, LOC, RESA, MARKET, BUILD, JOB, EXPLORE, CARNET et les futures briques sont des capacités héritées du CORE.

Elles ne remplacent jamais la lecture :

**Territoire → Zone → Besoin → Professionnel.**

## 7. Activation terrain

Un territoire peut être :
- `planned` — préparé mais non publié comme actif ;
- `pilot` — ouvert avec données limitées et suivi terrain ;
- `active` — exploité normalement.

Une zone peut suivre la même logique.

Aucun territoire ou zone planifié ne doit être présenté comme actif sans validation terrain.

## 8. Première implémentation

Le premier territoire de référence est :

**🇸🇳 SÉNÉGAL → PETITE CÔTE**

Configuration technique : `BEAUVILLE/digiy-master-modeles/MASTER-TERRITOIRE-PETITE-COTE-V1/`.

Saly est la première zone pilote de raccordement architectural. Mbour sert de deuxième pilote pour vérifier la couverture inter-zones et la conservation de l'ancrage réel des professionnels.

## 9. Extraction universelle validée — 26 août 2026

Après validation croisée de plusieurs terrains, la mécanique territoire commune est désormais formalisée dans :

`BEAUVILLE/digiy-master-modeles/MASTER-TERRITOIRE-UNIVERSEL-V1/`

Son autorité doctrinale est :

`BEAUVILLE/digiy-master/MAITRE-TERRITOIRE-UNIVERSEL-V1.md`

Le MASTER universel n’efface pas les MASTER territoires existants. Il devient le **point de départ obligatoire pour tout nouveau territoire**.

Règles universalisées notamment :

- vrais professionnels prioritaires ;
- exemples clairement marqués et secondaires ;
- règle « LE VIDE NE S’AFFICHE PAS. IL SE PROJETTE. » ;
- ANNONCES / BESOINS DU MOMENT comme porte chaude lorsqu’elle est active ;
- LA VOIX comme recherche transversale, jamais comme métier ;
- identité visuelle locale configurable sans dupliquer le moteur ;
- prix hérités du MASTER PAYS ;
- validation humaine avant publication et avant propagation d’une nouvelle règle ;
- PWA de `digiylyfe.com` protégé comme invariant de non-régression ;
- Ruban du Monde préparé comme navigation `MONDE → PAYS → RÉGION / TERRITOIRE → VILLE / ZONE`, alimentée par la configuration et non par des listes codées en dur ;
- seuls les niveaux géographiques validés pour le public peuvent apparaître ; `planned` reste invisible ;
- activation publique du Ruban du Monde différée jusqu’à validation humaine explicite.

Loi mondiale :

**LE MONDE NE S’AFFICHE PAS PAR PROMESSE. IL S’AFFICHE À MESURE QU’IL S’OUVRE.**

---

**DIGIYLYFE — Le CORE relie. Le pays organise. Le territoire rapproche. Le monde s’affiche à mesure qu’il s’ouvre.**