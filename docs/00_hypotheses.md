# Hypothèses et prédictions avant l’analyse

## 1. Question de recherche

Dans cet échantillon, quels facteurs démographiques, cliniques et comportementaux sont associés à la présence d’un accident vasculaire cérébral (AVC) ?

L’objectif est de comparer les associations entre plusieurs facteurs de risque potentiels et la variable `stroke`, puis d’examiner si ces associations persistent après ajustement sur d’autres caractéristiques des individus.

Cette étude est observationnelle. Les résultats seront donc interprétés comme des associations statistiques et non comme des relations causales.

## 2. Prédiction générale

Avant d’examiner les données, je prévois que l’âge élevé, l’hypertension, les maladies cardiaques, une glycémie moyenne élevée, un IMC élevé et le tabagisme seront associés à une probabilité plus élevée d’AVC.

Je prévois également que certaines associations observées dans l’analyse brute diminueront après ajustement, notamment après la prise en compte de l’âge.
## 2. Prédictions générales

Avant d’examiner les résultats, je prévois que l’âge, l’hypertension, un niveau moyen de glucose élevé, un IMC élevé et le tabagisme seront associés à une probabilité plus élevée d’AVC.

Je prévois également que certaines associations observées dans l’analyse brute diminueront après ajustement sur l’âge et sur les autres caractéristiques des individus.

Les prédictions ci-dessous ont été formulées avant l’analyse statistique. Elles ne seront pas modifiées en fonction des résultats obtenus.

## 3. Hypothèses spécifiques

### H1 — Âge

Je prévois une association positive forte entre l’âge et la présence d’un AVC. Plus l’âge augmente, plus la probabilité d’avoir eu un AVC devrait être élevée.

Je m’attends à ce que cette association reste importante après ajustement sur les autres variables.

### H2 — Hypertension

Je prévois que les personnes ayant des antécédents d’hypertension présenteront une probabilité d’AVC plus élevée que les personnes sans hypertension.

Je m’attends à une association relativement forte dans l’analyse brute. Cette association pourrait toutefois diminuer dans le modèle ajusté, notamment en raison des relations de l’hypertension avec l’âge, l’IMC et le niveau moyen de glucose.

Je prévois néanmoins que l’hypertension restera associée à la présence d’un AVC après ajustement sur les autres caractéristiques incluses dans le modèle.

### H3 — Niveau moyen de glucose

Je prévois qu’un niveau moyen de glucose plus élevé sera associé à une probabilité plus élevée d’AVC.

Je m’attends à une association d’intensité modérée. Une partie de cette association pourrait être liée à l’âge, à l’IMC, à l’hypertension ou à d’autres caractéristiques de santé.

### H4 — Indice de masse corporelle

Je prévois qu’un IMC plus élevé sera associé à une probabilité plus élevée d’AVC, avec une association relativement forte.

Cependant, cette association pourrait diminuer après ajustement sur l’âge, l’hypertension et le niveau moyen de glucose.

Il est également possible que la relation entre l’IMC et l’AVC ne soit pas strictement linéaire.

### H5 — Tabagisme

Je prévois que les personnes qui fument actuellement ou qui ont fumé dans le passé présenteront une probabilité d’AVC plus élevée que les personnes n’ayant jamais fumé.

Je m’attends à une association relativement forte. Toutefois, elle pourrait être partiellement expliquée par des différences d’âge et d’état de santé entre les catégories de tabagisme.

La catégorie `Unknown` devra être interprétée avec prudence, car elle indique une information manquante plutôt qu’un comportement tabagique particulier.

### H6 — Type d’emploi

Je ne prévois pas de relation directe forte entre le type d’emploi et l’AVC.

Des différences pourraient néanmoins apparaître dans l’analyse brute, car les catégories professionnelles peuvent avoir des compositions différentes en matière d’âge et d’état de santé. Je prévois donc que ces différences diminueront après ajustement sur l’âge et les variables cliniques.

Cette variable sera principalement considérée comme exploratoire.

### H7 — Type de résidence

Je prévois une association faible, voire inexistante, entre le fait de résider en zone urbaine ou rurale et la présence d’un AVC.

Si une différence est observée, elle pourrait être liée à d’autres caractéristiques des individus plutôt qu’au type de résidence lui-même.

### H8 — Statut matrimonial

Je prévois une association brute d’intensité modérée entre le fait d’avoir déjà été marié et la présence d’un AVC.

Les personnes ayant déjà été mariées pourraient présenter une fréquence d’AVC plus élevée, principalement parce qu’elles sont en moyenne plus âgées que les personnes n’ayant jamais été mariées.

Je prévois donc que cette association diminuera fortement, voire disparaîtra, après ajustement sur l’âge. Le statut matrimonial pourrait ainsi produire une association trompeuse si l’âge n’est pas pris en compte.
### H9 — Maladie cardiaque

Je prévois une association positive forte entre les antécédents de maladie cardiaque et la présence d’un AVC.

Les personnes ayant une maladie cardiaque devraient présenter une probabilité d’AVC plus élevée que les personnes sans maladie cardiaque.

Je prévois que cette association diminuera partiellement après ajustement sur l’âge, l’hypertension, le niveau moyen de glucose et le tabagisme, mais qu’elle restera néanmoins importante.

### H10 — Genre

Je prévois que les hommes présenteront une probabilité d’AVC plus élevée que les femmes dans l’analyse brute.

Une explication possible serait une fréquence plus élevée du tabagisme chez les hommes. Dans ce cas, le tabagisme pourrait constituer un mécanisme intermédiaire entre le genre et l’AVC plutôt qu’un facteur de confusion.

Je prévois donc que l’association entre le genre masculin et l’AVC pourrait diminuer après ajustement sur le tabagisme. Cette comparaison devra également prendre en compte l’âge et les autres caractéristiques cliniques.

La variable disponible dans le jeu de données est nommée `gender`. En l’absence d’informations supplémentaires sur sa définition, elle sera interprétée uniquement selon les catégories enregistrées dans le jeu de données.