# Glossaire — Centre-Val de Loire


## Indice de danger intégré

- **Définition**:

    *Indicateur calculé par Météo-France pour évaluer le danger météorologique d'éclosion, la vitesse de propagation et l'intensité potentielle d'un feu de forêt. Il combine l'Indice Forêt Météo (IFM : température, humidité de l'air, vitesse du vent, précipitations) avec l'état de sécheresse de la végétation et les relevés de terrain de l'Office national des forêts (ONF).*


- **Sources et colonnes** :

    - *https://confluence-meteofrance.atlassian.net/wiki/spaces/OpenDataMeteoFrance/pages/874741792/Donn+es+expertis+es#%F0%9F%8C%B3-M%C3%A9t%C3%A9o-des-for%C3%AAts*

- **Divergences :**
- **Règle retenue :** (lien vers la décision)
- **Unité ou granularité** :*département,jour*

- **Statut :** proposé
- **Origine de la définition** :*Documentation officielle Météo-France (La Météo des forêts — Qu'est-ce que l'Indice de danger intégré de Météo-France ?, PDF p. 3).*
- **Ajouté par :** Thanael Barthelemy, 2026-11-17

---

## Météo des forêts

- **Définition**:

    *La Météo des forêts indique les départements dans lesquelles les conditions météorologiques peuvent aggraver le risque de feux de forêts et de végétation*.

    *La Météo des forêts est conçue pour informer et sensibiliser le public au risque de feux de forêts et de végétation. Elle doit permettre à chacun d’adopter les bons réflexes au quotidien pour éviter les départs de feux.*

- **Sources et colonnes** :

    *https://static.data.gouv.fr/resources/archives-de-la-meteo-des-forets/20260909-143937/donnees-expertisees-presentation-meteodesforets-20260909.pdf* 


    *https://confluence-meteofrance.atlassian.net/wiki/spaces/OpenDataMeteoFrance/pages/874741792/Donn+es+expertis+es#%F0%9F%8C%B3-M%C3%A9t%C3%A9o-des-for%C3%AAts*

- **Divergences :**
- **Règle retenue :** (lien vers la décision)
- **Unité ou granularité** :*département,jour*
- **Exemple :**

| date | num_dep | niveau_j1 | niveau_j2 | nom_dep |
| :--- | :--- | :--- | :--- | :--- |
| 2026-06-18T14:50:04Z | 45 | 3 | 2 | Loiret |

    Avec niveau_j1 et niveau_j2 : indice quotidien de risque évalué sur une échelle de 1 à 4 (1 = Faible, 2 = Modéré, 3 = Élevé, 4 = Très élevé), correspondant respectivement aux prévisions pour demain (J1) et après-demain (J2).

- **Statut :** proposé
- **Origine de la définition** :*Documentation officielle Météo-France (La Météo des forêts — Qu’est-ce que la Météo des forêts?, PDF p. 1) et wiki Open Data Météo-France.*
- **Ajouté par :** Thanael Barthelemy, 2026-11-17

---



