# Matrice collective questions × sources

Version : V0  
Date : 19/11/2026  
Ticket associé : #13  
Questions de référence : ticket #11 et PR #12

Cette matrice reprend les 10 questions analytiques validées par le groupe et les confronte aux sources étudiées. Elle permet d'identifier les données exploitables, les limites des fichiers disponibles et les besoins en données complémentaires.

**Sources étudiées**

| ID | Source | Fichier ou données disponibles | Périmètre |
|---|---|---|---|
| S01 | BDIFF | Incendies.csv | Centre-Val de Loire, 2025 |
| S02 | Copernicus CEMS | Indices historiques de danger d'incendie | Extraction à réaliser |
| S03 | Météo des forêts | mdf_2025.csv | France métropolitaine et Corse, saison 2025 |
| S04 | Carroyage DFCI | carroyage_dfci_loiret.xlsx | Loiret et abords |
| S05 | Référentiel des communes | Admin_forêt_donnees_carte_loiret.xlsx | Loiret |
| S06 | BD Forêt | BDFORET_données.csv | Loiret |
| S07 | OCS GE – DIFF | DIFF_D045_2023_2020.xlsx | Loiret, 2020-2023 |
| S08 | Données climatologiques de Météo-France | Trois fichiers CSV compressés | Stations du Loiret, 1950-2026 selon les paramètres |

La liste des sources sera rapprochée de l'inventaire collectif.

**Niveaux de couverture**

- Complet : la source permet de répondre à la question au grain, sur la période et sur l'emprise nécessaires.
- Partiel : la source apporte une partie de la réponse.
- Absent : la source ne contient pas d'information utile pour répondre directement à la question.
- Inconnu : les données nécessaires n'ont pas encore été vérifiées.

**Matrice**

| Question | S01 – BDIFF | S02 – Copernicus CEMS | S03 – Météo des forêts | S04 – Carroyage DFCI | S05 – Communes | S06 – BD Forêt | S07 – DIFF | S08 – Climatologie |
|---|---|---|---|---|---|---|---|---|
| Q01 – Quelles zones du Loiret faut-il renforcer en priorité ? | Partiel : `Code INSEE` et `Surface parcourue (m2)` permettent d'identifier les communes touchées, mais pas les moyens disponibles. | Inconnu : les indices FWI et les mailles géographiques pourraient caractériser le danger local. Extraction à vérifier. | Partiel : `num_dep` et `niveau_j1` renseignent le danger départemental, sans distinction entre communes. | Partiel : les codes DFCI et les géométries permettent de découper le territoire, mais ne renseignent pas le risque. | Partiel : `Code INSEE`, `Population` et `Superficie cadastrale` permettent de caractériser les communes. | Partiel : `CODE_TFV` et `ESSENCE` renseignent la végétation, mais les géométries sont absentes du fichier. | Partiel : `CS_2023`, `US_2023` et les géométries décrivent les objets de la couche de différences. | Partiel : `LAT`, `LON`, `RR`, `TX` et `UM` permettent de caractériser les conditions météorologiques aux stations. |
| Q02 – Quelles caractéristiques du territoire favorisent les incendies ? | Partiel : `Code INSEE`, `Type de peuplement` et les surfaces par catégorie permettent d'étudier les caractéristiques des zones touchées. | Inconnu : les indices documentés pourraient renseigner la sensibilité de la végétation aux conditions météorologiques. | Absent : les niveaux de danger ne détaillent pas les caractéristiques du territoire. | Absent : le découpage DFCI ne renseigne ni la végétation ni l'occupation du sol. | Partiel : `Population` et `Superficie cadastrale` permettent d'étudier la densité de population. | Partiel : `CODE_TFV`, `TFV` et `ESSENCE` décrivent les formations végétales. Leur localisation reste nécessaire. | Partiel : `CS_2023` et `US_2023` renseignent la couverture et l'usage du sol sur les objets disponibles. | Partiel : `ALTI`, `LAT` et `LON` renseignent l'altitude et la localisation des stations, mais pas la topographie complète du territoire. |
| Q03 – Quels moyens le SDIS du Loiret possède-t-il et quelles sont ses principales contraintes ? | Absent : aucune donnée sur les ressources. | Absent : indices de danger uniquement. | Absent : niveaux de danger uniquement. | Absent : découpage géographique uniquement. | Absent : aucune information sur les centres de secours ou leurs effectifs. | Absent : formations végétales uniquement. | Absent : occupation et couverture du sol uniquement. | Absent : observations météorologiques uniquement. |
| Q04 – Les niveaux de danger annoncés par la Météo des forêts correspondent-ils aux départs de feu observés ? | Partiel : `Date de première alerte` et `Département` permettent d'identifier les jours avec feu. | Absent : le FWI ne correspond pas directement aux niveaux annoncés par la Météo des forêts. | Partiel : `date`, `num_dep`, `niveau_j1` et `niveau_j2` permettent de retrouver les niveaux annoncés, mais pas les feux observés. | Absent : aucune donnée sur les feux ou les niveaux annoncés. | Absent : aucune donnée journalière sur les feux ou le danger. | Absent : aucune donnée journalière. | Absent : aucune donnée sur les feux ou les niveaux annoncés. | Absent : les observations météorologiques ne représentent pas directement les niveaux annoncés. |
| Q05 – Quels facteurs peuvent expliquer les départs de feu, notamment lorsque le danger annoncé est faible ? | Partiel : `Nature` renseigne la cause lorsqu'elle est connue. Cette colonne est vide pour les neuf incendies du Loiret dans l'extraction actuelle. | Inconnu : FWI, FFMC, DMC et DC pourraient renseigner les conditions favorables aux incendies. | Partiel : `niveau_j1` permet d'identifier les jours à danger faible, sans expliquer les causes individuelles. | Absent : aucune information sur les facteurs de départ de feu. | Partiel : `Population` permet d'étudier un éventuel lien entre présence humaine et départs de feu. | Partiel : `TFV` et `ESSENCE` permettent d'étudier les caractéristiques de la végétation si les géométries sont récupérées. | Partiel : `CS_2023` et `US_2023` permettent d'étudier le contexte d'occupation du sol. | Partiel : `RR`, `TX`, `FFM` et `UM` permettent d'étudier les conditions météorologiques associées aux incendies. |
| Q06 – Quel niveau de danger devrait déclencher le dispositif renforcé dans le Loiret ? | Partiel : `Date de première alerte` permet d'identifier les jours avec feu et d'évaluer des scénarios de seuil. | Inconnu : les indices pourraient servir de critères complémentaires, mais ne remplacent pas directement les niveaux de la Météo des forêts. | Partiel : `niveau_j1` et `niveau_j2` permettent de comparer des seuils théoriques. Les contraintes du SDIS ne sont pas renseignées. | Absent : aucun niveau de danger ni information de mobilisation. | Absent : aucune information sur le déclenchement du dispositif. | Absent : aucun niveau de danger journalier. | Absent : aucune information sur le seuil opérationnel. | Partiel : `RR`, `TX`, `UM` et `FFM` peuvent servir de critères complémentaires après analyse. |
| Q07 – À quelles périodes de l'année faut-il renforcer les moyens en priorité ? | Partiel : `Date de première alerte` et `Surface parcourue (m2)` permettent d'étudier la saisonnalité des incendies. Une seule année est disponible actuellement. | Inconnu : l'historique des indices pourrait permettre d'étudier la saisonnalité du danger. | Partiel : `date` et `niveau_j1` renseignent les périodes de danger pendant la saison de publication 2025. | Absent : aucune donnée temporelle sur les incendies. | Absent : aucune donnée sur la saisonnalité des incendies. | Absent : aucune observation journalière. | Absent : comparaison de deux millésimes, sans suivi journalier des incendies. | Partiel : `AAAAMMJJ` et les paramètres météorologiques permettent d'étudier les variations saisonnières. |
| Q08 – La relation entre les niveaux de danger annoncés et les départs de feu est-elle la même dans le Loiret et dans les autres départements, à l'échelle régionale et nationale ? | Partiel : `Département` et `Date de première alerte` permettent une comparaison régionale sur l'extraction actuelle. L'historique national reste à récupérer. | Absent : le FWI ne représente pas directement les niveaux annoncés par la Météo des forêts. | Partiel : `num_dep`, `date` et `niveau_j1` permettent une comparaison entre départements, mais ne renseignent pas les départs de feu. | Absent : aucune observation de feu ou de danger. | Absent : fichier limité aux communes du Loiret et sans données de feu ou de danger. | Absent : aucune donnée sur les niveaux de danger et les feux observés. | Absent : aucune donnée sur les niveaux de danger et les feux observés. | Absent : observations limitées aux stations du Loiret et sans niveaux de danger annoncés. |
| Q09 – Dans quelle mesure les autres départements peuvent-ils renforcer les moyens du Loiret ? | Absent : aucun historique des renforts. | Absent : aucune information opérationnelle. | Absent : aucune information sur les renforts. | Absent : aucune information sur les ressources mobilisables. | Absent : aucune donnée sur les conventions entre SDIS. | Absent : aucune information opérationnelle. | Absent : aucune information opérationnelle. | Absent : aucune information sur les renforts. |
| Q10 – Quelles différences entre le Loiret et les autres départements pourraient nous aider à améliorer notre dispositif ? | Partiel : `Département`, `Surface parcourue (m2)` et `Date de première alerte` permettent de comparer les incendies et leurs conséquences. | Inconnu : une extraction sur plusieurs départements permettrait potentiellement de comparer leur exposition au danger. | Partiel : `num_dep` et les niveaux annoncés permettent de comparer les situations de danger. | Absent : le fichier ne contient pas de caractéristiques opérationnelles comparables entre départements. | Partiel : `Population` et `Superficie cadastrale` permettent de caractériser le Loiret. Les données des autres départements restent nécessaires. | Partiel : `TFV` et `ESSENCE` permettent de décrire les formations végétales du Loiret. Une couverture comparable des autres départements est nécessaire. | Partiel : `CS_2023` et `US_2023` permettent de caractériser certains objets du territoire. Les données complètes et celles des autres départements restent nécessaires. | Partiel : les observations météorologiques permettent de caractériser le climat du Loiret. Les fichiers des autres départements restent à récupérer. |

**Lecture de la matrice**

Les questions Q03 et Q09 ne sont couvertes par aucune des sources étudiées. Elles nécessitent des données sur les moyens du SDIS, son organisation, ses contraintes et les possibilités de renfort entre départements.

Les autres questions sont partiellement couvertes. Plusieurs sources devront être rapprochées pour obtenir une réponse exploitable.

Les huit sources présentent un intérêt potentiel pour au moins une question. Cependant, certaines nécessitent une extraction supplémentaire ou une vérification avant leur intégration dans le modèle cible.

La Météo des forêts et Copernicus CEMS ne doivent pas être considérés comme équivalents. La première fournit un niveau de danger annoncé à l'échelle départementale, tandis que le second propose des indices historiques de danger météorologique.

Les observations climatologiques de Météo-France constituent également une source distincte.

**Données manquantes et décisions proposées**

| Question | Données manquantes | Décision proposée | Limite ou coût |
|---|---|---|---|
| Q01 | Localisation des centres de secours, effectifs, véhicules, secteurs couverts et délais d'intervention. | Collecter. | Sans ces données, il est possible de cartographier les zones exposées, mais pas de déterminer précisément les zones insuffisamment couvertes. |
| Q02 | Géométries de BD Forêt, occupation du sol complète, relief, pentes et caractéristiques des interfaces entre forêt et habitat. | Collecter. | Nécessite de récupérer des données géographiques complémentaires et de les rapprocher des incendies. |
| Q03 | Effectifs disponibles, moyens matériels, budget et contraintes de mobilisation. | Collecter. | Certaines informations peuvent nécessiter une demande directe au SDIS. |
| Q04 | Historique commun des feux et des niveaux de danger annoncés sur plusieurs saisons. | Collecter. | L'extraction actuelle permet une première analyse sur 2025, insuffisante pour tirer une conclusion robuste. |
| Q05 | Causes détaillées et circonstances des départs de feu. | Collecter, puis approximer si nécessaire. | Les variables météorologiques et territoriales peuvent être utilisées comme facteurs associés, mais ne prouvent pas les causes réelles des incendies. |
| Q06 | Seuil actuel, budget, disponibilité des équipes et nombre de jours de renfort supportable. | Collecter. | Les sources actuelles permettent de tester des seuils théoriques, mais pas de confirmer leur faisabilité opérationnelle. |
| Q07 | Historique pluriannuel des incendies et calendrier de disponibilité des ressources. | Collecter, puis approximer les besoins avec la fréquence et les surfaces parcourues si nécessaire. | La fréquence des feux ne représente pas directement les besoins de mobilisation. |
| Q08 | Historique national BDIFF et niveaux de danger annoncés sur les mêmes saisons. | Collecter. | Les comparaisons doivent utiliser des périodes et des méthodes de calcul identiques. |
| Q09 | Conventions de renfort, ressources mobilisables, délais, disponibilité et historique des renforts. | Collecter. | Ces données peuvent être partiellement publiques ou nécessiter un échange avec les SDIS concernés. |
| Q10 | Moyens et organisation des autres SDIS, caractéristiques territoriales comparables et résultats opérationnels. | Collecter. | Les différences de superficie, de population, d'exposition et de ressources doivent être prises en compte avant de comparer les départements. |

Ces décisions restent à valider collectivement et à reporter dans le journal des décisions.

**Points de vigilance pour le modèle cible**

- Les incendies BDIFF sont identifiés à l'échelle de la commune.
- La Météo des forêts est disponible à l'échelle du département et du jour de publication. Les prévisions J1 et J2 doivent être rattachées à leur date de validité.
- Les observations climatologiques sont disponibles à l'échelle de la station et du jour.
- Les indices Copernicus sont attendus à l'échelle d'une maille géographique et d'une date.
- Les données DFCI et d'occupation du sol nécessitent des rapprochements géographiques.
- Le passage d'une commune à un carreau ou une maille ne doit pas être considéré comme un rattachement exact sans information de localisation suffisante.
- L'absence d'incendie dans une extraction ne signifie pas nécessairement une absence réelle d'incendie si la couverture des données n'est pas vérifiée.

La matrice sera mise à jour après la récupération et l'évaluation des sources complémentaires.