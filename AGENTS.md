# Doctrine DIGIYLYFE — Quartier Général

## MASTER CORE — règle supérieure

Toute évolution DIGIYLYFE doit respecter l'arbre maître :

**CORE MONDIAL → PAYS → TERRITOIRE → ZONE → BESOIN → PROFESSIONNEL → OUVRIR**

Référence : [`MASTER-CORE.md`](./MASTER-CORE.md).

Règles non négociables du CORE :

- un seul moteur territorial commun ;
- le pays est la première porte opérationnelle ;
- un nouveau pays est d'abord une configuration et des données, jamais une copie complète du moteur ;
- la géographie, le besoin, le professionnel et la capacité métier restent des couches distinctes ;
- DRIVER, LOC, RESA, MARKET, BUILD, JOB, EXPLORE, CARNET et autres briques sont des capacités, pas la colonne vertébrale visible ;
- dans les territoires, l'action générique vers la présence du professionnel est **OUVRIR** ;
- ne jamais qualifier cette présence comme « fiche » ou « site » si le niveau commercial n'a pas à être révélé.

## Règles non négociables

- Toujours partir du fichier réel existant.
- Ne jamais réécrire à l'aveugle un module entier si le fichier source existe déjà.
- Zéro démo si le rail réel existe.
- Ne pas refaire le SQL si le backend réel est déjà posé, sauf bug réel prouvé.
- Priorité au front si le backend existe déjà.
- Toujours renvoyer le fichier entier quand une correction est demandée.
- Travailler fichier par fichier.
- Ne modifier que ce qui casse, ce qui bloque le terrain, ou ce qui contredit la doctrine.
- Sur mobile : moins de bla-bla, plus d'action.
- Les mots visibles au public doivent rester humains, jamais techniques.

## Loi des routes DIGIY

On peut épurer une page, mais on ne doit jamais couper ses routes utiles.

Toute page DIGIY recousue doit vérifier la présence ou la pertinence de ces portes :

- Site DIGIYLYFE : https://digiylyfe.com/
- Territoires DIGIYLYFE : https://digiylyfe.com/#territoires
- Tarifs : https://tarifs.digiylyfe.com/
- Retour utile vers le territoire, la vitrine ou la capacité métier concernée
- Action principale terrain visible sans chercher

Une page plus sobre doit mieux guider l'utilisateur, pas l'enfermer.

## Vocabulaire façade

- Ne pas afficher inutilement : module, dashboard, cockpit, slug, backend, configuration, système, rail, session, token.
- Préférer les mots métier et les gestes humains.
- Le bouton principal doit nommer une action concrète.
- Dans une carte territoriale générique, utiliser **OUVRIR** pour ne pas confondre carte, présence, fiche et site.

## Architecture DIGIYLYFE

- CORE : architecture mondiale commune.
- Première couche opérationnelle : pays.
- Données territoriales : pays → territoire → zone → besoin → professionnel.
- Backend : Supabase (tables réelles, RLS actif lorsque requis).
- Hébergement front : GitHub Pages.
- API : VPS Nginx + PM2 lorsque nécessaire.
- Modèle commercial public : 0% commission, relation directe avec le professionnel.
- Système de langues commun ; activation locale par pays.
- Socle linguistique : FR · EN · ES · PT · IT · DE · NL · AR ; RTL automatique pour l'arabe.

## Sécurité front

- Ne jamais exposer de `service_role key` côté client.
- Ne jamais afficher de secret dans le HTML, le JavaScript public, les logs ou la console.
- Les pages protégées doivent conserver leur protection d'accès.
- Une simplification visuelle ne doit jamais transformer une page protégée en page publique.
- Une clé publique `anon` Supabase n'est pas un secret, mais son usage doit rester limité aux politiques RLS prévues.

## Capacités métier

DRIVER · LOC · MARKET · JOB · BUILD · RESA · EXPLORE · CARNET · RESTO · autres briques validées.

Ces capacités peuvent évoluer indépendamment du MASTER CORE. Elles ne définissent jamais à elles seules un pays ou un territoire.

## Méthode de travail

1. Lire le fichier actuel.
2. Identifier le rail réel à conserver.
3. Vérifier sa place dans l'arbre MASTER CORE.
4. Repérer les vieux rails, démos, boucles d'accès ou incohérences vocabulaire.
5. Corriger seulement ce qui est utile.
6. Tester téléphone et ordinateur quand l'interaction est publique.
7. Signaler ce qui a été gardé, corrigé ou volontairement laissé intact.

## Sortie attendue

- Pas de fragments inutiles.
- Pas de pseudo-démo.
- Pas de changement backend non demandé.
- Pas de duplication d'un moteur par pays.
- Toujours signaler ce qui a été gardé, corrigé ou volontairement laissé intact.

---

**DIGIYLYFE — Le CORE est mondial. Le terrain reste local.**
