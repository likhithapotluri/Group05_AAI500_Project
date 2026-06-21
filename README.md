## Predicting and Understanding Factors Affecting Secondary Student Performance 
This project is a part of the AAI-500 course in the Applied Artificial Intelligence Program at the University of San Diego (USD).

## Project Status: Completed

## Installation:

1. git init
2. git clone https://github.com/likhithapotluri/Group05_AAI500_Project

## Overview

This project analyzes the factors that influence secondary student academic performance using statistical inference, machine learning, clustering, Bayesian Networks, and intervention simulation. The analysis focuses on predicting and explaining Grade Point Average (GPA) and academic achievement classes using demographic, behavioral, support, attendance, and extracurricular variables.

The project is implemented in the notebook `AAI_500_Project.ipynb`.

## Partner(s)/Contributor(s):

1. Likhitha Potluri
2. Manish Nair
3. Aditya Singh Panwar

## Research Question

What are the key statistical and interactive factors influencing student GPA, and how can robust predictive models be developed while accounting for uncertainty, demographic variation, and student heterogeneity?

## Objectives

- Investigate relationships between student demographics, study behavior, support systems, and academic performance.
- Identify the strongest predictors of GPA.
- Evaluate interaction effects, including support-related moderation of attendance and study behavior.
- Build predictive models for continuous GPA and categorical GradeClass outcomes.
- Identify student archetypes using clustering.
- Use Bayesian Networks for probabilistic reasoning and intervention-oriented analysis.
- Assess model performance across demographic subgroups.

## Repository Structure

```text
Group05_AAI500_Project/
|-- AAI_500_Project.ipynb   # Main analysis notebook
`-- README.md               # Project documentation
```

## Dataset

The notebook uses a student performance dataset with 2,392 student records and variables related to:

- Demographics: `Age`, `Gender`, `Ethnicity`, `ParentalEducation`
- Academic behavior: `StudyTimeWeekly`, `Absences`, `Tutoring`
- Support and engagement: `ParentalSupport`, `Extracurricular`, `Sports`, `Music`, `Volunteering`
- Outcomes: `GPA`, `GradeClass`

The notebook reads the dataset from:

```python
pd.read_csv("/content/Student Performance Data.csv")
```

When running the notebook, place `Student Performance Data.csv` in the expected working directory or update the file path to match your environment.

## Feature Engineering

The analysis creates additional features to improve interpretation and modeling:

- `Absence_Rate`
- `Support_Index`
- `Activity_Diversity`
- `Inter_Support_x_Absences`
- `Inter_StudyTime_x_Gender`
- `StudyTime_Bin`
- `High_Performer`

## Methods

The notebook includes the following analytical stages:

- Data cleaning and missing-value handling
- Exploratory data analysis
- Distribution checks and correlation analysis
- Hypothesis testing and effect size analysis
- Bootstrap confidence interval estimation
- Multiple linear regression for GPA prediction
- Logistic Regression and Random Forest models for binary high-performer classification
- Multi-class Logistic Regression for GradeClass prediction
- K-Means clustering for student archetype discovery
- Bayesian Network modeling for conditional probability inference
- Fairness evaluation across demographic groups
- Intervention simulation for policy-oriented decision support

## Requirements

The notebook uses Python and the following major libraries:

```text
numpy
pandas
matplotlib
seaborn
scipy
scikit-learn
statsmodels
pgmpy
shap
xgboost
```

The notebook installs additional dependencies with:

```python
!pip -q install pgmpy shap xgboost
```

For a local environment, install the requirements manually:

```bash
pip install numpy pandas matplotlib seaborn scipy scikit-learn statsmodels pgmpy shap xgboost
```

## How to Run

1. Open `AAI_500_Project.ipynb` from the GitHub repository, or download the repository and run the notebook in Jupyter Notebook.
2. Upload `Student Performance Data.csv` or update the dataset path in the notebook.
3. Run the notebook cells sequentially.
4. Review the generated statistical summaries, model metrics, plots, clustering results, Bayesian Network outputs, and intervention simulation table.

## Key Results

| Task | Best Model | Metric 1 | Metric 2 | Metric 3 |
|---|---|---:|---:|---:|
| GPA prediction | OLS Regression | R2 = 0.9285 | RMSE = 0.2432 | MAE = 0.1857 |
| Binary high-performer classification | Logistic Regression | Accuracy = 0.9582 | F1 = 0.8276 | AUROC = 0.9857 |
| Multi-class GradeClass prediction | Multi-class Logistic Regression | Accuracy = 0.7265 | Weighted F1 = 0.7150 | - |

Additional findings:

- Average cross-validation R2 for the regression model was approximately 0.9301.
- Logistic Regression outperformed Random Forest for binary high-performer classification in the reported metrics.
- K-Means clustering selected `k = 2`, revealing two broad student archetypes:
  - Lower GPA, higher absences group
  - Higher GPA, lower absences group
- Bayesian Network inference showed that high absences with no tutoring were associated with a high probability of low GPA.
- Simulated absence reduction produced the largest predicted GPA improvement among the tested interventions.

## Interpretation

The analysis suggests that study time, absences, parental support, and tutoring are important factors associated with student academic performance. Absences showed a strong negative relationship with GPA, while parental support and tutoring showed positive relationships. Interpretable models, especially OLS Regression and Logistic Regression, performed strongly while remaining explainable.

## Intervention Simulation

The notebook compares practical intervention scenarios against the baseline predicted mean GPA:

| Scenario | Predicted Mean GPA | Delta vs Baseline |
|---|---:|---:|
| Baseline | 1.9065 | 0.0000 |
| Absences -20% | 2.1951 | 0.2887 |
| StudyTime +10% | 1.9349 | 0.0284 |
| ParentalSupport +1 | 2.0387 | 0.1322 |

Among the tested scenarios, reducing absences by 20% produced the largest predicted gain in mean GPA.

## Limitations

- The dataset is synthetic.
- Correlation does not imply causation.
- Some real-world educational factors are not represented.
- Results may not generalize to all student populations.
- The dataset file is not included directly in the repository and must be supplied separately when running the notebook.

## Conclusion

This project demonstrates how statistical modeling and machine learning can be combined to understand and predict student performance. The results indicate that attendance, study behavior, parental support, and tutoring are central factors in academic outcomes. The combination of regression, classification, clustering, Bayesian Networks, and intervention simulation provides a useful framework for identifying at-risk students and designing targeted support strategies.
