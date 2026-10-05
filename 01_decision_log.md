---
title: "Journal des décisions méthodologiques"
---

# Journal des décisions analytiques

Ce document enregistre les principales décisions prises au cours du projet, leur justification et leur impact potentiel sur l’analyse.

Les décisions sont enregistrées au moment où elles sont prises. Si une décision est modifiée ultérieurement, l’entrée initiale ne sera pas supprimée : une nouvelle entrée expliquera la modification.

****

## DEC-001 — 2026-09-20

**Étape :** Pré-analyse

**Décision :**  
L’objectif principal du projet est de comparer les associations entre plusieurs facteurs de risque potentiels et la présence d’un AVC.

**Justification :**  
Le jeu de données est observationnel et ne fournit pas suffisamment d’informations sur la temporalité des variables. Il n’est donc pas possible d’interpréter directement les associations observées comme des relations causales.

**Conséquence pour l’analyse :**  
Les résultats seront présentés comme des associations statistiques. Les termes tels que « cause », « effet causal » ou « provoque » seront évités.

**Statut :** Adoptée

**Entrée AI associée :** AI-001

****

## DEC-002 — 2026-09-20

**Étape :** Pré-analyse

**Décision :**  
Les hypothèses concernant l’âge, l’hypertension, les maladies cardiaques, le niveau moyen de glucose, l’IMC, le tabagisme, le genre, le statut matrimonial, le type d’emploi et le type de résidence ont été formulées avant l’analyse statistique.

**Justification :**  
Cette démarche permet de comparer les prédictions initiales aux résultats obtenus et de réduire le risque d’interpréter rétrospectivement les résultats comme s’ils avaient été prévus.

**Conséquence pour l’analyse :**  
Les hypothèses originales seront conservées même si elles ne sont pas confirmées par les données.

**Statut :** Adoptée

**Entrée AI associée :** AI-001

****

## DEC-003 — 2026-09-21

**Étape :** Évaluation initiale de la qualité des données

**Décision :**  
Une évaluation systématique de la qualité des données sera réalisée avant toute analyse statistique ou modélisation.

Cette évaluation comprendra les éléments suivants :

1. la source et la provenance des données ;
2. la structure initiale du jeu de données, notamment le nombre d’observations, le nombre de variables, les types de variables et la présence éventuelle de doublons ;
3. la distribution de la variable `stroke`, notamment le nombre et la proportion de personnes avec et sans AVC ;
4. les valeurs manquantes ;
5. les valeurs incohérentes, impossibles ou improbables.

**Justification :**  
La qualité des données peut influencer le choix des méthodes statistiques et la validité des résultats. En particulier, une faible proportion d’AVC pourrait entraîner un déséquilibre de la variable dépendante et limiter le nombre de paramètres pouvant être estimés dans le modèle.

**Conséquence pour l’analyse :**  
Les décisions concernant l’exclusion d’observations, le traitement des données manquantes, le regroupement de catégories et la spécification du modèle seront prises après cette évaluation. Chaque modification importante fera l’objet d’une nouvelle entrée dans le journal des décisions.

**Statut :** Adoptée

****

## DEC-004 — 2026-09-21

**Étape :** Planification de l’analyse multivariable

**Décision prévue :**  
Une régression logistique multivariable est envisagée pour étudier les associations entre les facteurs de risque potentiels et la présence d’un AVC.

La variable dépendante sera `stroke`, codée comme une variable binaire. Les résultats seront principalement présentés sous forme d’odds ratios ajustés accompagnés de leurs intervalles de confiance à 95 %.

**Justification :**  
La régression logistique est adaptée à une variable dépendante binaire et permet d’estimer l’association entre chaque variable explicative et l’AVC tout en tenant compte simultanément des autres variables incluses dans le modèle.

**Conséquence pour l’analyse :**  
Le modèle définitif ne sera établi qu’après l’évaluation de la qualité des données. Les variables ne seront pas sélectionnées uniquement en fonction de leur significativité statistique.

**Statut :** Prévue — à confirmer après l’évaluation de la qualité des données

****

## DEC-005 — 2026-09-22

**Étape :** Traitement des valeurs manquantes et extrêmes

**Décision :**
Les NA de bmi sont conservés pour le moment, sans imputation.

Les valeurs extrêmes de bmi seront d’abord conservées. Une analyse de sensibilité sera ensuite réalisée en excluant les valeurs hors des percentiles 2,5–97,5 %.

Les mineurs seront exclus de l’analyse principale.

**Justification :**
Éviter de supprimer ou modifier des données avant d’évaluer leur impact. L’analyse principale sera limitée aux adultes ; la justification de ce choix reste à préciser.

**Statut :** Prévue — à confirmer avant l’analyse multivariable.

****

## DEC-006 — 2026-09-26

**Étape :** Tableau descriptif — comparaison selon l’AVC

**Décision :**
add_p() utilise par défaut le test de Wilcoxon pour les variables continues. Le test t de Student a été choisi à la place, en conservant la présentation en moyenne (ET).

**Justification :**
Compte tenu de la grande taille de l’échantillon, le test t est relativement robuste aux écarts à la normalité. Ce choix est également cohérent avec la présentation des variables continues et leur utilisation dans le modèle de régression.

**Statut :** Retenue

****
## DEC-007 — 2026-09-26

**Étape :** Modèle multivariable — variable work_type

**Décision :**
Les 5 individus de la catégorie Never_worked ont été exclus de l’analyse.

**Justification :**
Cette catégorie ne contient que 5 individus et conduit à une estimation instable (OR = 0,00, IC non estimable). Son effectif est insuffisant pour obtenir une estimation interprétable.

**Conséquence :**
Le modèle principal est ajusté après exclusion de ces 5 observations.

**Statut :** Retenue

****
## DEC-008 — 2026-09-27

**Étape :** Traitement des valeurs manquantes de bmi

**Décision :**
L’imputation multiple initialement envisagée est abandonnée. Les valeurs manquantes de bmi seront remplacées par la médiane.

**Justification :**
L’imputation multiple nécessite des choix méthodologiques et une validation plus avancés. Compte tenu du cadre de ce projet, une méthode plus simple et facilement reproductible a été retenue. L’imputation médiane permet de conserver les observations tout en limitant l’influence des valeurs extrêmes.

**Limite :**
Cette méthode ne tient pas compte de l’incertitude liée aux valeurs imputées et peut réduire artificiellement la variabilité de bmi.

**Statut :** Retenue

****
## DEC-009 — 2026-10-01

**Étape : **Répartition de l’AVC dans le fichier brut

**Décision :**
L’IC à 95 % autour de la prévalence a été supprimé. Seule la proportion d’AVC observée dans l’échantillon est présentée.

**Justification :**
Cette section décrit la composition du fichier et non une estimation de la prévalence dans la population générale. Un IC à 95 % pourrait suggérer une inférence qui n’est pas justifiée par ce jeu de données.

**Statut :** Retenue

****
## DEC-010 — 2026-10-01

**Étape:** Prévalence de l’AVC chez les adultes

**Décision :**
Deux populations sont distinguées pour le calcul de la prévalence :

* brut : tous les individus adultes du fichier initial ;
* donnees_adultes : population analytique finale, après exclusion de gender = "Other" et work_type = "Never_worked".

**Justification :**
Cette distinction permet de séparer la composition du fichier brut de celle de la population effectivement utilisée dans les analyses.

**Statut : ** Retenue

****
## DEC-011 — 2026-10-02

**Étape :** Traitement des valeurs extrêmes de bmi

**Décision :**
L’analyse principale utilisera les valeurs originales de bmi, avec imputation médiane uniquement pour les valeurs manquantes.

La version winsorisée aux percentiles 2,5 % et 97,5 % sera utilisée uniquement en analyse de sensibilité.

**Justification :**
Les valeurs élevées de bmi peuvent correspondre à une obésité réelle et potentiellement associée à l’AVC. Elles ne doivent donc pas être considérées automatiquement comme des valeurs aberrantes.

L’analyse de sensibilité permettra de vérifier si les valeurs extrêmes influencent les résultats.

**Statut :** Retenue — remplace la stratégie précédente utilisant le BMI winsorisé dans l’analyse principale.

****

## DEC-012 — 2026-10-03

**Étape :** Interprétation du DAG

**Décision :**
Le DAG ne sera pas utilisé comme outil d’identification causale. Il sera présenté comme une représentation conceptuelle des relations hypothétiques entre les variables.

**Justification :**
La temporalité des données n’est pas connue : l’AVC correspond à un antécédent, tandis que le BMI, la glycémie, le tabagisme ou l’hypertension peuvent avoir été mesurés après l’AVC. De plus, la proportion d’AVC est élevée par rapport aux données françaises, suggérant une possible sélection de l’échantillon, et les valeurs manquantes de bmi sont fréquentes.

Ces limites ne permettent pas de soutenir une interprétation causale robuste.

**Statut :** Retenue

****

## DEC-013 — 2026-10-04

**Étape :** Vérification de la forme des associations continues

**Décision :**
Une analyse par splines sera ajoutée pour age, bmi et avg_glucose_level, en complément du modèle logistique principal.

**Justification :**
Le modèle principal suppose une relation linéaire entre chaque variable continue et le log-odds d’AVC. Cette hypothèse sera vérifiée en comparant la forme linéaire aux modèles avec splines.

Cette analyse permettra notamment d’identifier d’éventuelles associations non linéaires qui pourraient être masquées par un OR unique.

**Statut :** Prévue

****

## DEC-014 — 2026-10-04

**Étape :** Présentation de avg_glucose_level

**Décision :**
La comparaison entre la glycémie exprimée par 1 mg/dL et par 10 mg/dL est retirée des analyses de sensibilité. La glycémie sera présentée par augmentation de 10 mg/dL dans le modèle principal.

**Justification :**
Le passage de 1 à 10 mg/dL modifie uniquement l’unité de présentation de l’OR, sans modifier le modèle ni les résultats statistiques. Il ne constitue donc pas une analyse de sensibilité.

**Statut :** Retenue

****
