# Fiche d'identité de la source : 
## Météo-France sur les données climatologiques de base - quotidiennes par station

| Rubrique | Valeur |
| :--- | :--- |
| **Propriétaire et système** |Météo-France (via meteo.data.gouv.fr) |
| **Mode d'accès (export, API, téléchargement) et format** |API disponible; export en format csv, fichiers (_RR-T-Vent et _autres-parametres)|
| **Grain (une ligne = ?)** |1 station météorologique (NUM_POSTE), 1 jour (AAAAMMJJ) |
| **Emprise géographique** |France métropolitaine et Outre-Mer mais accès par département via un filtre (Département 45 - Loiret) retenu  |
| **Période réellement couverte par les données** | avant-1949, 1950-2024 et 2025-2026|
| **Date de dernière mise à jour affichée sur la fiche** |3 novembre 2026 (pour les fichiers 1950-2024) et 18 novembre 2026 (pour les fichiers 2025-2026) |
| **Fréquence de mise à jour** |annuel (pour fichiers 1950-2024) et quotidienne (pour les fichiers 2025-2026)|
| **Volumétrie** | pour le département 45, environ 5 à 15 Mo pour 1950-2024 et moins de 500 Ko pour 2025-2026|
| **Clés disponibles (sur quoi pourra-t-on joindre ?)** |Identifiant unique de station (NUM_POSTE) + Coordonnées géographiques de la station (LAT, LON, ALTI), Date (AAAAMMJJ)|
| **Données personnelles** |Non Vérifié : données météorologiques. Aucun nom, aucune adresse, ni aucune donnée permettant d'identifier un individu |
| **Licence** | Licence Ouverte / Open Licence v2.0 (Etalab)|
| **Questions de votre analyse auxquelles elle pourrait répondre** | Où concentrer les moyens? Avec le recalibrage du seuil.  |

---

### Notes et observations complémentaires
* **Faisabilité et pertinence :** *Cette donnée donne la possibilité de calculer l'Indice Forêt Météo (IFM) par secteur (Sologne, Forêt d'Orléans, Gâtinais, Beauce), via des variables physiques brutes (température, humidité relative, vent, précipitations).*