# Predicting Dota 2 Match Outcomes Using Machine Learning

## Project Overview

This project investigates whether machine learning can predict the outcome of a Dota 2 match using hero composition and early-game team performance. I compare three Logistic Regression models to evaluate how well these features predict match outcomes.

## Research Question

**Can machine learning models predict the outcome of a Dota 2 match using hero composition and early-game team performance?**

## Dataset

The dataset was obtained from Kaggle's **Dota 2: Predicting Match Outcome** competition.

- **Source:** [Kaggle — Dota 2: Predicting Match Outcome](https://www.kaggle.com/competitions/dota-2-prediction/data)
- **Target variable:** `radiant_win`, indicating whether the Radiant team won the match.
Train.csv file is too big and can't be uploaded due to Github file upload limitations. Train.csv file can be downloaded from the provided link.

## Methodology

### Feature Engineering

The project uses two groups of features:

- **Hero composition:** The five heroes selected by Radiant and the five heroes selected by Dire.
- **Early-game team performance:** Gold, experience (XP), last hits (LH), and kills, including differences between the two teams.

### Models

Three Logistic Regression models were developed:

1. **Early-game performance model:** Uses early-game team performance features.
2. **Hero composition model:** Uses the heroes selected by both teams.
3. **Combined model:** Uses both hero composition and early-game performance features.

Preprocessing is incorporated into the modeling pipelines. Hero-selection features are one-hot encoded, while numerical performance features are imputed where necessary and standardized.

### Evaluation

The models were evaluated using **five-fold stratified cross-validation**. This approach preserves approximately the same distribution of Radiant wins and losses in each fold and provides an estimate of model performance across multiple validation splits.

Accuracy was selected as the primary evaluation metric because the target variable is relatively balanced, with approximately 52% Radiant wins and 48% Radiant losses.

The majority-class baseline was **51.76%**, representing the accuracy achieved by always predicting the most frequent outcome.

## Results

| Model | Mean Accuracy | Improvement Over Baseline |
|---|---:|---:|
| Majority-class baseline | 51.76% | — |
| Early-game performance | 60.93% | +9.17 percentage points |
| Hero composition | 59.62% | +7.86 percentage points |
| Combined model | 65.22% | +13.46 percentage points |

## Conclusion

This project investigated whether machine learning models can predict Dota 2 match outcomes using hero composition and early-game team performance. I compared three Logistic Regression models using five-fold cross-validation: a model based on early-game performance, a model based on hero composition, and a combined model using both early-game performance and hero composition.

The early-game performance model achieved a mean accuracy of 60.93%, while the hero composition model achieved 59.62%. The combined model performed best, reaching a mean accuracy of 65.22%. Compared with the majority-class baseline of 51.76%, the combined model improved accuracy by 13.46 percentage points.

These results suggest that combining hero selections with early-game performance provides more predictive information than using either feature group independently. Early-game gold, experience, last-hit, and kill differences provide useful information about match outcomes, while hero composition contributes additional predictive value.

## How to Run the Project

1. Download the dataset from the [Kaggle competition page](https://www.kaggle.com/competitions/dota-2-prediction/data).
2. Place the dataset files in the location expected by the notebook.
3. Open the Jupyter Notebook in an environment with Python and the required libraries installed.
4. Run the notebook cells in order, from data loading through model evaluation.

**Main libraries:** pandas, NumPy, and scikit-learn. Matplotlib and Seaborn may also be used for visualizations.

## Limitations and Future Work

- Accuracy does not capture every type of classification error. Future work could evaluate precision, recall, F1-score.
- The results depend on the selected dataset, features, preprocessing, and validation strategy.
- Predictive relationships do not prove that a particular hero or statistic causes a team to win.

Future work could compare Logistic Regression with other classification algorithms and investigate feature importance.

## Acknowledgment

The dataset was obtained from Kaggle's [Dota 2: Predicting Match Outcome](https://www.kaggle.com/competitions/dota-2-prediction/data) competition.
