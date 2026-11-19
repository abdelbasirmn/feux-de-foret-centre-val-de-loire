# Inventaire des sources

| Source | Explorée par | Pertinente pour nos questions ? | Ce que nous avons découvert |
| :--- | :--- | :--- | :--- |
|Météo-France (Météo des forets)|Thanael |Oui|Granularité non conforme (un indicateur aggrégé pour tout le département). Cependant permettrait facilement des comparaison en tre departements e, regions et territoir. Mais aussi le niveau d'efficacité de la nouvelle métrique calculée.|
|Météo-France (données climatologiques)|Thanael |Oui |Les données climatoligiques fournissent toutes les variables physiques nécessaires pour recalculer l'Indice Forêt Météo (IFM) par zone géographique spécifique à l'intérieur du département du Loiret. Pour les données manquantes sur les facteurs clés dans le calcul de l'indice, nous devrons opérer par proxy.|
|Carroyage-dfci-2km|Karine  |Oui |les pompiers  communiquent par code carré DFCI. Facilite la conversion des résultats directement par maille DFCI dans leur logiciel opérationnel|
|OCS GE (Loiret, 2023)|Karine |Oui |Cette carte vectorielle distingue les forêts, des champs et des maisons. Elle permettrait de repérer les zones les plus critiques par exemple là où les maisons touchent la forêt ( risque de perte de vie humaine en cas d'incendie) et d'éliminer les zones sans forêt pour éviter d'envoyer des pompiers inutilement.|
|Copernicus CEMS|Ange |Oui|Les sous-indices ERA5 de sécheresse des sols (DC) et de combustible disponible (BUI) pour mesurer l'assèchement cumulé des massifs permettent d'aller au delà de l'IFM calculé et permettrait d'anticiper l'embrasement des feux. Cependant, l'indice global FWI est en revanche écarté  car grille de 9 à 25 km trop large et seuils européens inadaptés au Loiret comparé à notre IFM local calculé sur les stations Météo-France du département.|
|BDIFF|Ange |Oui | Fournit l'historique officiel des incendies réels dans le Loiret : dates exactes d'alerte, communes (codes INSEE) et surfaces brûlées, essentiels pour recalibrer nos seuils d'IFM sur des départs de feu avérés. En revanche, les causes détaillées et les moyens engagés sont souvent manquants, donc peuvent être une source de biais|
|BD Forêt® V2|Abdelbasir | Oui|Renseigne sur les formations végétales et la distinction précise entre les differents peuplements des végétations (très inflammables vs moins sensibles). Dans ce cas, les modalités à très faible combustibilité (comme les peupleraies ou les boisements humides de vallée) ne sont pas pertinets pour l'analyse. |
|ADMIN EXPRESS|Abdelbasir |Oui|Elle fournit les contours géométriques officiels des communes et du département du Loiret ainsi que les codes INSEE, indispensables pour lier les feux de la BDIFF (ne contenant pas de coordonnées GPS précises) au reste de la base via le DFCI d'. |

---

## Bilan de l'exploration

### Quelles questions de vos analyses n'ont encore aucune source ?
*Votre réponse ici...*

### Quelle source vous a surpris, et pourquoi ?
*Votre réponse ici...*

### Quelle source semble utile mais inexploitable dans le temps du projet ?
*Votre réponse ici...*