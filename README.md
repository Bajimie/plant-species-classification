# Plant Species Classification Using Machine Learning

Comparative multi-class classification of plant species using numerical leaf morphology and texture descriptors. This academic project evaluates five supervised learning algorithms in **Python (scikit-learn)** and reports additional experiments performed in **WEKA**.

## Project overview

The research compares **k-nearest neighbours, linear support vector machines, decision trees, random forests and Gaussian Naïve Bayes**. The analysis explores class distributions, feature correlations, class balancing with SMOTE, feature scaling, 80/20 hold-out evaluation, 10-fold cross-validation and Random Forest feature importance.

The supplied cleaned datasets each contain **330 observations, 14 numeric predictors and one species label column**, representing 30 species. The accompanying research report describes experiments on a **340-observation original dataset**; consequently, the reported paper scores should **not** be assumed to reproduce exactly with the provided cleaned files.

## Results reported in the research paper

| Model | Python test accuracy | Python 10-fold CV mean |
| --- | ---: | ---: |
| Random Forest | 88.54% | 86.25% |
| Linear SVM | 82.23% | 85.21% |
| kNN | 79.17% | 80.42% |
| Decision Tree | 79.17% | 77.29% |
| Naïve Bayes | 78.12% | 82.29% |

The paper also reports **86.36% WEKA Random Forest hold-out accuracy** and **86.97% WEKA 10-fold CV accuracy**. These figures are historical results from the submitted research paper, **not newly reproduced benchmarks**.

## Repository structure

```text
plant-species-classification/
├── data/
│   ├── leaf_labelled_V1_cleaned_final.csv
│   └── leaf_labelled_V1_cleaned_final_weka.csv
├── notebooks/
│   └── leaf_classification.ipynb
├── reports/
│   └── research_paper.docx
├── requirements.txt
├── .gitignore
└── README.md
```

## Run locally

From the repository root:

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter lab
```

Open `notebooks/leaf_classification.ipynb`. The notebook reads `data/leaf_labelled_V1_cleaned_final.csv` using a path **relative to the repository root**, so launch Jupyter from the root and configure the notebook's working directory accordingly, or adjust the path if Jupyter runs the notebook from `notebooks/`.

The notebook's SMOTE example writes optional balanced CSV/ARFF files to the current working directory; these generated artifacts are excluded from Git.

## Important notes

- **Reproducibility:** The original 340-row dataset referenced by the paper was not included in the provided materials. The 330-row cleaned datasets may produce different results.
- **Evaluation:** The notebook performs its main model comparison on the original cleaned data. The separate SMOTE demonstration does **not** feed into the main model comparison; do not interpret the reported model scores as scores from a SMOTE-balanced training pipeline.
- **Methodology:** If extending this work, perform SMOTE **only on training folds**, inside a suitable imbalanced-learn pipeline, to prevent data leakage.
- **WEKA:** The WEKA experiments are documented in the research paper; a separate WEKA workflow/configuration file was not supplied.
- **Scope:** This is tabular leaf-feature classification, not an image-upload identification application.

## Author

**Emmanuel Bajimi** — MSc Data Science, Ulster University.  
GitHub: [@Bajimie](https://github.com/Bajimie)
