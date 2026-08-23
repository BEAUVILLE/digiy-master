# DIGIYLYFE — MASTER TERRITOIRE 🧭

**Statut : DOCTRINE VALIDÉE — V1**

Le MASTER TERRITOIRE définit la couche locale située sous le MASTER PAYS.

Références supérieures :
- [`MASTER-CORE.md`](./MASTER-CORE.md)
- [`MASTER-PAYS.md`](./MASTER-PAYS.md)

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

## 4. BESOINS

Les besoins viennent du MASTER CORE. Ils ne sont pas recréés territoire par territoire.

Le territoire peut seulement décider quels besoins sont visibles selon les données réellement disponibles.

## 5. CONTRAT PROFESSIONNEL

Les professionnels réels appartiennent à la donnée de production, pas au coffre MASTER.

Chaque présence publique doit pouvoir être reliée au minimum à :

`country_id → territory_id → zone_id → need_id → professional_id → public_url`

Le contrat peut aussi porter, selon le besoin : `activity_label`, `category`, téléphone, WhatsApp, capacités, poids de classement ou zones desservies.

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

Saly est la première zone pilote de raccordement architectural. Ce choix sert à tester le contrat avec des données réelles de production sans créer un MASTER SALY séparé.

---

**DIGIYLYFE — Le CORE relie. Le pays organise. Le territoire rapproche.**
