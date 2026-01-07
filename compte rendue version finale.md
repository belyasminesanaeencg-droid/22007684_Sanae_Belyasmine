# 📘 GRAND GUIDE : ANALYSE AVANCÉE D’UN PROJET DATA SCIENCE

**Sanae BELYASMINE – CAC Groupe 1**

## 📱 Cas d’étude : *Prédiction de la santé mentale via l’usage des réseaux sociaux*

---

## 1. 🎯 Contexte métier et cadrage du problème

### 1.1 Problématique réelle

Les réseaux sociaux font partie du quotidien et influencent fortement le bien-être psychologique. Une exposition excessive peut entraîner :

* anxiété et stress,
* troubles du sommeil,
* isolement social,
* baisse de l’activité physique.

Les professionnels de santé (psychologues, médecins, institutions publiques) souhaitent **un outil d’aide à la détection précoce** des situations à risque, basé sur des **indicateurs comportementaux mesurables**.

### 1.2 Objectif data science

Construire un **modèle de Machine Learning supervisé** capable de prédire l’**état mental** d’un individu (`mental_state`) à partir de variables liées à son usage numérique et à son hygiène de vie.

### 1.3 Type de problème

* **Nature** : Classification binaire
* **Entrées (X)** : variables comportementales
* **Sortie (y)** : état mental (ex. sain / en détresse)

### 1.4 Enjeu métier critique

Dans ce contexte :

* **Faux négatif (FN)** → personne en détresse non détectée ❌ (grave)
* **Faux positif (FP)** → alerte inutile ⚠️ (moins grave)

➡️ **La métrique prioritaire est le Recall (sensibilité)**.

---

## 2. 🧪 Données et compréhension du dataset

### 2.1 Description générale

Le dataset regroupe des informations individuelles anonymisées décrivant les comportements numériques et de bien-être.

### 2.2 Variables explicatives

| Variable                      | Description                             |
| ----------------------------- | --------------------------------------- |
| `age`                         | Âge de la personne                      |
| `gender`                      | Genre                                   |
| `platform`                    | Réseau social principal                 |
| `daily_screen_time_min`       | Temps d’écran total quotidien (minutes) |
| `social_media_time_min`       | Temps passé sur les réseaux sociaux     |
| `negative_interactions_count` | Nombre d’interactions négatives         |
| `positive_interactions_count` | Nombre d’interactions positives         |
| `sleep_hours`                 | Heures de sommeil                       |
| `physical_activity_min`       | Activité physique quotidienne           |

### 2.3 Variable cible

* `mental_state` : état mental de l’individu (classe à prédire)

---

## 3. 🧹 Préparation et nettoyage des données

### 3.1 Suppression des colonnes non pertinentes

Certaines variables n’apportent aucune information prédictive :

* `person_name` → identifiant
* `date` → non exploitée temporellement

➡️ Suppression pour éviter le bruit et la fuite d’information.

### 3.2 Encodage des variables catégorielles

Les algorithmes de ML nécessitent des valeurs numériques.

* `gender`, `platform` → **LabelEncoder**

> ⚠️ Limite : LabelEncoder introduit un ordre artificiel. Une amélioration possible est l’utilisation de **OneHotEncoder**.

### 3.3 Vérifications essentielles

* Absence de valeurs manquantes
* Types de données cohérents
* Distribution des variables numériques

---

## 4. 🔎 Analyse Exploratoire des Données (EDA)

### 4.1 Distribution du temps d’écran

* Identification des **utilisateurs intensifs** (> 4h/jour)
* Détection de valeurs extrêmes (outliers)

### 4.2 Analyse de la variable cible

* Vérification de l’équilibre des classes
* Risque de biais si une classe est sous-représentée

### 4.3 Corrélations et relations métiers

Observations attendues :

* 📈 Temps d’écran ↑ → 😴 Sommeil ↓
* 📉 Interactions négatives ↑ → 😟 Bien-être ↓
* 🏃 Activité physique ↑ → 🙂 État mental amélioré

Ces relations justifient la pertinence des variables sélectionnées.

---

## 5. ⚙️ Méthodologie Machine Learning

### 5.1 Séparation Train / Test

```python
train_test_split(test_size=0.2, random_state=42)
```

* **80 %** apprentissage
* **20 %** évaluation finale

### 5.2 Pourquoi cette étape est cruciale ?

* Évaluer la **capacité de généralisation**
* Éviter l’overfitting
* Simuler des données jamais vues

---

## 6. 🤖 Modélisation

### 6.1 Modèles testés

* Logistic Regression
* Decision Tree
* Random Forest

### 6.2 Focus sur Random Forest

**Avantages :**

* Combine plusieurs arbres → meilleure robustesse
* Capture les relations non linéaires
* Moins sensible au bruit

➡️ Excellent compromis performance / interprétabilité.

---

## 7. 📊 Évaluation des performances

### 7.1 Matrice de confusion

|                    | Réel positif | Réel négatif |
| ------------------ | ------------ | ------------ |
| **Prédit positif** | TP           | FP           |
| **Prédit négatif** | FN           | TN           |

### 7.2 Métriques clés

* **Accuracy** : peu pertinente si déséquilibre
* **Precision** : qualité des alertes
* **Recall** : détection des cas à risque ⭐
* **F1-score** : compromis global

➡️ **Recall > Accuracy** dans ce projet.

---

## 8. 🧠 Interprétation experte

* Recall faible → danger réel (personnes ignorées)
* Precision faible → surcharge d’alertes
* F1 élevé → modèle fiable et équilibré

Ce raisonnement montre une **compréhension métier avancée**, au-delà des simples scores.

---

## 9. 🎓 Conclusion générale

Ce projet démontre :

* Une **chaîne Data Science complète**
* Une préparation des données cohérente
* Un choix de métriques aligné avec l’enjeu humain
* Une capacité à relier données ↔ réalité métier

👉 Le Machine Learning peut devenir un **outil d’aide à la décision** pour la prévention en santé mentale.

---

## 10. 🚀 Pistes d’amélioration

* Modèles avancés : XGBoost, LightGBM
* Encodage One-Hot pour `platform`
* Optimisation d’hyperparamètres (GridSearch)
* Gestion des outliers du temps d’écran
* Analyse temporelle si données chronologiques disponibles
* Approche coût-sensible (pondérer les FN)

---

📌 *Ce compte rendu est structuré selon une logique académique et professionnelle, conforme aux attentes d’un projet Data Science universitaire.*
