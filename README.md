# Prédiction de survie des passagers du Titanic

Ce dossier contient [`predictSurvie.ipynb`](./predictSurvie.ipynb), un notebook pédagogique qui entraîne un modèle de classification pour estimer si un passager du Titanic a survécu.

## Données utilisées

Le notebook lit le fichier `../titanic.csv` : placez-vous donc dans le dossier `predictionSurvie` au moment de l’exécuter. Le fichier CSV doit notamment contenir les colonnes `Survived`, `Pclass`, `Sex` et `Age`.

- `Survived` est la valeur à prédire : `0` signifie « n’a pas survécu » et `1` « a survécu ».
- `Pclass` est la classe du billet (1, 2 ou 3).
- `Sex` est converti en valeur numérique : `0` pour `female`, `1` pour `male`.
- `Age` est l’âge du passager.

Les lignes sans valeur pour ces colonnes sont supprimées avant l’entraînement.

## Installation

Avec Python et `pip`, installez les bibliothèques nécessaires :

```bash
python -m pip install numpy pandas matplotlib scikit-learn jupyter
```

`matplotlib` est importé dans le notebook, même si aucune visualisation n’est utilisée dans les cellules actuelles.

## Exécuter le notebook

Depuis la racine du projet :

```bash
cd predictionSurvie
jupyter notebook predictSurvie.ipynb
```

Dans VS Code, ouvrez le notebook, choisissez un kernel Python où les dépendances sont installées, puis exécutez les cellules dans l’ordre avec **Exécuter tout**. Le dossier courant d’exécution doit être `predictionSurvie` pour que le chemin `../titanic.csv` mène au bon fichier.

Les cellules chargent et inspectent les données, sélectionnent les colonnes utiles, puis entraînent un classifieur `KNeighborsClassifier` avec `n_neighbors=5`. La cellule `model.score(X, y)` affiche son exactitude sur les mêmes données que celles ayant servi à l’entraînement : ce résultat donne une première indication, mais ne mesure pas à lui seul la capacité du modèle à généraliser à de nouveaux passagers.

## Faire une prédiction

La fonction `survie` prend un modèle entraîné et les caractéristiques d’un passager. Exemple :

```python
survie(model, Pclass=3, Sex=1, Age=19)
```

La fonction affiche la classe prédite (`0` ou `1`), puis les probabilités associées à chaque classe. Pour `Sex`, utilisez `0` pour `female` et `1` pour `male`; pour `Pclass`, utilisez `1`, `2` ou `3`. Il faut d’abord avoir exécuté les cellules d’entraînement afin que la variable `model` soit disponible.
