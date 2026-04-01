# SKILL — Doctrine Façade DIGIY

## Principe fondamental
> "On ne change pas ce que l'utilisateur ne voit pas."
Backend, tables, RPCs, clés storage → intacts.
Seul le visible change.

## Dictionnaire de traduction

| Technique | Humain |
|-----------|--------|
| slug | identifiant |
| rail | terrain |
| module | espace |
| session | connexion |
| PIN | code secret |

## Périmètre

✅ À traiter :
- Titres, labels, boutons, placeholders, messages d'erreur
- Balises `alt`, `aria-label`

❌ Ne pas toucher :
- Variables JS, fonctions, tables Supabase
- RPCs et leurs paramètres
- Clés localStorage / sessionStorage
- Noms de fichiers

## Processus
1. Scanner le fichier ligne par ligne
2. Identifier tout texte user-facing technique
3. Appliquer le dictionnaire
4. Livrer le fichier recousu complet

## Format de sortie
1. Liste des termes remplacés (avant → après + numéro de ligne)
2. Fichier complet recousu
