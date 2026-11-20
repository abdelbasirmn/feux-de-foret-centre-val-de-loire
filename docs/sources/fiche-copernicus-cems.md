# Fiche d'identité de la source — Copernicus CEMS

**Fire danger indices historical data from the Copernicus Emergency Management Service**

Auteur : Ange Kamguem

Dernière actualisation : 20/11/2026

Notebook associé : `notebooks/01_exploration_copernicus.ipynb`

## 1. Description de la source

| Rubrique | Valeur |
| --- | --- |
| Propriétaire et système | Copernicus Emergency Management Service (CEMS), programme de l'Union européenne. Les données sont produites par l'ECMWF pour le JRC dans le cadre d'EFFIS. |
| Mode d'accès et format | Téléchargement depuis la plateforme Early Warning Data Store (EWDS), via un formulaire ou une API avec authentification. Les formats proposés sont GRIB et NetCDF4 (expérimental). Deux fichiers GRIB ont été téléchargés et explorés avec Python, notamment avec les bibliothèques xarray et cfgrib. |
| Grain (une ligne = ?) | Après transformation en tableau, une ligne correspond à un jour et à un point géographique, avec les valeurs des différents indices de danger d'incendie disponibles. |
| Emprise géographique | La source couvre le monde entier. L'extraction étudiée correspond à une zone englobant le Centre-Val de Loire, avec 92 points géographiques. Les latitudes vont de 46,229489° à 48,758762° et les longitudes de 0° à 3,375°. Le rattachement exact aux limites administratives reste à réaliser. |
| Période réellement couverte par les données | Du 01/01/2025 au 31/12/2025 pour les fichiers téléchargés. La couverture globale annoncée dans les métadonnées STAC consultées s'étend du 03/01/1940 au 24/10/2026. |
| Date de dernière mise à jour affichée sur la fiche | 10/11/2026, d'après l'onglet Documentation consulté initialement. |
| Fréquence de mise à jour | Les données sont régulièrement actualisées en fonction de la disponibilité des données ERA5. La fréquence exacte de mise à jour reste non vérifiée. Les observations des fichiers étudiés sont journalières. |
| Volumétrie | Deux fichiers GRIB représentant environ 1,57 Mo. Le premier semestre contient 16 652 observations et le second 16 928, soit 33 580 observations potentielles après consolidation. |
| Clés disponibles | Date, latitude et longitude. Cette combinaison permet d'identifier une observation. Aucun code INSEE n'est disponible pour effectuer directement une jointure avec BDIFF. |
| Données personnelles | Aucune donnée personnelle identifiée dans le schéma exploré. Il s'agit de données météorologiques et environnementales. |
| Licence | Creative Commons Attribution 4.0 (CC BY 4.0). |
| Questions de mon analyse auxquelles elle pourrait répondre | Identifier les périodes de l'année où le danger d'incendie est le plus élevé, étudier les conditions météorologiques favorisant les incendies et identifier les zones les plus exposées. En croisant cette source avec BDIFF, on pourrait également étudier la relation entre les indices de danger et les départs de feu réellement observés. |

## 2. Fichiers explorés

| Fichier | Période | Jours | Points géographiques | Observations | Indices |
| --- | --- | ---: | ---: | ---: | ---: |
| `936ba94bf6f92dd937c247c733c78419 (1).grib` | 01/01/2025 – 30/06/2025 | 181 | 92 | 16 652 | 14 |
| `82ed0e77832c9b72adfc8d0f7b7ae554 (1).grib` | 01/07/2025 – 31/12/2025 | 184 | 92 | 16 928 | 7 |
| Total | Année 2025 | 365 | 92 | 33 580 | 7 indices communs |

Les deux fichiers utilisent la même grille géographique de type `reduced_gg` (grille gaussienne réduite).

## 3. Schéma des données

### 3.1. Colonnes temporelles, géographiques et techniques

| Colonne | Description | Type ou nature |
| --- | --- | --- |
| `time` | Date et heure de référence | Date/heure |
| `values` | Position du point dans la grille géographique | Entier |
| `step` | Décalage temporel par rapport à la date de référence | Durée |
| `surface` | Niveau de surface associé aux données | Numérique |
| `latitude` | Latitude du point géographique | Numérique |
| `longitude` | Longitude du point géographique | Numérique |
| `valid_time` | Date et heure de validité de la donnée | Date/heure |

### 3.2. Indices communs aux deux fichiers

| Colonne | Indice | Description | Type |
| --- | --- | --- | --- |
| `fwinx` | FWI | Indice forêt météo, représentant le danger météorologique d'incendie | float32 |
| `ffmcode` | FFMC | Indice d'humidité des combustibles fins | float32 |
| `dufmcode` | DMC | Indice d'humidité de la litière organique | float32 |
| `drtcode` | DC | Indice de sécheresse des couches organiques profondes | float32 |
| `infsinx` | ISI | Indice de propagation initiale du feu | float32 |
| `fbupinx` | BUI | Indice de combustible disponible pour la combustion | float32 |
| `fdsrte` | DSR | Indice de sévérité journalière | float32 |

### 3.3. Indices supplémentaires du premier semestre

| Colonne | Description | Type | Unité affichée |
| --- | --- | --- | --- |
| `kbdi` | Indice de sécheresse de Keetch-Byram | float32 | Numeric |
| `drtmrk` | Facteur de sécheresse australien | float32 | Numeric |
| `fdimrk` | Indice australien de danger d'incendie | float32 | Numeric |
| `scnfdr` | Composante de propagation du feu | float32 | Numeric |
| `buinfdr` | Indice de combustion | float32 | Numeric |
| `icnfdr` | Composante d'allumage | float32 | % |
| `ercnfdr` | Composante de libération d'énergie | float32 | J/m² |

Ces sept indices supplémentaires ne sont pas présents dans le fichier du second semestre.

## 4. Premiers contrôles de qualité

Les contrôles ont été réalisés dans le notebook `notebooks/01_exploration_copernicus.ipynb`.

| Contrôle | Premier semestre | Second semestre |
| --- | --- | --- |
| Dates manquantes | 0 | 0 |
| Dates en doublon | 0 | 0 |
| Coordonnées géographiques en doublon | 0 | 0 |
| Complétude des variables présentes | 100 % | 100 % |
| Nombre de points géographiques | 92 | 92 |

La comparaison des coordonnées géographiques confirme que les deux fichiers utilisent les mêmes points.

Cependant, une différence de schéma a été identifiée : le premier semestre contient 14 indices, contre 7 au second semestre. Les sept indices supplémentaires ne permettent donc pas une analyse sur l'ensemble de l'année avec les fichiers actuels.

La complétude des valeurs est satisfaisante pour les variables présentes, mais la cohérence des schémas doit être prise en compte lors de la consolidation.

## 5. Limites identifiées

- Cette source ne donne pas directement les départs de feu, mais les conditions météorologiques pouvant favoriser les incendies.
- Elle ne contient pas de code INSEE permettant une jointure directe avec BDIFF.
- Un traitement géographique sera nécessaire pour rattacher les points aux communes ou départements.
- La résolution spatiale exacte de la grille reste non vérifiée.
- Les fichiers téléchargés couvrent uniquement l'année 2025, ce qui limite les analyses historiques sur plusieurs années.
- Sept indices ne sont disponibles que pour le premier semestre.
- La source ne permet pas de connaître les moyens humains et matériels disponibles ni les causes réelles des départs de feu.
- Les indices Copernicus ne doivent pas être assimilés directement aux niveaux de danger de la Météo des forêts.

## 6. Proposition d'intégration dans le modèle cible

Pour une première version du modèle cible, je propose :

- De conserver les fichiers bruts dans leur format d'origine.
- De retenir les sept indices communs aux deux semestres pour disposer d'un périmètre annuel homogène.
- De consolider les deux fichiers par union des observations.
- De conserver une granularité journalière par point géographique.
- De prévoir un rattachement géographique permettant le rapprochement avec BDIFF et les autres sources du projet.

Ces propositions restent à valider collectivement.

## 7. Conclusion

L'exploration a permis de confirmer que les fichiers Copernicus sont accessibles et exploitables avec Python. Les données présentent une bonne complétude pour les indices disponibles, une couverture journalière continue sur l'année 2025 et une grille géographique identique entre les deux semestres.

Je retiens cette source en complément de BDIFF pour analyser les relations entre le danger météorologique d'incendie et les incendies réellement observés.

Le prochain travail consistera à intégrer ces données dans le modèle cible et à définir les règles de rapprochement temporel et géographique avec les autres sources.