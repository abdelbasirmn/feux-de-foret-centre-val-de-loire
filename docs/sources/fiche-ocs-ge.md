# Fiche d’identité de la source — OCS GE (Loiret, différentiel 2020–2023)

| Rubrique | Valeur |
|---|---|
| Propriétaire et système | IGN — Institut national de l’information géographique et forestière. OCS GE décrit la couverture et l’usage du sol. |
| Mode d’accès (export, API, téléchargement) et format | Téléchargement départemental sur cartes.gouv.fr. Fichier de données consulté pour cette correction : `DIFF_D045_2023_2020.gpkg`, au format GeoPackage, en RGF93 / Lambert-93 (EPSG:2154). |
| Grain (une ligne = ?) | Une ligne représente une zone du différentiel, sous forme de multipolygone, avec des attributs pour 2020 et 2023. |
| Emprise géographique | Loiret (45). Le fichier porte sur les zones du différentiel, pas sur la couche complète d’occupation du sol de 2023. |
| Période réellement couverte par les données | Comparaison des millésimes **2020 et 2023**. Date exacte d’observation de chaque zone **non vérifiée** : aucune date par zone dans le fichier ou ses métadonnées internes. |
| Date de dernière mise à jour affichée sur la fiche | **22 octobre 2026**, sur la [fiche du catalogue OCS GE](https://www.data.gouv.fr/datasets/ocs-ge). Cette date concerne le catalogue, pas les millésimes des données. |
| Fréquence de mise à jour | **Irrégulière**, selon les métadonnées du catalogue. |
| Volumétrie | **11 963 lignes et autant de multipolygones**. Huit attributs descriptifs et un identifiant technique `fid`. GeoPackage : environ **9,22 Mo**. |
| Clés disponibles (sur quoi pourra-t-on joindre ?) | `fid` est unique dans ce fichier. `ID_2020` et `ID_2023` comportent des répétitions et des valeurs manquantes. Compatibilité avec d’autres couches **non vérifiée** : aucune jointure réalisée. Aucun code INSEE de commune ; rapprochement géographique envisageable avec les communes ou les feux. |
| Données personnelles | Aucune donnée personnelle repérée dans les attributs examinés : identifiants d’objets et codes de couverture, d’usage et d’ossature du sol. |
| Licence | **Licence Ouverte / Open Licence version 2.0**, indiquée sur la fiche du catalogue. |
| Questions de votre analyse auxquelles elle pourrait répondre | Caractériser l’occupation du sol et son évolution entre 2020 et 2023 dans les zones touchées par les feux, pour contribuer à repérer des secteurs à surveiller. À croiser avec les données de feux, de météo et de moyens disponibles ; cette source seule ne détermine ni les causes des feux ni les priorités de renfort. |
