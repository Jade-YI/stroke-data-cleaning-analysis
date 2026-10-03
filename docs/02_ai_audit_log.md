# Journal d’audit de l’utilisation de l’IA

Ce document recense les principales utilisations de l’IA dans le projet. L’IA sert d’aide à l’organisation, à la rédaction, au code et à la méthode. Les hypothèses, les choix analytiques et l’interprétation finale restent sous la responsabilité de l’autrice.

---

## AI-001 · 2026-09-19 · Organisation / rédaction

* **Source :** ChatGPT — organisation du projet et rédaction du `README.md`.
* **Demande :** Créer une structure de dossiers et de fichiers adaptée au projet, puis rédiger le `README.md`.
* **Réponse :** Proposition d’une arborescence séparant données, code, figures et documentation.
* **Vérification :** Contrôle des fichiers, des chemins et de leur cohérence dans le dépôt local et sur GitHub.
* **Constat :** ✅ Structure globalement adaptée, avec quelques ajustements.
* **Impact :** Léger, limité à l’organisation du projet.
* **Décision :** Structure générale conservée et adaptée aux besoins réels.
* **Preuve :** Arborescence du dépôt, `README.md` et historique Git.
* **Leçon :** Une structure proposée par l’IA doit être adaptée au projet réel.

---

## AI-002 · 2026-09-20 · Méthode / interprétation / rédaction

* **Source :** ChatGPT — vérification méthodologique des hypothèses.
* **Demande :** Vérifier la formulation de mes hypothèses et les reformuler en français sans en modifier le contenu.
* **Réponse :** Prudence recommandée pour `smoking_status = "Unknown"`. L’IA a aussi proposé que le tabagisme puisse être un médiateur entre le genre et l’AVC plutôt qu’un facteur de confusion.
* **Vérification :** Comparaison avec la définition des variables et les notions de confusion et de médiation vues en cours.
* **Constat :** ⚠️ La remarque sur `"Unknown"` est pertinente. Le rôle du tabagisme dépend toutefois du modèle causal retenu.
* **Impact :** Léger à modéré sur la formulation, sans effet sur l’origine des hypothèses.
* **Décision :** Prudence conservée pour `"Unknown"`. Le rôle du tabagisme reste à vérifier. Les hypothèses et les qualificatifs « forte », « modérée » ou « faible » restent les miens.
* **Preuve :** Document des hypothèses et décisions `DEC-001` et `DEC-002`.
* **Leçon :** Une suggestion causale de l’IA doit être vérifiée avant d’être retenue.

---

## AI-003 · 2026-09-22 · Code / visualisation

* **Source :** Claude — code décrivant la proportion d’AVC dans la population.
* **Demande :** Calculer la répartition des individus avec ou sans AVC et la représenter graphiquement.
* **Réponse :** Diagramme en barres avec les effectifs sur l’axe des y.
* **Vérification :** Comparaison du graphique avec l’objectif, qui était de montrer la proportion d’AVC dans la population.
* **Constat :** ⚠️ Le graphique était correct, mais les effectifs répondaient moins bien à cet objectif.
* **Impact :** Léger, limité à la présentation.
* **Décision :** Remplacement des effectifs par des proportions, avec un axe des y allant de 0 à 1.
* **Preuve :** Code et graphique dans le document Quarto.
* **Leçon :** Un graphique correct doit aussi être adapté au message présenté.

---
 
## AI-004 · 2026-09-22 · Type : code / présentation

* **Source :** GPT — analyse des valeurs manquantes.
* **Ce que j’ai demandé / l’IA a fait :** Générer le code pour résumer les valeurs manquantes.
* **Réponse de l’IA :** Résultat présenté horizontalement (`gender | age | hypertension | bmi | ...`), avec une lisibilité limitée.
* **Vérification / constat :** ✅ Les résultats étaient exploitables, mais le format peu lisible.
* **Impact :** Aucun sur les résultats ; uniquement sur la présentation.
* **Traitement final :** J’ai ajouté `pivot_longer()` pour obtenir un format long plus lisible.
* **Preuve :** `docs/stroke_multivariable_analysis.qmd`
* **Leçon :** Vérifier aussi la lisibilité des sorties générées par l’IA.

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

##AI-007 · 2026-10-03 · Code / présentation

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


