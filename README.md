## Football Match Outcome Prediction | Machine Learning

**MSc Data Science Dissertation | Manchester Metropolitan University**

**Python | Scikit-learn | Feature Engineering | SelectKBest | PCA | SMOTE | GridSearchCV | ROC-AUC | SHAP**

An end-to-end machine learning research project investigating three-class football match outcome prediction: **Home Win (H), Draw (D) and Away Win (A)**.

The research covers historical football data exploration, feature engineering, comparative model development, hyperparameter optimisation, model evaluation and explainable AI.

**Key research outcome:** Random Forest achieved approximately **66% recorded test accuracy**, with a reported ROC-AUC of **0.82**, subject to the methodological limitations documented below.

**Author:** Chinthaka Gamage  
**Institution:** Manchester Metropolitan University, United Kingdom  
**Research materials dated:** 2023  
**Graduated:** July 2024

> **Project status:** Archived academic research and portfolio documentation. The original dataset is currently unavailable and is not included. Saved results can be inspected, but the complete workflow cannot currently be rerun or independently reproduced from this repository.

## Project overview

This project investigates whether machine learning can predict the outcome of football matches as **Home win (H)**, **Draw (D)** or **Away win (A)**. It combines historical match statistics, football-domain feature engineering, comparative modelling and explainable AI to examine a difficult, inherently uncertain classification problem.

The research was completed as part of an MSc Data Science dissertation at Manchester Metropolitan University. The dissertation focuses on approximately ten seasons of EPL results from 2013 onwards, while the broader data collection described in the research contains **45,952 observations**. These figures refer to different stages of the study and should not be treated as the same modelling sample.

### Headline result

- **Best-performing final model reported in the dissertation:** Random Forest Classifier (RFC)
- **Held-out test accuracy:** approximately **66%**
- **Reported ROC-AUC:** approximately **0.82** (see the dissertation for evaluation details)
- **Prediction classes:** Away win, Draw, Home win
- **Final comparison:** Random Forest, k-Nearest Neighbours, Gradient Boosting, Multi-Layer Perceptron and Voting Ensemble

> **Result clarification:** The dissertation identifies **Random Forest**, not Gradient Boosting, as the final preferred model. Any different figures from intermediate notebook runs should be labelled as experimental results rather than the dissertation's final test outcome.

## Research objective

Develop and critically evaluate an end-to-end machine learning workflow for predicting English Premier League match outcomes (Home Win, Draw or Away Win), with particular emphasis on feature engineering, model comparison, class imbalance, hyperparameter optimisation, generalisation and explainable AI.

## Repository contents

| File | Description |
| --- | --- |
| [Dissertation](docs/epl_results_prediction_dessertation_final.pdf) | Research background, literature review, methodology, experiments, evaluation and conclusions. |
| [Part 1: exploratory analysis — PDF](docs/epl_results_prediction%28part1_eda%29_jupyter_notebook.pdf) | Readable PDF export of the exploratory analysis notebook. |
| [Part 2: modelling — PDF](docs/epl_results_prediction%28part2%29_jupyter_notebook.pdf) | Readable PDF export of the modelling notebook. |
| [Presentation](docs/epl_result_prediction_ppt.pdf) | Slide presentation summarising the research and findings. |
| [Part 1: exploratory analysis — notebook](notebooks/epl_results_prediction%28part1_eda%29_jupyter_notebook.ipynb) | Original Jupyter notebook for data exploration and visual analysis. |
| [Part 2: modelling — notebook](notebooks/epl_results_prediction%28part2%29_jupyter_notebook.ipynb) | Original Jupyter notebook for preprocessing, feature engineering, modelling and evaluation. |

The original notebook was divided into **two parts because of computational demands**. Both parts are available in Jupyter notebook format under `notebooks/`, with PDF copies under `docs/`. The source dataset is currently unavailable. Keep this README at the repository root, alongside the `docs/` and `notebooks/` folders. Links assume the PDF files use `.pdf` and the notebooks use `.ipynb`, with filenames matching those listed above.

## Running the notebooks

```bash
git clone https://github.com/chinthakagama/football-match-outcome-prediction-ml.git
cd football-match-outcome-prediction-ml
python -m venv .venv
```

Activate the environment:

```bash
# Windows PowerShell
.venv\Scripts\Activate.ps1

# macOS / Linux
source .venv/bin/activate
```

Install dependencies and start Jupyter:

```bash
pip install -r requirements.txt
jupyter notebook
```

Open **Part 1** first, followed by **Part 2**. Reproduction may require the original datasets and local path adjustments; the presence of notebooks does not by itself guarantee a fully automated run.

## Dataset and predictive features

The project explores historical football results and related predictors, including:

- Team form and historical performance
- Home-versus-away characteristics
- Goals scored and conceded
- Bookmakers' pre-match betting odds
- Other engineered indicators examined during exploratory analysis

The research describes an initial set of **138 candidate features** and a later selection of approximately **21 influential features**. The modelling subset is smaller than the broader 45,952-observation collection.

**Important:** For genuinely prospective predictions, every input must be available *before kick-off*. Any post-match statistics, future-derived aggregates or 
transformations fitted on the full dataset would cause leakage and should not be used in a production-ready model.

## Data and prediction target

The historical source identified in the dissertation is [Football-Data.co.uk: English football data](https://www.football-data.co.uk/englandm.php). The notebook lists season files from **2013/14 to 2022/23** for the Premier League, Championship, League One, League Two and Conference.

The dissertation reports **45,952 initial observations and 138 columns** in its abstract and data exploration. This is an initial dataset description, not the final modelling sample size; preprocessing and resampling change the number of records. The source chapter contains an inconsistent count of 45,922, which has not been independently resolved because the original files are unavailable.

The target is the full-time result, `FTR`:

| Label | Outcome |
| --- | --- |
| `H` | Home win |
| `D` | Draw |
| `A` | Away win |

The original data includes team identifiers, dates, scores, match statistics and bookmaker odds. The selected modelling features include team identifiers, shots, shots on target, corners, fouls, cards, odds and derived indicators of form and scoring performance.

## Methodology

| Stage | Techniques and purpose |
| --- | --- |
| Data understanding | Data familiarisation, exploratory data analysis, missing-value investigation and distribution checks |
| Preprocessing | Missing-value handling, categorical encoding (including One-Hot Encoding) and feature scaling where applicable |
| Feature engineering | Team-form, goals-related, home/away and odds-based indicators; investigation of Elo ratings and clustering |
| Feature selection | Correlation analysis and `SelectKBest` to identify informative predictors |
| Dimensionality reduction | PCA experiments to investigate feature-space compression |
| Imbalance handling | SMOTE experiments to address uneven representation of Home, Draw and Away outcomes |
| Model development | RFC, k-NN, Gradient Boosting, MLP and Voting Ensemble |
| Optimisation | Hyperparameter search / grid-search experiments and cross-validation |
| Evaluation | Confusion matrix, accuracy, precision, recall, F1-score, ROC-AUC and actual-versus-predicted comparisons |
| Explainability | SHAP-based analysis of feature contributions to predictions |

The dissertation reports a **70% training / 20% validation / 10% test** division. The final test set was used to compare generalisation after model development and tuning.

### Model comparison

| Model | Role in the study |
| --- | --- |
| Random Forest Classifier | **Best overall model reported in the final dissertation** |
| k-Nearest Neighbours | Distance-based benchmark |
| Gradient Boosting Classifier | Boosted-tree alternative |
| Multi-Layer Perceptron | Neural-network alternative |
| Voting Ensemble | Combined predictions from multiple estimators |

Other algorithms, including Logistic Regression and Support Vector Machines, are discussed in the research context. The five models above form the dissertation's final comparison.

## Recorded results
**Evaluation note:** The reported results reflect the original academic experiments. Subsequent review identified potential data leakage involving feature availability, preprocessing and resampling. 
Therefore, the recorded accuracy should be interpreted as an experimental classification result rather than a verified estimate of future pre-match prediction performance.
The following values are the **rounded test accuracies displayed in the saved Part 2 notebook**, in the order of the model evaluation loop. They have not been regenerated.

| Model | Recorded test accuracy |
| --- | ---: |
| Random Forest Classifier | 66% |
| k-Nearest Neighbours | 62% |
| Multilayer Perceptron | 63% |
| Gradient Boosting Classifier | 60% |
| Soft Voting Classifier | 65% |

Random Forest achieved the highest recorded test accuracy in this comparison, consistent with the dissertation abstract. The saved test classification reports cover 3,241 observations drawn from the resampled dataset.

## Evaluation and findings

The dissertation reports **approximately 66% test accuracy** for Random Forest and an **ROC-AUC of approximately 0.82**. Its class-specific Random Forest scores are:

| Actual outcome | Precision | Recall | F1-score |
| --- | ---: | ---: | ---: |
| Away (A) | 0.67 | 0.70 | 0.69 |
| Draw (D) | 0.69 | 0.59 | 0.64 |
| Home (H) | 0.64 | 0.70 | 0.67 |

The comparatively lower **draw recall (0.59)** illustrates why overall accuracy alone is insufficient for this three-class problem. Confusion matrices and per-class metrics provide a more informative assessment.

SHAP analysis was used to interpret the contribution of predictors to the model's outputs. These explanations describe the trained model's behaviour; they do not establish that a feature causes a match outcome.

## Analytical workflow

1. **Data preparation:** combine season CSV files, inspect structure and missing values, and prepare numerical and categorical variables.
2. **Exploratory analysis:** investigate outcome frequencies, team performance, summary statistics and feature correlations.
3. **Feature engineering:** explore team form, winning and losing streaks, scoring indicators and aggregated odds.
4. **Feature preparation:** apply imputation, scaling and categorical encoding; investigate feature selection and PCA.
5. **Class balancing:** use SMOTE to address outcome imbalance.
6. **Model comparison:** train and tune classifiers and a soft voting ensemble.
7. **Evaluation:** inspect accuracy, precision, recall, F1 scores, confusion matrices and cross-validation outputs.
8. **Interpretation:** use feature importance and SHAP visualisations to examine model behaviour.

PCA and clustering appear as exploratory investigations; they should not be interpreted as verified components of every final model. The final comparison in the supplied notebook covers Random Forest, k-Nearest Neighbours, a Multilayer Perceptron, Gradient Boosting and a Voting Classifier. Algorithms discussed in the literature review are not necessarily implemented final models.

**These are historical experimental results, not verified estimates of future-match performance.** Some notebook print statements contain literal formatting placeholders, and some evaluation comments mislabel validation data as test data. The table above follows the actual test evaluation loop and its stored classification reports. Other figures and claims in the academic materials may refer to different experiments or evaluation contexts and should not be combined into a single performance claim.

## Methodological limitations

The archived workflow provides evidence of research and implementation experience, while also identifying concrete areas for improvement:

- **Feature availability:** the selected inputs include same-match shots, shots on target, corners, fouls and cards. These are unavailable before kick-off. Their use prevents the recorded scores from demonstrating pre-match forecasting performance.
- **Resampling before splitting:** SMOTE is applied before the training, validation and test split. Related original and synthetic observations can therefore cross evaluation boundaries, creating leakage risk and potentially optimistic scores.
- **Preprocessing before splitting:** imputation, scaling and encoding are fitted on the combined data before splitting, rather than being learned exclusively from the training partition.
- **Random splitting:** the notebook uses stratified random splits of approximately 70% training, 20% validation and 10% testing. A chronological evaluation is needed to assess generalisation to later matches.
- **Missing source data and environment:** the original CSV files and a pinned dependency specification are not included, so exact reproduction is currently unavailable.

SHAP helps explain model outputs; it does not establish causality, remove leakage or validate the evaluation design. These limitations are documented to distinguish the original academic experiments from a production forecasting system.

## Repository structure

```text
football-match-outcome-prediction-ml/
├── README.md
├── LICENSE
├── .gitignore
├── requirements.txt
├── notebooks/
│   ├── epl_results_prediction(part1_eda)_jupyter_notebook.ipynb
│   └── epl_results_prediction(part2)_jupyter_notebook.ipynb
└── docs/
    ├── epl_results_prediction_dessertation_final.pdf
    ├── epl_results_prediction(part1_eda)_jupyter_notebook.pdf
    ├── epl_results_prediction(part2)_jupyter_notebook.pdf
    └── epl_result_prediction_ppt.pdf
```

## Viewing and reproducibility

Start with the presentation for a brief overview, then read the dissertation for the full research narrative. Use the PDF exports for convenient reading and the two original notebooks to inspect code and saved outputs.

The notebook uses Python with pandas, NumPy, scikit-learn, imbalanced-learn, Matplotlib, Seaborn and SHAP, alongside Jupyter. This list describes the principal tools; it is not a tested environment specification.

The notebook retains original local CSV paths. Installing its libraries alone will not make it runnable. Reproduction requires recovering or reconstructing the source data, checking its schema and season coverage, updating paths, establishing compatible package versions and reviewing the execution order. A newly downloaded dataset should not be assumed identical to the original snapshot.

## Future improvements

- Recover the historical source files and document their provenance, schema and permitted use.
- Define a strict pre-kick-off prediction time and retain only features available at that time.
- Calculate team-history features using earlier matches only.
- Split chronologically before fitting preprocessing or applying resampling.
- Place preprocessing and any resampling inside training and cross-validation pipelines.
- Compare with a majority-class baseline and report per-class results, macro F1 and balanced accuracy on an untouched future-period test set.
- Reconcile inconsistent labels and metrics across the notebook, dissertation and presentation.
- Publish a tested environment specification and a cleaned, reproducible workflow.
- Future predictors: Investigate injuries, line-ups, player ratings, weather and pre-match news where reliable historical coverage is available.

## Skills demonstrated

**Python data analysis · Exploratory data analysis · Data preprocessing · Feature selection and engineering · Multiclass classification · Class-imbalance analysis · Hyperparameter tuning · Model evaluation · Explainable AI · Technical research and documentation**

## Project context and data rights

This work was undertaken as part of the MSc Data Science programme at Manchester Metropolitan University. The original dissertation contains the academic references and acknowledgements. The historical data provider is credited above; no dataset is distributed with this repository, and this README does not grant rights to third-party data or referenced materials. The model is a research demonstration, not a guarantee of football-result prediction or a betting recommendation.

## Licence

The original source code in this repository, including original code cells in the Jupyter notebook, is licensed under the **MIT License**. See [LICENSE](LICENSE) for the full terms.

The MIT License applies to original source code only. It does **not** apply to the dissertation, presentation, PDF exports, written explanations, figures or other non-code materials. Copyright in original non-code materials is retained by the author; no additional reuse permission for those materials is granted by the MIT License.

Third-party data, code, figures, quotations and other referenced materials remain subject to their respective owners' rights and applicable licences. No third-party dataset is included in this repository.
