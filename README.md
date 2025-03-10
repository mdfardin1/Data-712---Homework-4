# Data-712---Homework-4
# NHANES Logistic Regression Analysis

## **Project Overview**
This project performs a **logistic regression analysis** to predict whether an individual has ever consumed alcohol, based on demographic and income variables from the **National Health and Nutrition Examination Survey (NHANES)** dataset. The analysis evaluates **how gender, age, and income levels** impact alcohol consumption trends using **logistic regression models with increasing complexity**.

## **Dataset Sources**
The datasets used in this analysis are from the **NHANES (August 2021 - August 2023) survey cycle** and include:
- **Income Data (`INQ_L.xlsx`)** – Contains financial data, including income-to-poverty ratio.
- **Alcohol Use Data (`ALQ_L.xlsx`)** – Provides responses related to lifetime and recent alcohol consumption.
- **Demographics Data (`DEMO_L.xlsx`)** – Includes key demographic variables such as age, gender, and race/ethnicity.

All datasets are merged using the **SEQN (Respondent ID)** column to ensure participant data is aligned across files.

## **Methodology**
### **1. Data Preparation**
- **Reading the Datasets:** The script loads three datasets and merges them by `SEQN`.
- **Variable Selection:** The binary dependent variable **ALQ111** (Ever had a drink of alcohol) is recoded (`1 = Yes, 0 = No`).
- **Predictor Variables:** `RIAGENDR` (Gender), `RIDAGEYR` (Age), and `INDFMPIR` (Income-to-Poverty Ratio) are selected as independent variables.
- **Handling Missing Values:** Missing observations are removed using `na.omit()`.

### **2. Logistic Regression Models**
The analysis estimates three **logistic regression models** with increasing complexity:
- **Model 1:** `ALQ111 ~ RIAGENDR` (Gender only)
- **Model 2:** `ALQ111 ~ RIAGENDR + RIDAGEYR` (Adds Age)
- **Model 3:** `ALQ111 ~ RIAGENDR + RIDAGEYR + INDFMPIR` (Adds Income)

### **3. Model Evaluation**
- **Likelihood Ratio Tests (LRT):** Compares nested models to check if adding predictors significantly improves the model.
- **Akaike Information Criterion (AIC) & Bayesian Information Criterion (BIC):** Lower values indicate a better model fit.
- **Variance Inflation Factor (VIF):** Ensures independent variables do not exhibit high collinearity.

### **4. Interpretation & Results**
- The best model is **Model 3**, as it has the **lowest AIC/BIC** and a significant LRT improvement over Model 2.
- **VIF values** are low, confirming **no multicollinearity**.
- **Odds Ratios** are calculated for better interpretability of predictor effects.
- A **ggplot2 visualization** illustrates the predicted probability of alcohol consumption across age and gender.

## **Repository Contents**
| File Name | Description |
|-----------|------------|
| `Homework_4_03092025.Rmd` | R Markdown script containing the analysis |
| `INQ_L.xlsx` | Income dataset |
| `ALQ_L.xlsx` | Alcohol Use dataset |
| `DEMO_L.xlsx` | Demographics dataset |
| `README.md` | Project documentation (this file) |

## **Installation & Running the Script**
### **Prerequisites**
Ensure you have the following R packages installed:
```r
install.packages(c("dplyr", "ggplot2", "car", "MASS", "lmtest", "readxl"))
