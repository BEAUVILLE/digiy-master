# DIGIYLYFE — CONTRAT COMMUN DE RECHERCHE V1
**Statut :** Proposition d'architecture en revue — aucun déploiement.  
**Date :** 8 novembre 2026.  
**Autorité :** `MASTER-CORE.md`, `MASTER-PAYS.md`, `MASTER-TERRITOIRE.md`, `MAITRE-TERRITOIRE-UNIVERSEL-V1.md`, `AGENTS.md`. En cas d'écart, les doctrines validées prévalent.

## 1. Problème réel observé (lecture du code, pas bug de production démontré)
Trois parcours publics chargent/filtrent les professionnels différemment :
- `digiylyfe.com/annuaire.html` : vues `digiy_annuaire_public`, `digiy_annuaire_volontaires`, `digiy_zones`, `digiy_metiers`, `digiy_annuaire_public_zones` ; filtrage par identifiants, parfois par texte de ville ; tri A→Z.
- `digiylyfe.com/territoire.html` via `assets/digiy-territoire-runtime-v1.js` : données annuaire Supabase, rattachement besoins/territoires, base + couverture, données locales de secours ; tri pondéré.
- `digiylyfe.com/recherche.html` via `assets/i18n/recherche-v5-app.js` : RPC `digiy_rechercher_pros`, `digiy_build_public_profiles`, données BUILD statiques ; déduplication de préférence par téléphone, sinon URL/slug/nom.

Ces différences peuvent rendre les résultats divergents. Le comportement réel, les données Supabase et la sécurité RLS n'ont pas encore été audités exhaustivement.

## 2. Décision de direction
**Centraliser le contrat de lecture, d'identité et de correspondance ; ne pas fusionner les interfaces, bases privées ni modules métier.**
Un seul CORE mondial. Pays, territoires et capacités restent distincts. Supabase demeure source de vérité pour les données vivantes ; les éventuels secours ne remplacent pas la production.

## 3. Contrat conceptuel de présence publique normalisée
Ce schéma est **logique** : aucune nouvelle table SQL ni migration n'est prescrite.

| Champ logique | Fonction | Règle |
|---|---|---|
| `professional_id` | Identité canonique du professionnel | Stable ; jamais remplacer par téléphone seul |
| `source_id`, `source_type` | Traçabilité des anciens rails | Garder la provenance ; correspondance explicite si les IDs diffèrent |
| `country_id`, `territory_id` | Ancrage géographique | Séparation pays/territoire |
| `base_zone_id` | Zone principale | Ne change pas selon la zone recherchée |
| `service_zone_ids`, `service_territory_ids` | Couverture déclarée et validée | Ne pas déduire à partir du texte libre |
| `need_id`, `metier_id` | Besoin public et métier déclaré | Référentiels canoniques ; alias historiques comme adaptateurs |
| `public_url` | Porte publique vérifiée | Pointer vers carte, fiche, site ou présence selon l'existant |
| `public_phone`, `public_whatsapp` | Contact autorisé | N'afficher que les informations publiques confirmées |
| `visibility`, `is_active` | Éligibilité publique | Respecter publication, retrait et suspension |
| `capabilities` | Capacités métier disponibles | Facultatif, non utilisé pour réécrire l'arbre territorial |

Ce contrat décrit les champs attendus et leur sémantique ; il ne prouve pas que tous existent aujourd'hui dans toutes les tables.

## 4. Règles communes envisagées
1. **Éligibilité publique** : afficher uniquement une présence réelle, publique et active, autorisée à être montrée.
2. **Géographie** : correspondance si zone cible = base, ou zone explicitement desservie, ou zone contenue dans un territoire de service validé. Les villes libres ne prouvent pas la couverture.
3. **Identité / déduplication** : priorité à `professional_id` validé ; rapprochement des rails historiques uniquement sur correspondance établie. Deux métiers partageant un WhatsApp peuvent rester deux activités distinctes. Aucun fusionnement automatique incertain.
4. **Besoin / métier** : normaliser les libellés via un dictionnaire ou adaptateur commun, sans relancer `MARKET` legacy ni masquer des métiers.
5. **Contact** : numéro lisible et appels/WhatsApp directs quand autorisés ; lien public canonique ; pas de fiche imaginaire, disponibilité inventée ni niveau commercial exposé.
6. **Classement** : séparer **éligibilité commune** et **ordre d'affichage propre à chaque porte** (A→Z dans l'annuaire ; pondération documentée dans le territoire). Un moteur commun n'impose pas une seule expérience.
7. **Confidentialité** : aucune remontée de jeton de gestion, `owner_id` privé, secret Supabase, données administratives ou calendriers privés ; contrôle serveur/RLS toujours obligatoire.
8. **Résilience** : ne pas créer une API obligatoire supplémentaire ; privilégier un adaptateur partagé testable côté lecteur, avec comportement de secours déjà approuvé et explicitement identifié.

## 5. Démarche d'implémentation NON autorisée par ce document seul
A. Comparer les vues Supabase et la RPC avec leurs règles RLS en lecture seule, avec accès autorisé ; éviter toute copie de données privées.  
B. Relever les écarts de schéma, identifiants, références géographiques et URL publiques sur des enregistrements tests.  
C. Écrire des tests locaux reproductibles avec données simulées : **aucun déploiement**.  
D. Construire un adaptateur commun dans une branche isolée de `digiylyfe.com` en conservant les trois interfaces.  
E. Mesurer les divergences et vérifier mobile, langues, QR, contacts, URLs et sécurité.  
F. Présenter diff et résultats au fondateur. Merge, mise en production et dépenses uniquement après autorisation distincte.

## 6. Cas de tests minimaux
- Deux professionnels distincts utilisant le même numéro public : **2 résultats**, jamais fusionnés automatiquement.
- Un professionnel basé à Saly et servant Mbour : visible sur Mbour si couverture validée, affiché **basé à Saly**.
- Une fiche dont la ville libre mentionne Mbour mais sans zone de service validée : **pas de fausse extension** de couverture.
- Deux sources avec même `professional_id` canonique : **une seule présence**, contacts/URL sélectionnés selon les données publiques canoniques.
- Professionnel retiré/inactif : **absent**.
- Compte privé/token de gestion : **jamais affiché ni loggé**.
- `MARKET` historique : alias éventuel vers COMMERCE uniquement pour compatibilité, jamais nouvelle activation du module.
- Multilingue et RTL arabe : affichage inchangé ; aucune traduction locale non validée.
- Source indisponible : erreur claire / secours conforme aux règles, jamais données simulées présentées comme réelles.

## 7. Critères d'acceptation avant intégration
- Pas de divergence injustifiée d'identité, de couverture, d'activité et de contact entre les trois portes.
- Aucune perte de route, carte, QR ou action terrain.
- Aucune fuite de données privées, RLS examinée et tests reproductibles.
- Aucun changement comportemental de production avant validation humaine.
- Coût supplémentaire : **zéro** au stade documentaire et test local.

## 8. Sources de lecture
- `BEAUVILLE/digiy-master` : `MASTER-CORE.md`, `MASTER-PAYS.md`, `MASTER-TERRITOIRE.md`, `MAITRE-TERRITOIRE-UNIVERSEL-V1.md`, `AGENTS.md`.
- `BEAUVILLE/digiylyfe.com` : `annuaire.html`, `territoire.html`, `recherche.html`, `annuaire-inscription-auto.js`, `assets/digiy-territoire-runtime-v1.js`, `assets/i18n/recherche-v5-app.js`.

**Décision de contrôle : documentation proposée sur branche dédiée ; aucune mutation des tables, de la production ou du MASTER validé sans revue et fusion explicites.**
