# Facteurs associés à l'AVC chez les adultes : analyse multivariée

Analyse transversale reproductible (R et Quarto) du jeu de données public *Stroke Prediction Dataset* : qualité des données, description de la population et régression logistique multivariée.

**Rapport en ligne :** <https://jade-yi.github.io/stroke-data-cleaning-analysis/>

## Présentation

Ce projet documente une démarche complète et transparente, de la vérification de la qualité des données à la modélisation :

- évaluation de la structure, des valeurs manquantes (explicites et implicites) et des valeurs improbables ;
- définition d'une population analytique (adultes) et documentation de chaque exclusion ;
- description de la population selon le statut AVC ;
- régression logistique multivariée, résultats exprimés en *odds ratios* (OR) ajustés avec IC à 95 % ;
- vérification de la linéarité des variables continues (splines naturels, test du rapport de vraisemblance) ;
- analyse de sensibilité évaluant l’influence des valeurs extrêmes de l’IMC par winsorisation.

Le rapport suit les recommandations STROBE. Le projet ne vise ni la prédiction (pas de modèle d'apprentissage automatique) ni l'estimation d'effets causaux.

## Question de recherche

> Quels facteurs démographiques, cliniques et comportementaux sont associés au statut AVC chez les adultes de ce jeu de données ?

## Données

- **Source :** *Stroke Prediction Dataset*, Kaggle : <https://www.kaggle.com/datasets/fedesoriano/stroke-prediction-dataset>
- **Fichier brut :** `data/raw/healthcare-dataset-stroke-data.csv` (5 110 individus, 12 variables), conservé tel quel ; toutes les transformations sont réalisées dans R.
- **Variables :** `id`, `gender`, `age`, `hypertension`, `heart_disease`, `ever_married`, `work_type`, `Residence_type`, `avg_glucose_level`, `bmi`, `smoking_status`, `stroke`.
- **Droits de réutilisation :** voir la page Kaggle du jeu de données.

## Population analytique

Analyse restreinte aux adultes (âge ≥ 18 ans). Sont également exclus l'unique individu `gender = "Other"` et les individus `work_type = "Never_worked"` (effectif très faible, aucun AVC, séparation dans le modèle). Le détail des effectifs figure dans le rapport.

## Principaux résultats

Après ajustement, l’âge (OR = 1,08 par année ; IC à 95 % : 1,07–1,09), l’hypertension (OR = 1,49 ; IC à 95 % : 1,07–2,05) et la glycémie moyenne (OR = 1,04 par +10 mg/dL ; IC à 95 % : 1,02–1,07) restent associés au statut AVC.

## Limites d'interprétation

Le jeu de données ne documente pas :

- la population source, le mode d'échantillonnage ni les dates de recrutement ;
- la définition de l'AVC (premier événement ou non), sa date ni son type ;
- le moment de mesure des autres variables par rapport à l'AVC ;
- la durée de suivi.

En conséquence, l'analyse ne permet d'estimer ni une incidence ni une prévalence en population, d'établir une temporalité ni de conclure à un lien causal. La proportion d'AVC décrit uniquement ce fichier.

## Structure du dépôt

```text
stroke-data-cleaning-analysis/
├── data/
│   ├── raw/                         # données brutes et documentation de provenance
│   └── processed/                   # jeux de données générés par le code
├── R/                               # scripts de traitement et d'analyse
├── figures/                         # figures exportées hors du rapport
├── docs/                            # site généré pour GitHub Pages
├── index.qmd                        # page d'accueil du site
├── stroke_multivariable_analysis.qmd # rapport d'analyse principal
├── 00_hypotheses.md                 # hypothèses formulées avant l'analyse
├── 01_decision_log.md               # journal des décisions méthodologiques
├── 02_ai_audit_log.md               # journal de revue de l'utilisation de l'IA
├── references.bib
├── _quarto.yml                      # configuration du site Quarto
├── renv/
├── renv.lock                        # versions des packages R
├── stroke-data-cleaning-analysis.Rproj
├── LICENSE
└── README.md
```

## Reproduire l'analyse

Prérequis : R (version ≥ 4.1, opérateur `|>`), [Quarto](https://quarto.org) et RStudio (recommandé).

```bash
git clone https://github.com/Jade-YI/stroke-data-cleaning-analysis.git
cd stroke-data-cleaning-analysis
```

Ouvrir `stroke-data-cleaning-analysis.Rproj` dans RStudio, puis restaurer l'environnement :

```r
renv::restore()
```

Générer le rapport :

```bash
quarto render
```

Le site est écrit dans `docs/`. La sortie PDF éventuelle nécessite une installation LaTeX (par exemple `quarto install tinytex`).

Les chemins sont relatifs à la racine du projet (ex. `data/raw/healthcare-dataset-stroke-data.csv`) ; ne pas déplacer `index.qmd`.

## Usage d'outils d'intelligence artificielle

Des outils d'IA générative ont été utilisés comme aide au projet. Les choix méthodologiques ont été décidés et validés par l'auteure, qui a relu et vérifié le code, les données, les résultats et leur interprétation. Deux documents tenus pendant le projet tracent cette démarche : un **journal des décisions** méthodologiques et un **journal de revue des contenus produits avec l'IA**. L'auteure assume l'entière responsabilité du contenu.

## Outils

R, Quarto, Git/GitHub, `renv`. Principaux packages : `tidyverse`, `gtsummary`, `broom`, `gt`, `splines`, `ggdag`. La liste exacte et les versions figurent dans `renv.lock`.

## Statut

Version de travail : Analyse principale terminée ; documentation et présentation du dépôt en cours de finalisation.

## Auteure

Jade YI (Jiahui YI)

## Licence

Code publié sous licence MIT (voir `LICENSE`). Les données restent soumises à la licence de leur source.