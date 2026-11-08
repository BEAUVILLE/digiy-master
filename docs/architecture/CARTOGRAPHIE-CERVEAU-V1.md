# DIGIYLYFE — CARTOGRAPHIE DU CERVEAU V1
**Date :** 8 novembre 2026  
**Statut :** Diagnostic initial soumis à revue en PR — non fusionné au MASTER.

## Périmètre effectivement inspecté
- `BEAUVILLE/digiy-master` : `README.md`, `AGENTS.md`, `MASTER-CORE.md`, `MASTER-PAYS.md`, `MASTER-TERRITOIRE.md`.
- `BEAUVILLE/digiylyfe.com` : `README.md`, `index.html` (début), `annuaire.html` (début), `annuaire-inscription-auto.js`, `manifest.json`, `sw.js`, `docs/DOCTRINE-CARTE.md`.
- Les recherches globales GitHub n'ont pas retourné de résultats indexés. L'inventaire des fichiers et des fonctionnalités n'est donc **pas complet**.

## Carte des responsabilités
| Couche | Source de référence | Rôle et état vérifié |
|---|---|---|
| CORE mondial | MASTER-CORE.md | Un seul moteur, navigation besoins → professionnels → OUVRIR. Doctrine lue. |
| Pays | MASTER-PAYS.md | Monnaies, langues, indicatifs, territoires configurés sans copie du moteur. Doctrine lue. |
| Territoire | MASTER-TERRITOIRE.md | Base et zones desservies distinctes ; déduplication par professionnel. Doctrine lue. |
| Capacités | AGENTS.md, MASTER-CORE.md | DRIVER, LOC, RESA, COMMERCE, BUILD, JOB, EXPLORE : capacités sous le professionnel. Contrat propriétaire défini ; runtime non vérifié. |
| Vitrine | index.html | Page d'accueil et porte d'entrée ; seules les premières lignes ont été examinées. |
| Annuaire | annuaire.html | Formulaire et résultats par activité/territoire ; inspection partielle. |
| Inscription | annuaire-inscription-auto.js | RPC `digiy_annuaire_inscrire`, `digiy_annuaire_gerer`, lien public, token privé dans fragment URL. Code inspecté ; RPC serveur non audité. |
| PWA | manifest.json, sw.js | Application installable, page hors connexion mise en cache, navigation privée non mise en cache. Pas de test navigateur. |
| Carte DIGIY | docs/DOCTRINE-CARTE.md | Carte payante sans adhésion obligatoire dans cette doctrine courte. |

## Règles fondamentales confirmées dans les documents
1. Arbre : CORE MONDIAL → PAYS → TERRITOIRE → ZONE → BESOIN → PROFESSIONNEL → OUVRIR.
2. Pays et territoires ajoutés par configuration + données, sans duplication du moteur.
3. Les capacités métier ne remplacent pas l'arbre public.
4. Contact direct prioritaire ; aucune commission sur la transaction directe.
5. Propriétaire authentifié, espace privé, seules les données publiques autorisées sont exposées.
6. Ne pas créer de faux professionnels, disponibilités, vérifications ou garanties.
7. `MARKET` historique hors service ; `COMMERCE / MON COMMERCE` est désigné actif dans AGENTS.md et MASTER-CORE.md.

## Écarts et questions à résoudre, sans conclure prématurément
- **Carte vs adhésion :** MASTER-CORE évoque un « socle adhérent » ; la doctrine du site précise que la carte n'impose pas l'adhésion. Les décisions commerciales plus récentes et implémentations doivent départager les formulations.
- **Antériorité documentaire :** MASTER-PAYS et MASTER-TERRITOIRE mentionnent encore `MARKET` dans leurs listes ; le MASTER-CORE et AGENTS.md le déclarent legacy. Écart rédactionnel probable, pas preuve d'un module relancé.
- **Inscription privée :** JS interdit de stocker le token privé localement, mais l'URL de gestion contient un token dans le fragment. Une revue sécurité du flux et des politiques Supabase demeure nécessaire, sans exposer de données ou secrets.
- **Fonctions RPC :** le JS les appelle mais leur sécurité côté serveur et RLS ne sont pas encore vérifiées.
- **PWA :** manifeste et service worker trouvés ; la qualité de l'installation et le bug WebKit ne sont pas tranchés par cette lecture.
- **V1 vitrine :** FREEZE validé par le fondateur ; absence de contrôle de parité complète entre branche, production et toutes les pages.

## Hypothèse d'intelligence interdisciplinaire — étude seulement
Réutiliser le contrat `zone cible + besoin + professionnel + couverture effective` afin de proposer des métiers complémentaires autour d'un besoin complexe, sans nouveau CORE ni création automatique de collaborations.

Exemple : « rénover une maison à Saly » → métiers potentiellement associés, avec indication explicite de leur zone de base et couverture validée ; utilisateur et professionnels gardent l'initiative.

Avant prototype : vérifier données des professions, couverture, qualité des fiches et mécanisme de recherche existants.

## Prochain ordre d'audit (non exécuté)
1. Lire `MAITRE-TERRITOIRE-UNIVERSEL-V1.md`, modèles Sénégal et routes réelles.
2. Vérifier JS/SQL existants liés à l'annuaire, recherche et RLS.
3. Tracer un parcours complet inscription → visibilité → carte → contact → gestion propriétaire, avec données fictives en environnement de test.
4. Tester mobile/PWA et contrôler production indépendamment du code.
5. Comparer décisions commerciales récentes aux doctrines datées.
6. Ne proposer un algorithme de rapprochement qu'après ce contrôle.

## Sources lues
- https://github.com/BEAUVILLE/digiy-master/blob/main/README.md
- https://github.com/BEAUVILLE/digiy-master/blob/main/AGENTS.md
- https://github.com/BEAUVILLE/digiy-master/blob/main/MASTER-CORE.md
- https://github.com/BEAUVILLE/digiy-master/blob/main/MASTER-PAYS.md
- https://github.com/BEAUVILLE/digiy-master/blob/main/MASTER-TERRITOIRE.md
- https://github.com/BEAUVILLE/digiylyfe.com/blob/main/README.md
- https://github.com/BEAUVILLE/digiylyfe.com/blob/main/index.html
- https://github.com/BEAUVILLE/digiylyfe.com/blob/main/annuaire.html
- https://github.com/BEAUVILLE/digiylyfe.com/blob/main/annuaire-inscription-auto.js
- https://github.com/BEAUVILLE/digiylyfe.com/blob/main/manifest.json
- https://github.com/BEAUVILLE/digiylyfe.com/blob/main/sw.js
- https://github.com/BEAUVILLE/digiylyfe.com/blob/main/docs/DOCTRINE-CARTE.md

**Ce document est un état de connaissance partiel, non un audit de sécurité complet. Aucun changement de production ni fusion autorisé par sa seule création.**
