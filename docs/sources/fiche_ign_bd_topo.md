# Fiche d'identité de la source :
## IGN : BD TOPO (Infrastructures et accès des secours)

| Rubrique | Valeur |
| :--- | :--- |
| **Proprietaire et systeme** | Institut national de l'information geographique et forestiere (IGN), diffuse via la Geoplateforme (cartes.gouv.fr, geoservices.ign.fr) et data.gouv.fr |
| **Mode d'acces et format** | Téléchargement direct par département (archives 7z) ou flux cartographiques WFS aux formats GeoPackage (.gpkg) et Shapefile (.shp) |
| **Grain (une ligne = ?)** | Un objet géographique par ligne : un bâtiment de caserne de pompiers ou un tronçon de route et de piste forestière |
| **Emprise geographique** | France entière, téléchargeable uniquement pour le département du Loiret (45) |
| **Période couverte par les données** | Etat actuel du territoire (date de création ou de mise a jour de chaque équipement disponible dans les colonnes de la table) |
| **Date de dernière mise à jour** | A relever directement sur la fiche de présentation lors du téléchargement sur le site de l'IGN |
| **Fréquence de mise a jour** | Trimestrielle (nouvelle version publiée tous les trois mois par l'IGN) |
| **Volumétrie** | 300 Mo a 800 pour l'archive complète du département du Loiret (D045). moins de 10 Mo une fois filtrée sur les casernes et les routes. |
| **Clés disponibles (pour rélier les données)** | Coordonnées géographiques en projection française Lambert-93 (geom / geometry en EPSG:2154) permettant de calculer les distances vers les carrés DFCI (NOM), ainsi que le code INSEE de la commune (code_insee) |
| **Donnees personnelles** | Non, uniquement des infrastructures publiques et des équipements de secours |
| **Licence** | Licence Ouverte Etalab v2.0 |
| **Questions de l'analyse concernees** | Quelles zones du Loiret faut-il renforcer en priorité ? |

### Notes et observations complémentaires
- **Faisabilité et pertinence :** Source pertinente et facilement exploitable. Une fois filtrée sur les casernes de pompiers et les axes routiers principaux, la donnée peut être croisée avec le carroyage DFCI pour identifier les massifs à fort risque qui sont éloignés des secours.