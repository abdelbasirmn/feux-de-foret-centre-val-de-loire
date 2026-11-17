# Fiche d'identité de la source — Copernicus CEMS

**Fire danger indices historical data from the Copernicus Emergency Management Service**

| Rubrique | Valeur |
| --- | --- |
| Propriétaire et système | Copernicus Emergency Management Service (CEMS), programme de l'Union européenne. Les données sont produites par l'ECMWF pour le JRC dans le cadre d'EFFIS. |
| Mode d'accès et format | Téléchargement depuis la plateforme Early Warning Data Store (EWDS), via un formulaire ou une API. Il faut s'authentifier pour récupérer les données. Les formats proposés sont GRIB et NetCDF4 (expérimental). |
| Grain (une ligne = ?) | Après transformation en tableau, une ligne correspondrait à la valeur d'un indice de danger d'incendie pour une date et une maille géographique. |
| Emprise géographique | Le monde entier, mais on peut sélectionner la zone qui nous intéresse, notamment le Centre-Val de Loire. |
| Période réellement couverte par les données | Du 03/01/1940 au 24/10/2026 d'après les métadonnées STAC consultées. La période réellement disponible pour notre région n'a pas été vérifiée, car le fichier n'a pas été téléchargé. |
| Date de dernière mise à jour affichée sur la fiche | 10/11/2026, d'après l'onglet Documentation. |
| Fréquence de mise à jour | Les données sont régulièrement actualisées en fonction de la disponibilité des données ERA5. Fréquence exacte non vérifiée. |
| Volumétrie | Non vérifiée, car elle dépend de la période, des indicateurs et de la zone géographique que l'on sélectionne. |
| Clés disponibles | La date, la latitude et la longitude. On pourrait les utiliser pour rapprocher ces données de celles de BDIFF en fonction des dates et de la localisation des incendies. |
| Données personnelles | Aucune, il s'agit de données météorologiques et environnementales. |
| Licence | Creative Commons Attribution 4.0 (CC BY 4.0). |
| Questions de mon analyse auxquelles elle pourrait répondre | Cette source pourrait m'aider à identifier les périodes de l'année où le danger d'incendie est le plus élevé. Elle pourrait aussi permettre de comprendre quelles conditions météorologiques favorisent les incendies et d'identifier les zones les plus exposées. En la croisant avec BDIFF, on pourrait voir si les départs de feu sont plus fréquents lorsque les indices de danger sont élevés. |

## Principaux indicateurs disponibles

- FWI : indice forêt météo.
- FFMC : humidité des combustibles fins.
- DMC : humidité de la litière organique.
- DC : indice de sécheresse.
- ISI : indice de propagation initiale du feu.
- BUI : indice de combustible disponible.
- DSR : indice de sévérité journalière.

## Limites identifiées

- Cette source ne donne pas directement les départs de feu, mais plutôt les conditions qui peuvent favoriser les incendies.
- Il n'y a pas de code INSEE permettant de faire directement une jointure avec BDIFF.
- Il faudrait donc effectuer un traitement sur les coordonnées géographiques pour pouvoir croiser les deux sources.
- Je n'ai pas pu vérifier la structure exacte du fichier ni sa volumétrie, car je ne l'ai pas téléchargé.
- Cette source ne permet pas de connaître les moyens humains et matériels disponibles ni les causes réelles des départs de feu.

## Conclusion

Je pense que cette source est intéressante pour notre projet, surtout en complément de BDIFF. BDIFF nous permettrait de savoir où et quand les incendies ont eu lieu, tandis que Copernicus nous permettrait d'analyser les conditions météorologiques à ces moments-là.

Je retiens donc cette source, mais il faudra vérifier par la suite si nous pouvons facilement exploiter les fichiers et les croiser avec BDIFF.