# Cahier des charges V0 — Feux de forêt dans le Loiret

**Commanditaire** — Direction du SDIS du Loiret  
**Périmètre** — Loiret (45), avec comparaison à l’échelle régionale et, si les données sont comparables, nationale  
**Statut** — Ébauche collective du 22 novembre 2026  
**Jalons** — Contrôle du dépôt le 6 décembre 2026, présentation client le 11 décembre 2026

## 1. Besoin du SDIS

Le SDIS prépare la saison des feux de forêt de l’été 2027. Ses moyens ne permettent pas de renforcer le dispositif partout pendant toute la saison. Le projet doit éclairer trois décisions :

1. **Où concentrer les moyens ?** Identifier les communes ou zones à étudier en priorité à partir des feux observés, des surfaces parcourues et des caractéristiques territoriales disponibles.
2. **Quand concentrer l’effort ?** Repérer les périodes qui concentrent les départs de feu ou les surfaces parcourues.
3. **À partir de quel niveau de danger envisager un renforcement ?** Comparer les départs observés aux niveaux annoncés et mesurer, pour chaque seuil testé, les jours de mobilisation simulée et les jours avec feu qui resteraient sous le seuil.

La comparaison avec les autres départements doit montrer dans quelle mesure les constats du Loiret se retrouvent ailleurs, sur des périodes et des définitions comparables. Commande du SDIS du Loiret · [Questions collectives #11](https://github.com/abdelbasirmn/feux-de-foret-centre-val-de-loire/issues/11)

## 2. Données et règles de traitement

| Source | Usage prévu | Limite ou vérification attendue |
|---|---|---|
| **BDIFF** | Départs de feu, dates de première alerte, communes et surfaces parcourues. | La matrice recense une extraction Centre-Val de Loire 2025. La PR qualité décrit un historique plus large pour le Loiret. Réconcilier les versions et vérifier la couverture avant de fixer la période d’analyse. |
| **Météo des forêts** | Niveaux de danger annoncés par département et date de validité. | Vérifier la période commune avec BDIFF. Le choix de l’échéance reste ouvert. **J1** est proposé à l’équipe. |
| **ADMIN EXPRESS, BD Forêt V2, DFCI et OCS GE** | Référentiel communal, végétation et occupation du sol pour le diagnostic territorial. | Vérifier les géométries disponibles. Le carroyage DFCI décrit le territoire. La localisation précise d’un feu à l’intérieur de sa commune reste inconnue. L’extrait OCS GE recensé décrit des changements entre deux dates. |
| **Copernicus CEMS, climatologie, BD TOPO et BD ALTI** | Compléments sur la sécheresse, la météo locale, l’accessibilité et le relief. | Intégrer ces sources selon la faisabilité des rapprochements et leur apport à une question métier. La localisation des centres de secours renseigne leur implantation. Les moyens effectivement disponibles restent à documenter. |

Le pipeline doit agréger les feux par **département et jour de première alerte**, puis les rapprocher du **département et de la date de validité** de la prévision. L’analyse utilisera une échéance de prévision constante. Un jour couvert sans feu enregistré peut compter pour zéro. Les jours sans couverture vérifiée et les feux sans prévision associée doivent être signalés séparément. [Matrice des sources](https://github.com/abdelbasirmn/feux-de-foret-centre-val-de-loire/blob/main/docs/sources/matrice.md) · [Rapport qualité en revue, PR #28](https://github.com/abdelbasirmn/feux-de-foret-centre-val-de-loire/pull/28)

## 3. Solution et livrables attendus

Le cadrage retient **Databricks Free Edition, Python, PySpark, SQL et Delta Lake** pour le pipeline, **Power BI Desktop** pour la restitution et **GitHub** pour le versionnement. L’architecture prévoit trois couches : **Bronze** pour les données brutes et leur provenance, **Silver** pour les données nettoyées et contrôlées, **Gold** pour les tables destinées à l’analyse. Le cadrage mentionne un modèle en étoile. Le modèle cible propose plusieurs tables de faits partageant des dimensions communes pour respecter les différents niveaux de détail. Cette articulation est à confirmer en équipe. [Cadrage technique](https://github.com/abdelbasirmn/feux-de-foret-centre-val-de-loire/blob/main/docs/cadrage-technique.md) · [Modèle cible](https://github.com/abdelbasirmn/feux-de-foret-centre-val-de-loire/blob/main/docs/modelisation/modele-cible-v0.md) · [Data Lineage](https://github.com/abdelbasirmn/feux-de-foret-centre-val-de-loire/blob/main/docs/modelisation/data-lineage-v0.md)

| Livrable | Contenu minimal | Critère de validation |
|---|---|---|
| **Pipeline de consolidation** | Chargement multi-sources, nettoyage, transformations, contrôles qualité et sorties documentées. | Un membre peut relancer le traitement depuis un clone du dépôt en suivant les instructions. Les sources et leurs versions, les volumes avant et après nettoyage, les rejets et les résultats des contrôles sont traçables. |
| **Indicateurs et tableau de bord** | Les sept indicateurs V0 couvrent le nombre de feux, la surface totale et moyenne, le taux de jours avec feu par niveau, la part des départs en danger faible, les jours de renfort simulés et la part des départs couverts par seuil. La restitution prévoit des vues par période et par territoire. | Les mesures sont reliées aux questions métier et calculées sur les sorties vérifiées du pipeline. Les unités, périodes et dénominateurs sont lisibles. Les résultats de référence sont comparés à ceux de Power BI et l’actualisation est testée. |
| **Proposition au SDIS** | Une synthèse des zones et périodes à examiner, des scénarios de seuil et des limites qui affectent leur interprétation. | Chaque proposition renvoie à un indicateur ou à un visuel vérifiable et indique les hypothèses nécessaires. Les coûts, effectifs et contraintes non renseignés sont signalés avant toute recommandation de mobilisation. |

Consignes HETIC — UE01, Projet 1 - MD5 · [Fiche des indicateurs DataViz V0](https://github.com/abdelbasirmn/feux-de-foret-centre-val-de-loire/blob/main/docs/fiche-projet/Fiches_projet_SDIS_Loiret_V0.pdf)

## 4. Priorités et décisions ouvertes

- **P0 — Avant le contrôle du 6 décembre.** Versionner et documenter le premier traitement BDIFF du Loiret. Vérifier les dates, les doublons, les surfaces et les volumes. Préparer le rapprochement météo en contrôlant l’unicité des lignes au bon niveau de détail et en recensant les feux et jours non appariés.
- **P0 — Avant la présentation du 11 décembre.** Relier les visualisations aux données effectivement traitées et justifier les conclusions. Si la comparaison nationale reste insuffisamment documentée, présenter les résultats régionaux vérifiables et expliquer la limite.
- **À arbitrer en équipe.** Choisir J1 ou une autre échéance justifiée, confirmer les années communes, valider les objectifs K1/K2 et préciser les données opérationnelles à demander au SDIS. [Brouillon K1/K2](https://github.com/abdelbasirmn/feux-de-foret-centre-val-de-loire/blob/TEMPLATE_MEFIRE_NSANGOU_Abdelbasir/kpi/diagnostic-et-objectifs-collectifs-v0.md) · [Discussion sur J1](https://github.com/abdelbasirmn/feux-de-foret-centre-val-de-loire/issues/20#issuecomment-7080758197)

**Répartition proposée pour la relecture.** Abdelbasir coordonne la validation et la restitution. Ange vérifie la faisabilité du pipeline et du modèle. Thanael vérifie les contrôles qualité, les cas de données manquantes et les critères de recette.

**État vérifié du projet.** Le test d’ouverture et d’affichage de Power BI est consigné dans le #20. L’actualisation et les calculs sur les sorties réelles restent à vérifier. Aucun script ni notebook de pipeline n’apparaît dans `main` au moment de cette vérification. [Ticket #20](https://github.com/abdelbasirmn/feux-de-foret-centre-val-de-loire/issues/20) · [Arborescence auditée](https://github.com/abdelbasirmn/feux-de-foret-centre-val-de-loire/tree/f48db21fd2f81c7d46a8ff6e3c0d38f40a8c4e70)
