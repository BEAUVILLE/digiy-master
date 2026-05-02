# Doctrine DIGIYLYFE — Quartier Général

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

## Vocabulaire façade
- Ne pas afficher : module, PRO, dashboard, cockpit, slug, backend, configuration, système, rail, session, token.
- Préférer les mots métier et les gestes humains.
- Le bouton principal doit nommer une action concrète.

## Architecture DIGIYLYFE
- Backend : Supabase (tables réelles, RLS actif)
- Auth : RPC `digiy_verify_pin` — params `{p_phone, p_module, p_pin}` — table `go_pins`
- Pattern auth canonique : `window.DIGIY_LOGIN_URL` → `visibility:hidden` → `guard.js` → Supabase CDN → app scripts
- Session : clé `digiy_guard_session:MODULE` — expiry 8h — sessionStorage + localStorage
- Hébergement front : GitHub Pages
- API : VPS Nginx + PM2
- Modèle commercial : 0% commission, abonnement fixe

## Modules actifs (ne pas désactiver)
CAISSE PRO · DRIVER PRO · LOC PRO · MARKET · JOBS · BUILD · PAY

## Modules en veille stratégique (ne pas toucher)
FRET PRO · RESTO PRO · EXPLORE · FRET CHAUFFEUR · FRET CLIENT · NOTABLE

## Méthode de travail
1. Lire le fichier actuel.
2. Identifier le rail réel à conserver.
3. Repérer les vieux rails, démos, boucles d'accès ou incohérences vocabulaire.
4. Corriger seulement ce qui est utile.
5. Renvoyer un résultat propre, complet, directement exploitable.

## Sortie attendue
- Pas de fragments inutiles.
- Pas de pseudo-démo.
- Pas de changement backend non demandé.
- Toujours signaler ce qui a été gardé, corrigé, ou volontairement laissé intact.
- ## Loi des routes DIGIY

On peut épurer une page, mais on ne doit jamais couper ses routes.

Toute page DIGIY recousue doit vérifier la présence ou la pertinence de ces portes :

- Site DIGIYLYFE : https://digiylyfe.com/
- HUB DIGIY : https://digiy-hub.digiylyfe.com/
- Tarifs : https://tarifs.digiylyfe.com/
- Retour utile vers le module, la vitrine ou l’espace métier concerné
- Action principale terrain visible sans chercher

Une page plus sobre doit mieux guider l’utilisateur, pas l’enfermer.
