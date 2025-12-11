# 📘 GRAND GUIDE : ANALYSE D'UN PROJET DATA SCIENCE
![photo sanae belyasmine.jpeg](https://github.com/belyasminesanaeencg-droid/22007684_Sanae_Belyasmine/blob/5127ea756f97a1f741ed3d6892565b1c3810dc89/photo%20sanae%20belyasmine.jpeg)
## 📱 *Cas d'étude : Prédiction de la santé mentale via l'usage des réseaux sociaux*

------------------------------------------------------------------------

## 1. 🎯 Contexte Métier et Objectif

### Le problème

Les réseaux sociaux influencent fortement la santé mentale : anxiété,
isolement, surcharge numérique.\
Les psychologues veulent un outil permettant de détecter des signaux
d'alerte à partir de comportements mesurables.

### Objectif du projet

Construire un modèle de Machine Learning capable de prédire l'état
mental d'une personne à partir de :

-   Temps d'écran total\
-   Temps passé sur les réseaux sociaux\
-   Interactions négatives\
-   Interactions positives\
-   Heures de sommeil\
-   Activité physique

### Enjeu critique

Un **faux négatif** (dire qu'une personne va bien alors qu'elle est en
détresse) est beaucoup plus grave qu'un faux positif.

➡️ **Il faut donc maximiser le Recall (sensibilité).**

------------------------------------------------------------------------

## 2. 🧪 Données et Préparation

### Description du dataset

Le dataset contient des informations comportementales :

-   `age`
-   `gender`
-   `platform`
-   `daily_screen_time_min`
-   `social_media_time_min`
-   `negative_interactions_count`
-   `positive_interactions_count`
-   `sleep_hours`
-   `physical_activity_min`
-   `mental_state` (variable cible)

### Nettoyage

-   Suppression des colonnes inutiles : `person_name`, `date`
-   Encodage des variables catégorielles via `LabelEncoder()`

------------------------------------------------------------------------

## 3. 🔎 Analyse Exploratoire (EDA)

### Distribution du temps d'écran

Permet d'identifier les gros utilisateurs (\> 4h/jour).

### Répartition de la variable cible

À vérifier : si une classe est sous-représentée → risque de biais.

### Relations possibles

-   Temps d'écran ↑ → sommeil ↓\
-   Interactions négatives ↑ → état mental ↓\
-   Activité physique ↑ → bien-être ↑

------------------------------------------------------------------------

## 4. ⚙️ Méthodologie

### Train/Test Split

On utilise `train_test_split(test_size=0.2)`.

-   80% : apprentissage\
-   20% : évaluation finale

### Pourquoi cette séparation ?

Assurer la **généralisation**, éviter l'overfitting et garantir une
évaluation honnête.

------------------------------------------------------------------------

## 5. 🤖 Modélisation

Le modèle utilisé dans ton notebook peut être :

-   **Decision Tree**
-   **Random Forest**
-   **Logistic Regression**

### Pourquoi Random Forest serait un bon choix ?

-   Gère bien les interactions complexes\
-   Robuste au bruit\
-   Très performant sans tuning poussé

------------------------------------------------------------------------

## 6. 📊 Évaluation et Métriques

### Matrice de confusion

-   **TP :** prédits en détresse + réellement en détresse\
-   **TN :** prédits bien + réellement bien\
-   **FP :** fausse alerte\
-   **FN :** cas non détecté (le plus grave)

### Métriques clés

-   **Accuracy** : trompeur si dataset déséquilibré\
-   **Precision** : fiabilité des alertes\
-   **Recall** : capacité à détecter les cas critiques\
-   **F1-score** : compromis équilibré

➡️ **Dans ton contexte, Recall \> Accuracy**

------------------------------------------------------------------------

## 7. 🧠 Interprétation des résultats comme un expert

-   Un Recall faible = l'IA manque des personnes en détresse →
    dangereux\
-   Un Precision faible = trop de fausses alertes, moins grave\
-   Un F1-score élevé = modèle bien équilibré

------------------------------------------------------------------------

## 8. 🎓 Conclusion

Le projet montre : - Une chaîne Data Science complète\
- Une préparation correcte des données\
- L'importance des métriques adaptées au domaine\
- Une bonne compréhension du comportement numérique et de ses effets

L'approche Machine Learning peut réellement aider à détecter les signaux
d'alerte de manière automatique.

------------------------------------------------------------------------

## 9. 🚀 Améliorations possibles

-   Ajouter un modèle plus puissant (XGBoost, LightGBM)\
-   Utiliser un encodage plus riche (OneHotEncoder pour platform)\
-   Faire une optimisation d'hyperparamètres\
-   Ajouter des analyses temporelles (si dates disponibles)\
-   Gérer les outliers du temps d'écran

------------------------------------------------------------------------
