---
name: review-pr-digiy
description: Relire une pull request, un diff ou un ensemble de changements selon la doctrine DIGIY. Utiliser avant merge, pendant revue GitHub, ou quand on veut attraper régressions, vieux rails, incohérences de façade ou boucles d’accès.
---

Utilise cette skill pour relire des changements de code DIGIY avant validation.

## Objectif
Détecter les écarts qui cassent le terrain, le rail réel ou la doctrine produit.

## Checklist de revue
- Le front visible reste humain.
- Les noms techniques ne fuient pas en façade.
- Le slug continue bien d’être transmis là où nécessaire.
- Les anciens rails ou vieux RPC n’ont pas été réintroduits.
- La navigation interne reste cohérente.
- Le backend réel n’a pas été modifié sans raison claire.
- Le fichier renvoyé reste aligné avec le dépôt existant.
- Le mobile n’a pas été dégradé.
- Aucun faux contenu de démonstration n’a été injecté.

## Sortie
Classer les retours en 3 niveaux :
- bloquant,
- à corriger vite,
- amélioration facultative.

Toujours citer précisément le fichier et l’impact terrain.
