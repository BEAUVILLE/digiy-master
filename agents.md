# AGENTS.md

## Doctrine DIGIYLYFE — Quartier Général

### Règles non négociables
- Toujours partir du fichier réel existant.
- Ne jamais réécrire à l’aveugle un module entier si le fichier source existe déjà.
- Zéro démo si le rail réel existe.
- Slug-first pour l’accès et la navigation interne.
- Ne pas refaire le SQL si le backend réel est déjà posé, sauf bug réel prouvé.
- Priorité au front si le backend existe déjà.
- Toujours renvoyer le fichier entier quand une correction est demandée.
- Travailler fichier par fichier.
- Ne modifier que ce qui casse, ce qui bloque le terrain, ou ce qui contredit vraiment la doctrine produit.
- Sur mobile : moins de bla-bla, plus d’action.
- Les mots visibles au public doivent rester humains, jamais techniques.

### Vocabulaire façade
- Ne pas afficher : module, PRO, dashboard, cockpit, slug, backend, configuration, système.
- Préférer les mots métier et les gestes humains.
- Le bouton principal doit nommer une action concrète.

### Méthode de travail
1. Lire le fichier actuel.
2. Identifier le rail réel à conserver.
3. Repérer les vieux rails, démos, boucles d’accès ou incohérences de vocabulaire.
4. Corriger seulement ce qui est utile.
5. Renvoyer un résultat propre, complet, directement exploitable.

### Sortie attendue
- Pas de fragments inutiles.
- Pas de pseudo-démo.
- Pas de changement backend non demandé.
- Toujours signaler clairement ce qui a été gardé, corrigé, ou volontairement laissé intact.
