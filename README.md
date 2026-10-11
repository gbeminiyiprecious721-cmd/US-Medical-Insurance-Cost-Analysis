# US Medical Insurance Cost Analysis

Exploratory analysis and a linear regression model of individual medical insurance charges, built in Python on the US medical insurance dataset (1,338 records).

## Questions

- What drives individual insurance charges?
- How large is the smoking effect compared with age, BMI, family size and region?
- How well can a simple regression model predict charges?

## Data

`insurance.csv`: 1,338 policyholders, 7 columns, no missing values.

| Column | Description |
|---|---|
| age | Age of the policyholder (18 to 64) |
| sex | male or female |
| bmi | Body mass index |
| children | Number of dependent children |
| smoker | yes or no |
| region | northeast, northwest, southeast or southwest |
| charges | Individual medical insurance charges in USD |

## Method

1. Load, inspect and validate the data (types, missing values, summary statistics).
2. Explore charges against age, BMI, smoking status and sex with distributions, scatter plots, box plots and group means.
3. Correlation analysis of the numeric variables.
4. Encode `sex` and `smoker` as binary, one-hot encode `region`, and split 80/20 into train and test sets.
5. Fit a linear regression model and evaluate it on the held-out test set.

## Results

- Mean charges are $13,270 (median $9,382, maximum $63,770).
- Smokers average $32,050 against $8,434 for non-smokers, about 3.8 times higher.
- Average charges are $13,957 for men and $12,570 for women.
- Correlation with charges: age 0.30, BMI 0.20, children 0.07.
- Linear regression on the test set: R² 0.78, MAE $4,181, MSE 33.6 million (RMSE about $5,800).
- Smoking is the dominant coefficient, adding about $23,650 to predicted charges with other factors held constant. Each extra year of age adds about $257, each BMI point about $337 and each child about $425. Regional differences are small by comparison (between -$370 and -$810 relative to the northeast).

## Files

| File | Purpose |
|---|---|
| `us-medical-insurance-costs.ipynb` | Full analysis and model |
| `insurance.csv` | Source data |

## Run it

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
jupyter notebook us-medical-insurance-costs.ipynb
```

## Possible extensions

- Test non-linear models (gradient boosting, random forest) and compare against the linear baseline.
- Test interactions between smoking status and the other features.
- Cross-validate the model rather than relying on a single split.