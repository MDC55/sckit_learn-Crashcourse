# sckit_learn-Crashcourse


Notebook: `1. scikit_learn_basic.ipynb` — a short scikit-learn demo using the (deprecated) Boston housing dataset.

## Summary
- Demonstrates dataset inspection, LinearRegression, KNeighborsRegressor, Pipeline with StandardScaler, and GridSearchCV.
- Key notebook patterns:
  - Pipeline steps named `"scale"` and `"model"`.
  - GridSearchCV param grid uses nested names (example: `'model__n_neighbors'`).
  - Cells reuse globals (`X`, `y`, `model`, `pipeline_mod`) — consider refactoring to scripts for reproducibility.

## Requirements (tested)
- Python 3.8+
- scikit-learn==1.1.3
- pandas
- matplotlib
- jupyter

Install:
```bash
python -m venv .venv
.venv\Scripts\activate
pip install scikit-learn==1.1.3 pandas matplotlib jupyter
```

## Run
- Open in VS Code or:
```bash
jupyter notebook "1. scikit_learn_basic.ipynb"
```
- To convert to a script for CI or quick runs:
```bash
jupyter nbconvert --to script "1. scikit_learn_basic.ipynb"
python scripts/<converted_file>.py
```

## Important note: `load_boston` is deprecated
The notebook currently uses:
```python
from sklearn.datasets import load_boston
X, y = load_boston(return_X_y=True)
```
Options:
- Pin scikit-learn to 1.1.x (recommended for reproducibility).
- Replace with `fetch_california_housing`:
```python
from sklearn.datasets import fetch_california_housing
X, y = fetch_california_housing(return_X_y=True)
```
- Or fetch via OpenML:
```python
from sklearn.datasets import fetch_openml
boston = fetch_openml(name="boston", as_frame=False)
X, y = boston.data, boston.target
```

## Contributing / Commits
- Keep notebook edits minimal and add a markdown cell describing changes (e.g., dataset migration).
- Example commit message: `fix: replace load_boston with fetch_california_housing` or `chore: add README and .gitignore`.

## References
- Notebook reference link included at end of notebook: https://towardsdatascience.com/linear-regression-on-boston-housing-dataset-f409b7e4a155
