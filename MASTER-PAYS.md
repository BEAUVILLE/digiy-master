# DIGIYLYFE — MASTER PAYS 🌍

**Statut : DOCTRINE VALIDÉE — V1**

Le MASTER PAYS définit la couche opérationnelle située immédiatement sous le MASTER CORE.

Référence supérieure : [`MASTER-CORE.md`](./MASTER-CORE.md)

## Arbre maître

**CORE MONDIAL → PAYS → TERRITOIRE → ZONE → BESOIN → PROFESSIONNEL → OUVRIR**

Le CORE est mondial. Le **PAYS** est la première porte réelle d'usage.

## 1. Rôle du PAYS

Un pays ne crée pas un nouveau moteur DIGIYLYFE.

Il configure le CORE avec sa réalité locale :

- identité pays ;
- monnaie ;
- langue principale ;
- langues visiteurs ;
- langues locales progressives ;
- préfixe téléphonique ;
- fuseau(x) horaire(s) ;
- territoires disponibles ;
- règles locales utiles au terrain ;
- moyens de contact ou particularités commerciales quand ils s'appliquent.

## 2. Loi de non-duplication

**Un nouveau pays = configuration + données.**

Il est interdit de recopier le moteur territorial complet pour ouvrir un nouveau pays.

Le pays peut ajouter des adaptations locales, mais elles doivent rester des paramètres, des données ou des extensions clairement isolées.

Si une évolution est réellement universelle, elle remonte dans le MASTER CORE au lieu d'être dupliquée pays par pays.

## 3. Séparation obligatoire des couches

Les couches suivantes restent distinctes :

**PAYS ≠ TERRITOIRE ≠ ZONE ≠ BESOIN ≠ PROFESSIONNEL ≠ CAPACITÉ ≠ NIVEAU COMMERCIAL**

Le niveau commercial acheté par un professionnel ne doit pas modifier l'arbre territorial public.

Dans le territoire, l'action générique reste **OUVRIR**.

## 4. Langues

Chaque pays déclare :

- une langue principale ;
- les langues internationales disponibles dans l'interface ;
- les langues locales ajoutées progressivement.

Une langue locale ne doit jamais être publiée comme complète si sa traduction n'est pas suffisamment validée.

Les variantes orales et dialectales peuvent être traitées séparément de la langue écrite standard.

## 5. Données pays

Toute donnée territoriale doit pouvoir être rattachée au minimum à un `country_id`.

Puis, selon le niveau utile :

`country_id → territory_id → zone_id → need_id → professional_id`

Cette structure empêche les contenus d'un pays de se noyer dans le contenu mondial et évite les collisions de noms de villes ou de territoires.

## 6. Modules et capacités

DRIVER, LOC, RESA, MARKET, BUILD, JOB, EXPLORE, CARNET et les futures briques DIGIYLYFE sont des **capacités activables**.

Elles ne remplacent jamais la hiérarchie pays / territoire / zone / besoin.

Le visiteur cherche d'abord une réalité humaine et locale. La capacité technique reste derrière le professionnel.

## 7. Test de conformité MASTER PAYS

Avant d'activer un nouveau pays, vérifier :

1. le pays possède un identifiant stable ;
2. sa monnaie et son préfixe téléphonique sont déclarés ;
3. ses langues sont classées par statut ;
4. ses territoires sont séparés des autres pays ;
5. aucun moteur complet n'a été copié ;
6. les besoins universels viennent du CORE ;
7. les capacités viennent du CORE ;
8. la présence du professionnel reste accessible par **OUVRIR** ;
9. les données locales peuvent évoluer sans modifier l'architecture mondiale.

## 8. Première implémentation

La première configuration de référence est :

**🇸🇳 MASTER PAYS SÉNÉGAL**

Elle est conservée dans le coffre technique `BEAUVILLE/digiy-master-modeles` sous `MASTER-PAYS-SENEGAL-V1/`.

---

**DIGIYLYFE — Un CORE mondial. Des pays lisibles. Des territoires humains.**
