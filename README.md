# Football Match Outcome Classification Using Machine Learning

An MSc Data Science research project exploring the classification of football matches as **home wins, draws or away wins**, using historical English football data, feature engineering and comparative machine learning.

**Author:** Chinthaka Gamage  
**Institution:** Manchester Metropolitan University, United Kingdom  
**Research materials dated:** 2023  
**Graduated:** July 2024

> **Project status:** Archived academic research and portfolio documentation. The original dataset is currently unavailable and is not included. Saved results can be inspected, but the complete workflow cannot currently be rerun or independently reproduced from this repository.

## Project overview

The project investigated how data preparation, feature engineering, class balancing and model selection affect the classification of football match outcomes. Particular attention was given to distinguishing draws from home and away wins and interpreting the contribution of individual features.

Although the original filenames refer to EPL prediction, the source files cover **multiple English football divisions**, rather than the Premier League alone. The study is presented here as historical match outcome classification; the original workflow does not establish reliable prediction of unseen matches before kick-off.

## Repository contents

| File | Description |
| --- | --- |
| [Dissertation](epl_results_prediction_dessertation_final.pdf) | Research background, literature review, methodology, experiments, evaluation and conclusions. |
| [Part 1: exploratory analysis](epl_results_prediction%28part1_eda%29_jupyter_notebook.pdf) | PDF export of the first notebook, covering data exploration and visual analysis. |
| [Part 2: modelling notebook](epl_results_prediction%28part2%29_jupyter_notebook.ipynb) | Original Jupyter notebook containing preprocessing, feature engineering, modelling and saved outputs. |
| [Presentation](epl_result_prediction_ppt.pdf) | Slide presentation summarising the research and findings. |

The original notebook was divided into **two parts because of computational demands**. Part 1 is supplied as a PDF export; Part 2 is supplied as an executable notebook format, although its source data is missing. Filenames are retained to match the original materials. The links above assume all four files are uploaded beside this README at the repository root.

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

## Recorded results

The following values are the **rounded test accuracies displayed in the saved Part 2 notebook**, in the order of the model evaluation loop. They have not been regenerated.

| Model | Recorded test accuracy |
| --- | ---: |
| Random Forest Classifier | 66% |
| k-Nearest Neighbours | 62% |
| Multilayer Perceptron | 63% |
| Gradient Boosting Classifier | 60% |
| Soft Voting Classifier | 65% |

Random Forest achieved the highest recorded test accuracy in this comparison, consistent with the dissertation abstract. The saved test classification reports cover 3,241 observations drawn from the resampled dataset.

**These are historical experimental results, not verified estimates of future-match performance.** Some notebook print statements contain literal formatting placeholders, and some evaluation comments mislabel validation data as test data. The table above follows the actual test evaluation loop and its stored classification reports. Other figures and claims in the academic materials may refer to different experiments or evaluation contexts and should not be combined into a single performance claim.

## Methodological limitations

The archived workflow provides evidence of research and implementation experience, while also identifying concrete areas for improvement:

- **Feature availability:** the selected inputs include same-match shots, shots on target, corners, fouls and cards. These are unavailable before kick-off. Their use prevents the recorded scores from demonstrating pre-match forecasting performance.
- **Resampling before splitting:** SMOTE is applied before the training, validation and test split. Related original and synthetic observations can therefore cross evaluation boundaries, creating leakage risk and potentially optimistic scores.
- **Preprocessing before splitting:** imputation, scaling and encoding are fitted on the combined data before splitting, rather than being learned exclusively from the training partition.
- **Random splitting:** the notebook uses stratified random splits of approximately 70% training, 20% validation and 10% testing. A chronological evaluation is needed to assess generalisation to later matches.
- **Missing source data and environment:** the original CSV files and a pinned dependency specification are not included, so exact reproduction is currently unavailable.

SHAP helps explain model outputs; it does not establish causality, remove leakage or validate the evaluation design. These limitations are documented to distinguish the original academic experiments from a production forecasting system.

## Viewing and reproducibility

Start with the presentation for a brief overview, then read the dissertation for the full research narrative. Use the Part 1 PDF to inspect exploratory work and the Part 2 notebook to inspect implementation and saved outputs.

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

## Skills demonstrated

Python data analysis, exploratory visualisation, missing-value handling, categorical encoding, feature engineering, model comparison, hyperparameter tuning, classification evaluation, model interpretation and technical research communication.

## Acknowledgements and data rights

This work was undertaken as part of the MSc Data Science programme at Manchester Metropolitan University. The original dissertation contains the academic references and acknowledgements. The historical data provider is credited above; no dataset is distributed with this repository, and this README does not grant rights to third-party data or referenced materials.

## Licence

The original source code in this repository, including original code cells in the Jupyter notebook, is licensed under the **MIT License**. See [LICENSE](LICENSE) for the full terms.

The MIT License applies to original source code only. It does **not** apply to the dissertation, presentation, PDF exports, written explanations, figures or other non-code materials. Copyright in original non-code materials is retained by the author; no additional reuse permission for those materials is granted by the MIT License.

Third-party data, code, figures, quotations and other referenced materials remain subject to their respective owners' rights and applicable licences. No third-party dataset is included in this repository.
