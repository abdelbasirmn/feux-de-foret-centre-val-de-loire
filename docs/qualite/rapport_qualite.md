# Profilage et Rapport de Qualité — Région Centre-Val de Loire (Loiret - 45)

## 1. Profilage chiffré des sources communes

### Source 1 : BDIFF — Historique des incendies de forêt (*Incendies.csv*, Loiret 45)
* **Volume et période :** On recense *135* incendies entre le *2015-04-10* et le *2025-07-18*, répartis sur 10 années distinctes.
* **Localisation, unicité et clés :** Les feux sont localisés à l'échelle de la commune (*Code INSEE* et *Nom de la commune*). Le fichier ne contient aucun doublon sur l'identifiant *(Année, Numéro)* et couvre *83* communes du Loiret, toutes reconnues sans erreur dans la liste officielle de l'INSEE (*Code INSEE* allant de *45004* à *45347*).
* **Taux de remplissage :**
  * **Champs complets à 100 % :** Toutes les informations indispensables à notre analyse sont présentes (*Année*, *Numéro*, *Département*, *Code INSEE*, *Nom de la commune*, *Date de première alerte*, *Surface parcourue (m2)* comprise entre *5 m²* et *2 500 000 m²*, *Surface forêt (m2)* comprise entre *0* et *1 200 000 m²*, et *Précision des surfaces*).
  * **Champs incomplets ou vides :** La cause du départ de feu (*Nature*) n'est renseignée que dans *17,04 %* des cas (*112* lignes vides), et la mention *Décès ou bâtiments touchés* dans *11,85 %* des cas (*119* lignes vides). Les colonnes *Surface maquis garrigues (m2)* et *Type de peuplement* sont quant à elles entièrement vides (*0 %*).

### Source 2 : Météo des forêts — Prévision départementale (*mdf_2024..csv* à *mdf_2026..csv*)
* **Volume et période :** L'ensemble regroupe *35 616* lignes sur la France entière, couvrant *371* journées de publication du *2024-06-03* au *2026-10-05* (uniquement durant la saison d'été, de juin à octobre), soit une validité **J1** du *2024-06-04* au *2026-10-06*.
* **Anomalies repérées lors de l'audit :**
  * **Changement de nom de colonne :** D'une année sur l'autre, le nom du département change de colonne : il apparaît sous *nom_dep* dans deux fichiers (*67,65 %* des lignes) et sous *dep_nom* dans le troisième (*32,35 %* des lignes).
  * **Format du numéro de département :** La colonne *num_dep* affiche *105* codes différents pour *96* départements réels, car le zéro initial devant les départements *1* à *9* a sauté dans l'un des fichiers.
  * **Niveaux de danger :** Les indicateurs *niveau_j1* et *niveau_j2* sont complets à *100 %* et respectent tous l'échelle officielle allant de *1* (Faible) à *4* (Très élevé).

### Test de croisement entre *BDIFF* et *Météo des forêts*
* **Sur toute la période 2015–2025 (*135* feux) :** *126* feux (*93,33 %*) n'ont pas de bulletin météo associé (contre *9* feux appariés, soit *6,67 %*), tout simplement parce que le dispositif *Météo des forêts* n'existait pas avant 2023.
* **Sur la période commune 2024–2025 (*9* feux) :** Tous les incendies du Loiret retrouvent leur bulletin météo sans aucune perte (*100 %* de correspondance après remise au format sur 2 chiffres de *num_dep*), aussi bien sur la date de validité **J1** (`date_publication + 1 jour`) que sur **J2** (`date_publication + 2 jours`) : *0* feu a eu lieu en niveau *1* (Faible), *8* en niveau *2* (Modéré) et *1* en niveau *3* (Élevé).
* **Jours couverts sans feu enregistré :** En comptant uniquement les jours couverts par les deux sources (validité **J1** de *Météo des forêts* jusqu'au *2025-07-18*, date du dernier feu *BDIFF*), on recense *159* jours sans feu enregistré dans le Loiret.

---

## 2. Règles de qualité retenues

| N° | Dimension | Ce que l'on contrôle | Règle à respecter | Seuil d'alerte (et justification) | Action en cas d'erreur |
|---|---|---|---|---|---|
| **RQ-01** | Validité géographique | *Code INSEE* dans *BDIFF* (toutes les lignes du Loiret) | Le code ne doit pas être vide, doit comporter 5 chiffres (en gardant le zéro devant) et exister dans le référentiel officiel INSEE. | *> 0 %* d'erreur (notre audit affiche *0 %* d'erreur sur les *83* communes du Loiret). | **Bloquer** le chargement et écarter la ligne en rejet. |
| **RQ-02** | Vraisemblance des mesures | *Surface parcourue (m2)* dans *BDIFF* (toutes les lignes) | La surface doit être renseignée, strictement supérieure à *0* et inférieure à *50 000 000* (soit 5 000 hectares maximum plausibles dans la région). | *> 1 %* de valeurs vides ou aberrantes (notre audit va de *5 m²* à *2 500 000 m²*, soit *0 %* hors limite). | **Alerter** et isoler les lignes suspectes pour vérification. |
| **RQ-03** | Unicité et format | Couple *(num_dep, date)* et *niveau_j1* dans *Météo des forêts* | Un seul bulletin par département et par jour (après remise sur 2 chiffres du numéro de département), et un *niveau_j1* compris entre *1* et *4*. | *> 0 %* de doublon après correction ou de note hors *{1..4}* (nos *105* codes bruts se ramènent bien à *96* départements sans doublon). | **Bloquer** en cas de doublon ou de niveau invalide. |

---

## 3. Bilan : ce que ces données permettent d'affirmer (et leurs limites)

* **Ce que nous pouvons affirmer avec certitude :**
  * **La carte et l'ampleur des feux (2015–2025) :** Grâce à des codes communes propres à *100 %* et des surfaces systématiquement renseignées, nous pouvons situer précisément les *135* incendies du Loiret à l'échelle de la commune et mesurer leur étendue (jusqu'à *250 hectares* pour le plus grand).
  * **Le lien avec les alertes météo récentes (2024–2025) :** Sur les étés récents, chaque feu recensé dans le département correspond bien à un bulletin *Météo des forêts* valide, sans aucun décalage de date ni donnée perdue (sur la validité **J1** comme **J2**).

* **Ce que ces données ne permettent pas de dire :**
  * **L'origine des départs de feu :** Comme la cause (*Nature*) manque dans *82,96 %* des dossiers du Loiret, il serait faux de vouloir chiffrer la part d'accidents ou d'actes malveillants.
  * **La fiabilité des alertes sur dix ans (2015–2023) :** *Météo des forêts* étant un dispositif récent (*93,33 %* des feux historiques n'ont pas de bulletin associé), il faut obligatoirement s'appuyer sur les relevés quotidiens des stations Météo-France pour reconstituer le danger météo sur l'ensemble de la décennie.
  * **Les écarts de risque d'une commune à l'autre :** Bien que les feux soient localisés à l'échelle de la commune dans *BDIFF*, le niveau de danger *Météo des forêts* étant publié pour tout le département en bloc, il ne permet pas de distinguer si le risque est plus élevé en forêt d'Orléans qu'en Beauce le même jour.

---

## 4. Fichiers utilisés et étapes pour relancer le notebook

* **Fichiers sources utilisés :**
  * `data/brutes/bdiff/Incendies.csv`
  * Fichiers du dossier `data/brutes/météo-des-forêts/` : `mdf_2024..csv` (*120* bulletins), `mdf_2025..csv` (*120* bulletins) et `mdf_2026..csv` (*131* bulletins)

  https://oxymis-my.sharepoint.com/:u:/r/personal/t_barthelemy_hetic_eu/Documents/feux-de-foret-centre-val-de-loire_Loiret(45)_donn%C3%A9es_brutes.zip?d=w663a322d77be4a90b4581572dfbd4328&csf=1&web=1&e=iapNfN

  ---
* **Étapes pour relancer le notebook (`scripts_audit_qualite_et_cles.ipynb`) :**
  1. Vérifier que l'environnement Python dispose de la bibliothèque `pandas`.
  2. Vérifier dans la première cellule de code que les chemins `chemin_bdiff` (`data/brutes/bdiff/Incendies.csv`) et `dossier_mdf` (`data/brutes/météo-des-forêts`) correspondent à l'arborescence locale.
  3. Exécuter les cellules de manière séquentielle de l'étape 1 à l'étape 4 (chargement de *BDIFF*, chargement de *Météo des forêts* et calcul des dates de validité **J1**/**J2**, croisement sur la date de validité, puis génération du bilan chiffré).
