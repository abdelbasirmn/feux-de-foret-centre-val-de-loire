# FOAD 1 — Diagnostic stratégique et objectifs collectifs V0

**Projet** — Feux de forêt en Centre-Val de Loire, priorité au Loiret (45)  
**Date** — 22 novembre 2026  
**Statut** — Ébauche collective à relire et à valider

## K1 — Diagnostic stratégique

| Niveau | Formulation | Statut et justification |
|---|---|---|
| **Stratégie** | Préparer le SDIS du Loiret à la saison des feux de forêt de l’été 2027. | **Établi.** La direction indique qu’elle prépare l’été 2027 et s’attend à autant de feux qu’en 2026, voire davantage. |
| **Enjeu** | Concentrer les moyens humains et financiers là où ils sont le plus utiles. | **Établi.** La commande indique que le budget ne permet pas de renforcer le dispositif dans tout le département pendant tout l’été. |
| **Objectif** | Éclairer deux décisions : les zones où concentrer les moyens et le niveau de danger à partir duquel envisager un dispositif renforcé. | **Établi.** Ces deux arbitrages sont demandés par le SDIS. Les zones, les périodes et le seuil à recommander restent à déterminer. |
| **Action** | Décrire les feux observés par commune et période, puis comparer plusieurs scénarios de seuil sur les jours couverts par BDIFF et la Météo des forêts. | **Supposé.** Cette méthode est proposée par l’équipe projet. Sa faisabilité dépend de la qualité des données et de la couverture commune. |

Commande du SDIS 45 — Saison feux 2027 · [Analyse d’Abdelbasir](https://github.com/abdelbasirmn/feux-de-foret-centre-val-de-loire/blob/main/docs/analyse/commande-Abdelbasir-MEFIRE_NSANGOU.md) · [Matrice du #13](https://github.com/abdelbasirmn/feux-de-foret-centre-val-de-loire/blob/main/docs/sources/matrice.md)

### Hypothèses et verdicts

| Hypothèse | Comment la tester | Verdict à ce stade |
|---|---|---|
| **H1 — Périodes.** Les périodes avec le plus de départs de feu peuvent différer de celles avec les plus grandes surfaces parcourues. | Sur des périodes comparables, classer les mois selon le nombre de feux, puis selon la surface totale parcourue. Un classement différent appuie l’hypothèse. Des classements concordants sur les saisons comparées l’affaiblissent. | **Impossible de trancher.** Les champs nécessaires sont identifiés. La comparaison n’est pas documentée dans le K1 d’Ange. |
| **H2 — Zones.** Certaines caractéristiques territoriales peuvent être associées à une concentration des feux observés. | Comparer les communes selon les feux observés et les caractéristiques documentées dans les sources territoriales. Tenir compte de la surface forestière et de la couverture des données. Vérifier si l’association persiste après ces contrôles. | **Impossible de trancher.** Le croisement spatial reste à réaliser. Les feux sont localisés à l’échelle communale. |
| **H3 — Seuil.** Un seuil de danger peut couvrir une part utile des jours avec feu tout en limitant les jours de mobilisation simulée. | Pour chaque seuil, compter les jours où il est atteint et les jours avec feu qui restent en dessous. Comparer ces résultats aux contraintes du SDIS quand elles seront connues. L’hypothèse est infirmée sur le périmètre testé si aucun scénario ne respecte les deux critères convenus. | **Impossible de trancher.** L’appariement par date de validité reste à vérifier. Le nombre de jours de renfort supportable par le SDIS reste inconnu. |

[K1 d’Ange](https://github.com/abdelbasirmn/feux-de-foret-centre-val-de-loire/blob/TEMPLATE_KAMGUEM_Ange/kpi/diagnostic-k1-ange-kamguem.md) · [K1 de Thanael](https://github.com/abdelbasirmn/feux-de-foret-centre-val-de-loire/blob/TEMPLATE_BARTHELEMY_Thanael/kpi/k1_diagnostic_strategique_thanael.md) · [Discussion sur l’échéance météo](https://github.com/abdelbasirmn/feux-de-foret-centre-val-de-loire/issues/20#issuecomment-7080758197)

## K2 — Trois objectifs SMART proposés à l’équipe

| Axe et décision | Action | Objectif général | Objectif SMART proposé |
|---|---|---|---|
| **Périodes — Q07. Quand renforcer les moyens ?** | Regrouper les feux et les surfaces par mois. | Mieux cibler les périodes de renfort. | **Pour le contrôle du 6 décembre**, produire un tableau mensuel du Loiret avec le nombre de départs de feu, la surface totale parcourue et le nombre de feux dont la surface est renseignée. Indiquer les mois les plus touchés selon chaque mesure et la période réellement couverte. |
| **Zones — Q01 et Q02. Où concentrer les moyens ?** | Rapprocher les feux des communes et des caractéristiques territoriales disponibles. | Mieux cibler les zones à surveiller. | **Pour la présentation du 11 décembre**, produire une carte communale du Loiret des feux observés qui indique la période couverte, les critères de classement et les données territoriales utilisées. Signaler les communes insuffisamment documentées. |
| **Seuil — Q04, Q06 et Q08. Quel niveau de danger tester ?** | Rapprocher les feux et les prévisions, puis simuler plusieurs seuils. | Améliorer la règle de déclenchement des renforts. | **Pour le contrôle du 6 décembre**, produire un tableau comparant les seuils de la nomenclature météo vérifiée. Pour chaque seuil, indiquer les jours de renfort simulés et les jours avec feu sous le seuil. Utiliser une échéance unique et une période commune vérifiées, puis déclarer le nombre de feux non appariés. Étendre la comparaison régionale si la couverture le permet. |

### H3 — Règles de calcul proposées pour la simulation des seuils

Rapprocher la date de première alerte BDIFF de la date de validité de la prévision pour le Loiret. Utiliser une seule échéance sur une période commune vérifiée. J1 sur 2025 reste à confirmer.

Pour chaque seuil, afficher trois mesures.

- **Jours de renfort simulés** — nombre de jours couverts où le niveau prévu atteint ou dépasse le seuil, sur le total des jours couverts.
- **Jours avec feu sous le seuil** — nombre de jours couverts avec au moins un départ enregistré et un niveau prévu inférieur au seuil, sur le total des jours couverts avec au moins un départ enregistré.
- **Part des départs couverts par le seuil** — nombre de départs appariés à une prévision qui atteint ou dépasse le seuil, divisé par le nombre total de départs appariés.

Compter zéro départ uniquement pour un jour dont la couverture par les deux sources est documentée et pour lequel BDIFF ne recense aucun départ. Présenter séparément les jours hors couverture ou de couverture inconnue et les départs sans prévision associée.

**Références et tests de cohérence**

- **Périodes.** Référence historique **à mesurer**. Couvrir toute la saison pourrait maximiser la part des feux couverts, mais le nombre de jours à mobiliser doit aussi figurer dans le résultat.
- **Zones.** Surface forestière et part des feux couverts **à mesurer**. Classer presque toutes les communes comme prioritaires ferait monter la couverture. Le résultat doit donc montrer aussi l’étendue des zones proposées.
- **Seuil.** Seuil actuel et capacité de mobilisation **à confirmer auprès du SDIS**. Un seuil très bas pourrait couvrir davantage de jours avec feu tout en multipliant les jours de renfort simulés. Les deux mesures doivent être présentées ensemble.

Ange propose des cibles de **90 %** pour les feux et les surfaces couverts par les périodes retenues. Thanael propose **80 %** des feux et **85 %** des surfaces sur au plus **30 %** de la surface forestière. À ce stade, ces valeurs restent des pistes individuelles. Leur faisabilité dépend de la période de référence, des données territoriales et des moyens disponibles. [K2 d’Ange](https://github.com/abdelbasirmn/feux-de-foret-centre-val-de-loire/blob/TEMPLATE_KAMGUEM_Ange/kpi/objectif-k2-ange-kamguem.md) · [K2 de Thanael](https://github.com/abdelbasirmn/feux-de-foret-centre-val-de-loire/blob/TEMPLATE_BARTHELEMY_Thanael/kpi/k2_objectif_smart_thanael.md)

## Suite pour le rendu

**Abdelbasir** coordonne la relecture et consolide les preuves. **Ange** vérifie la faisabilité des calculs et les périodes disponibles. **Thanael** vérifie les critères qualité, les données manquantes et la précision géographique. **L’équipe** choisit les objectifs collectifs et confirme leurs cibles.
