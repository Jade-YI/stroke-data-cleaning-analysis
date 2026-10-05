---
title: "Journal de revue de l'utilisation de l'IA"
---
# Journal d’audit de l’utilisation de l’IA

Ce document recense les principales utilisations de l’IA dans le projet. L’IA sert d’aide à l’organisation, à la rédaction, au code et à la méthode. Les hypothèses, les choix analytiques et l’interprétation finale restent sous la responsabilité de l’autrice.

---

## AI-001 · 2026-09-19 · Organisation / rédaction

**Source :** ChatGPT — organisation du projet et rédaction du `README.md`.
**Demande :** Créer une structure de dossiers et de fichiers adaptée au projet, puis rédiger le `README.md`.
**Réponse :** Proposition d’une arborescence séparant données, code, figures et documentation.
**Vérification :** Contrôle des fichiers, des chemins et de leur cohérence dans le dépôt local et sur GitHub.
**Constat :** ✅ Structure globalement adaptée, avec quelques ajustements.
**Impact :** Léger, limité à l’organisation du projet.
**Décision :** Structure générale conservée et adaptée aux besoins réels.
**Preuve :** Arborescence du dépôt, `README.md` et historique Git.
**Leçon :** Une structure proposée par l’IA doit être adaptée au projet réel.

---

## AI-002 · 2026-09-20 · Méthode / interprétation / rédaction

**Source :** ChatGPT — vérification méthodologique des hypothèses.
**Demande :** Vérifier la formulation de mes hypothèses et les reformuler en français sans en modifier le contenu.
**Réponse :** Prudence recommandée pour `smoking_status = "Unknown"`. L’IA a aussi proposé que le tabagisme puisse être un médiateur entre le genre et l’AVC plutôt qu’un facteur de confusion.
**Vérification :** Comparaison avec la définition des variables et les notions de confusion et de médiation vues en cours.
**Constat :** ⚠️ La remarque sur `"Unknown"` est pertinente. Le rôle du tabagisme dépend toutefois du modèle causal retenu.
**Impact :** Léger à modéré sur la formulation, sans effet sur l’origine des hypothèses.
**Décision :** Prudence conservée pour `"Unknown"`. Le rôle du tabagisme reste à vérifier. Les hypothèses et les qualificatifs « forte », « modérée » ou « faible » restent les miens.
**Preuve :** Document des hypothèses et décisions `DEC-001` et `DEC-002`.
**Leçon :** Une suggestion causale de l’IA doit être vérifiée avant d’être retenue.

---

## AI-003 · 2026-09-22 · Code / visualisation

**Source :** Claude — code décrivant la proportion d’AVC dans la population.
**Demande :** Calculer la répartition des individus avec ou sans AVC et la représenter graphiquement.
**Réponse :** Diagramme en barres avec les effectifs sur l’axe des y.
**Vérification :** Comparaison du graphique avec l’objectif, qui était de montrer la proportion d’AVC dans la population.
**Constat :** ⚠️ Le graphique était correct, mais les effectifs répondaient moins bien à cet objectif.
**Impact :** Léger, limité à la présentation.
**Décision :** Remplacement des effectifs par des proportions, avec un axe des y allant de 0 à 1.
* **Preuve :** Code et graphique dans le document Quarto.
* **Leçon :** Un graphique correct doit aussi être adapté au message présenté.

---
 
## AI-004 · 2026-09-22 · Type : code / présentation

**Source :** GPT — analyse des valeurs manquantes.
**Ce que j’ai demandé / l’IA a fait :** Générer le code pour résumer les valeurs manquantes.
**Réponse de l’IA :** Résultat présenté horizontalement (`gender | age | hypertension | bmi | ...`), avec une lisibilité limitée.
**Vérification / constat :** ✅ Les résultats étaient exploitables, mais le format peu lisible.
**Impact :** Aucun sur les résultats ; uniquement sur la présentation.
**Traitement final :** J’ai ajouté `pivot_longer()` pour obtenir un format long plus lisible.
**Preuve :** `docs/stroke_multivariable_analysis.qmd`
**Leçon :** Vérifier aussi la lisibilité des sorties générées par l’IA.

---

## AI-005 · 2026-09-26 · Code / visualisation

**Source :** GPT — génération du DAG.
**Demande :** Générer le code pour représenter le DAG des hypothèses.
**Réponse :** Utilisation de ggdag() avec text = FALSE.
**Vérification :** Le graphique affichait de gros points noirs qui masquaient les variables. Après vérification, text = FALSE ne supprime pas les nœuds dessinés par défaut avec geom_dag_point().
**Constat :** ⚠️ Le code fonctionnait, mais la visualisation était incorrecte.
**Impact :** Aucun sur l’analyse ; uniquement sur la présentation.
**Décision :** Remplacement de ggdag() par ggplot() + geom_dag_edges() + geom_dag_label_repel() afin de conserver uniquement les étiquettes et les flèches.
**Preuve :** docs/stroke_multivariable_analysis.qmd
**Leçon :** Vérifier les couches graphiques ajoutées par défaut par les fonctions utilisées.

---

## AI-006 · 2026-09-27 · Code / exploration des données

**Source :** GPT — vérification des valeurs incohérentes ou improbables.
**Demande :** Générer un code pour examiner les valeurs potentiellement incohérentes.
**Réponse :** Vérification basée uniquement sur le minimum et le maximum.
**Vérification :** Le minimum et le maximum ne permettent pas d’évaluer la distribution globale des variables.
**Constat :** ⚠️ Analyse correcte mais incomplète.
**Impact :** Léger, sur l’exploration des données.
**Décision :** Ajout de la médiane et des quartiles pour mieux décrire la distribution.
**Preuve :** docs/stroke_multivariable_analysis.qmd
**Leçon :** Les valeurs extrêmes seules ne suffisent pas pour décrire une distribution.

---

## AI-007 · 2026-10-03 · Code / présentation

**Source :** Claude — tableau de la population analytique.
**Demande :** Générer le code résumant les étapes de sélection de la population analytique.
**Réponse :** Tableau avec une seule colonne "Nombre exclus / retenu" regroupant les effectifs exclus et l’effectif final.
**Vérification :** Le code était correct, mais cette colonne mélangeait deux informations différentes et rendait la lecture ambiguë.
**Constat :** ⚠️ Résultat correct mais présentation peu claire.
**Impact :** Aucun sur l’analyse ; uniquement sur la présentation.
**Décision :** Séparation en deux colonnes, "Nombre exclu" et "Effectif restant", avec ajout de l’effectif initial pour rendre les étapes de sélection plus lisibles.
**Preuve :** docs/stroke_multivariable_analysis.qmd
**Leçon :** Vérifier que la structure d’un tableau distingue clairement les informations présentées.

---

## AI-008 · 2026-10-03 · Code / présentation

**Source :** Claude — génération du code pour les graphiques descriptifs.
**Demande :** Générer le code des graphiques pour l’analyse descriptive.
**Réponse :** Les modalités des variables catégorielles ont été reprises directement depuis le jeu de données.
**Vérification :** Lors de la relecture, j’ai constaté que certains libellés restaient en anglais alors que le document est rédigé en français.
**Constat :** ⚠️ Résultats corrects, mais présentation linguistique incohérente.
**Impact :** Aucun sur les résultats ; uniquement sur la présentation.
**Décision :** Traduction des modalités affichées dans les graphiques afin d’harmoniser la langue du document.
**Preuve :** docs/stroke_multivariable_analysis.qmd
**Leçon :** Vérifier les libellés générés automatiquement à partir des données.

---

## AI-009 · 2026-10-03 · Code / présentation

**Source :** Claude — génération du Tableau 1.
**Demande :** Générer le code du tableau descriptif selon le statut d’AVC.
**Réponse :** Les deux modalités "Oui" et "Non" étaient affichées pour les variables binaires comme l’hypertension et la maladie cardiaque.
**Vérification :** Pour ces variables binaires, afficher les deux modalités était redondant et alourdissait le tableau.
**Constat :** ⚠️ Résultats corrects, mais présentation trop détaillée.
**Impact :** Aucun sur les résultats ; uniquement sur la présentation.
**Décision :** Affichage uniquement de la modalité "Oui" avec value = list(hypertension ~ "Oui", heart_disease ~ "Oui").
**Preuve :** docs/stroke_multivariable_analysis.qmd
**Leçon :** Pour une variable binaire, une seule modalité peut suffire lorsque l’autre est directement déductible.

---

## AI-010 · 2026-10-03 · Méthode / interprétation

**Source :** Claude — interprétation du modèle de régression logistique.
**Demande :** Vérifier l’interprétation des résultats du modèle glm.
**Réponse :** Pour avg_glucose_level, l’OR était calculé pour une augmentation de 1 mg/dL (OR = 1,00 ; IC 95 % 1,00–1,01 ; p < 0,001), une unité trop faible pour rendre l’association facilement interprétable.
**Vérification :** Une variation de 1 mg/dL est cliniquement faible et conduit à un OR arrondi très proche de 1, malgré une association statistiquement significative.
**Constat :** ⚠️ Le modèle était correct, mais l’échelle utilisée limitait fortement l’interprétation du résultat.
**Impact :** Modéré. L’échelle initiale rendait le résultat du Tableau 2 peu informatif et affectait son interprétation dans la suite de l’analyse.
**Décision :** Recalcul de l’OR pour une augmentation de 10 mg/dL afin d’obtenir une mesure plus interprétable, sans modifier le modèle sous-jacent.
**Preuve :** docs/stroke_multivariable_analysis.qmd
**Leçon :** L’unité d’une variable continue doit être choisie de façon à produire une mesure d’association interprétable.
---
