# DIGIYLYFE MASTER CORE 🌍🦅

**Statut : SOCLE VALIDÉ — V1**

Le MASTER CORE est la colonne vertébrale mondiale de DIGIYLYFE.

Il ne représente ni un pays, ni un module, ni une société. Il définit la mécanique commune que chaque pays configure selon sa réalité locale.

## Arbre maître

**CORE MONDIAL → PAYS → TERRITOIRE → ZONE → BESOIN → PROFESSIONNEL → OUVRIR**

Cette hiérarchie est le socle de toute extension territoriale DIGIYLYFE.

## 1. Loi du CORE unique

- Un seul moteur territorial commun.
- Un nouveau pays ne doit jamais nécessiter la copie complète du moteur.
- Les différences entre pays viennent d'abord de la configuration et des données.
- Le CORE porte les règles communes : navigation, langues, accessibilité, recherche, affichage des résultats, contact direct et sécurité front.
- Le CORE doit rester suffisamment neutre pour accueillir de nouveaux pays sans réécriture structurelle.

**Test de conformité :** si ouvrir un nouveau pays oblige à recopier le moteur, l'architecture n'est pas conforme au MASTER CORE.

## 2. Le PAYS est la première porte opérationnelle

Le monde constitue le socle technique. Le pays constitue la première couche réelle d'usage.

Chaque pays apporte sa configuration locale :

- code pays ;
- nom public ;
- monnaie ;
- langue principale ;
- langues visiteurs ;
- langues locales progressives ;
- formats téléphone / contact ;
- territoires disponibles ;
- éventuelles particularités commerciales, administratives ou réglementaires.

Le contenu d'un pays ne doit pas se noyer dans le contenu mondial.

## 3. TERRITOIRE puis ZONE

Un pays contient un ou plusieurs territoires.

Exemples initiaux :

- Sénégal → Petite Côte, Dakar, Thiès, Saint-Louis…
- France → Vallée de la Dordogne, Bordeaux, Arcachon…

Un territoire contient des zones utiles au terrain : ville, commune, quartier, aéroport ou autre découpage pertinent.

La géographie et le métier restent séparés.

**PAYS ≠ TERRITOIRE ≠ ZONE ≠ BESOIN ≠ PROFESSIONNEL ≠ CAPACITÉ.**

## 4. BESOINS universels

Le visiteur ne doit pas avoir à comprendre l'organisation technique de DIGIYLYFE.

Le moteur présente des besoins humains simples. La base V1 est :

- Se déplacer
- Trouver un artisan
- Dormir ou louer
- Manger ou réserver
- Acheter local
- Beauté & Bien-être
- Emploi et missions
- Annonces
- La Voix / orientation

Ces familles peuvent évoluer, mais elles restent indépendantes des modules techniques.

## 5. PROFESSIONNEL puis OUVRIR

Le territoire référence le professionnel et son activité publique. Il ne révèle pas son niveau commercial DIGIYLYFE.

Le bouton principal universel est :

**OUVRIR**

Il peut ouvrir selon le cas :

- une carte ;
- une présence ;
- une fiche ;
- un site ;
- une boutique ;
- une page restaurant ;
- une capacité métier spécialisée.

Le territoire ne doit jamais créer de confusion entre ces niveaux de prestation.

Les actions fonctionnelles restent nommées explicitement quand elles existent : **WhatsApp**, **Appeler**, etc.

## 6. Les modules sont des CAPACITÉS

DRIVER, LOC, RESA, MARKET, BUILD, JOB, EXPLORE, CARNET et les autres briques ne constituent pas l'arbre principal.

Ils deviennent des capacités activables derrière un professionnel ou une activité.

Le visiteur voit son besoin et le professionnel. La plomberie interne reste invisible.

## 7. Langues et localisation

Le système de langues appartient au CORE, les langues réellement activées appartiennent à la configuration du pays.

Socle multilingue déjà retenu :

**FR · EN · ES · PT · IT · DE · NL · AR**

Règles :

- RTL automatique pour l'arabe ;
- arabe standard pour l'interface écrite commune ;
- langues locales africaines ajoutées progressivement selon la qualité disponible ;
- ne jamais publier une traduction locale approximative uniquement pour afficher un drapeau ;
- la voix pourra ultérieurement utiliser des variantes locales lorsque la qualité le permet.

Exemple Sénégal : français + langues visiteurs, puis wolof progressivement, puis autres langues locales si la qualité est suffisante.

## 8. Données vivantes

Le CORE ne doit pas embarquer une copie figée de chaque professionnel.

La donnée vivante doit être structurée au minimum par :

**country_id → territory_id → zone_id → need/category → professional_id**

Supabase reste la source de données opérationnelle lorsqu'elle est disponible.

Un secours local peut exister pour la continuité d'affichage, mais il ne devient jamais la source maître.

## 9. Architecture commerciale séparée

Le niveau acheté par un professionnel est une couche commerciale distincte de l'annuaire territorial.

**Professionnel → niveau de présence / prestation → capacités activées**

Cette couche ne doit pas modifier l'arbre public :

**PAYS → TERRITOIRE → ZONE → BESOIN → PROFESSIONNEL → OUVRIR**

Ainsi les tarifs, offres et niveaux de travail peuvent évoluer sans reconstruire le moteur territorial.

## 10. Architecture juridique séparée

La structure technique ne décide pas automatiquement de la structure juridique.

À terme, une structure opérationnelle par pays peut être pertinente lorsque le volume, le droit local, la fiscalité ou l'exploitation le justifient.

Cela ne crée jamais un nouveau CORE et n'impose pas une société par module.

## 11. Ordre de construction

1. CORE mondial commun.
2. MASTER PAYS.
3. MASTER TERRITOIRE.
4. Configuration des zones et besoins.
5. Connexion des professionnels.
6. Activation éventuelle des capacités métier.
7. Validation terrain sur téléphone et ordinateur.

## 12. Pays pilotes

### 🇸🇳 Sénégal

- monnaie : FCFA ;
- première base : Petite Côte ;
- extensions naturelles : Dakar, Thiès, Saint-Louis… ;
- français + socle visiteurs ;
- wolof et autres langues locales progressivement.

### 🇫🇷 France

- monnaie : EUR ;
- première base : Vallée de la Dordogne ;
- extensions naturelles : Bordeaux, Arcachon… ;
- français + langues visiteurs.

## Règle finale

**Le monde partage le moteur. Le pays garde sa réalité. Le territoire organise le terrain. Le professionnel garde sa relation directe.**

---

**DIGIYLYFE — Le CORE est mondial. Le terrain reste local.**
