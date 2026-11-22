# K1 - Diagnostic stratégique

**Auteur :** Thanael BARTHELEMY
**Date :** 22/11/2026
**Question analytique :** Q02 — Quelles caractéristiques du territoire favorisent les incendies ?

## 1. Diagnostic

| Niveau | Formulation | Statut | Justification |
|---|---|---|---|
| *Stratégie* | Préparer le SDIS du Loiret (*45*) pour la saison des feux de forêt *2027*. | Établi | Le SDIS s'attend à autant de feux qu'en *2026*, voire davantage. |
| *Enjeu* | Concentrer les moyens humains et financiers là où ils sont vraiment utiles. | Établi | Le budget ne permet pas de renforcer le dispositif partout dans le département pendant tout l'été. |
| *Objectif* | Cibler en priorité les zones forestières dont les caractéristiques physiques favorisent les départs de feu. | Supposé | La commande demande où concentrer les moyens, mais ne précise pas quels critères géographiques comptent le plus dans le Loiret. |
| *Action* | Croiser l'historique des feux (*BDIFF*) avec les données sur la végétation (*BD Forêt V2*), les routes/bâtiments (*BD TOPO*) et le relief (*BD ALTI*). | Supposé | Ce croisement devrait permettre de repérer le profil des zones les plus exposées. |

## 2. Hypothèse

Dans le Loiret (*45*), les départs de feu et les plus grandes *surfaces parcourues* se concentrent surtout dans les secteurs qui cumulent des essences résineuses inflammables, une forte proximité avec les routes ou les habitations, et des zones difficiles d'accès.

Cette hypothèse permet de vérifier sur quels critères appuyer le futur zonage du SDIS.

Pour la tester, on croise les communes touchées dans *BDIFF* avec les couches géographiques *BD Forêt V2*, *BD TOPO* et *BD ALTI*.

- **Confirmation :** Une nette majorité des feux historiques du Loiret se situe dans des communes qui présentent ces caractéristiques précises.
- **Infirmation :** Les départs de feu sont répartis un peu partout dans les forêts du département, sans lien clair avec le type d'arbres, le relief ou la proximité des infrastructures.

## 3. Confrontation aux résultats disponibles

Dans la base *BDIFF* nettoyée pour le Loiret (*45*), nous disposons de *135* feux exploitables avec un *Code INSEE* valide.

En revanche, le croisement spatial avec *BD Forêt V2*, *BD TOPO* et *BD ALTI* n'a pas encore été lancé.

## 4. Verdict

Impossible de trancher pour le moment.

Deux limites sont déjà visibles dans les données : nous devons travailler à l'échelle de la commune (*Code INSEE*) faute de coordonnées GPS précises pour chaque feu, et la cause des incendies (*Nature*) manque dans *82,96 %* des cas, ce qui empêche de relier directement le terrain à l'origine humaine ou naturelle du départ de feu.