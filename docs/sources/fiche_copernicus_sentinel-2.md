# Fiche d'identité de la source :
## Copernicus Sentinel-2 : Indices de végétation et d'humidité

| Rubrique | Valeur |
| :--- | :--- |
| **Propriétaire et système** | Union Europeenne et Agence Spatiale Europeenne (portail Copernicus Data Space, satellites Sentinel-2A et 2B) |
| **Mode d'accès et format** | Acces via API (openEO, Sentinel Hub, STAC API) et telechargement web direct aux formats GeoTIFF (.tif) et SAFE |
| **Grain (une ligne = ?)** | Un carreau image de 10 m sur 10 m (pour la densite de vegetation) ou 20 m sur 20 m (pour l'humidite des feuilles) a une date de passage du satellite |
| **Emprise géographique** | Couverture mondiale, decoupable sur le departement du Loiret (45) |
| **Période couverte par les donnees** | Données disponibles depuis juin 2015 jusqu'à aujourd'hui (selon les jours sans nuages au-dessus du Loiret) |
| **Date de dernière mise à jour** | A verifier. Catalogue en ligne lors du choix des images non ouvert. |
| **Fréquence de mise a jour** | Tous les 5 jours (a chaque passage du satellite, sous reserve d'une meteo degagee) |
| **Volumétrie** | environ 500 Mo a 1 Go par image complete |
| **Clés disponibles (pour relier les données)** | Coordonnées géographiques (geometry, système de projection EPSG:2154 / EPSG:32631) permettant de croiser les images avec les massifs forestiers (ID de la BD Forêt), les carrés DFCI (NOM) ou les communes du 45 (INSEE_COM), associées à la date de prise de vue (datetime) |
| **Données personnelles** | Non trouvées car il s'agit uniquement de photographies satellites du territoire |
| **Licence** | Règlement délégué (UE) n° 1159/2013 (gratuite et libre d'utilisation avec mention de la source). |
| **Questions de l'analyse concernées** | Q05 : evaluer le manque d'eau reel des arbres (pins de Sologne ou feuillus) pour expliquer certains départs de feu lorsque le risque météo annoncé est bas. |

### Notes et observations complémentaires
- **Faisabilité et pertinence :** Source pertinente sur le plan scientifique mais non retenue dans le temps imparti du projet. Le volume des images satellites et la lourdeur des traitements demandent trop de temps par rapport aux indices de secheresse deja disponibles dans Copernicus ERA5 et a la carte de végétation BD Forêt.