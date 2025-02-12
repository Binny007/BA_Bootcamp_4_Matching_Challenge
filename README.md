# BA_Bootcamp_4_Matching_Challenge

# Matching Challenge: Remote Workers' Career Satisfaction


# Remote Workers' Career Satisfaction: Matching Analysis

## 🚀 Overview

This project explores the **career satisfaction** of **remote** versus **non-remote** workers by applying **matching techniques** to estimate the treatment effect. The groups of remote and non-remote workers are inherently different, making direct comparisons misleading. The goal is to use **matching** to account for these differences and accurately estimate whether remote work impacts career satisfaction.

## 📝 Steps and Findings

### 1. **Picking Variables** 🧑‍💻
   The selection of variables is crucial for ensuring that we can account for factors that might confound the comparison between remote and non-remote workers. We aim for variables that fully describe the characteristics of the groups to meet the **unconfoundedness assumption**.

   - **Variables Selected**:
     - `Salary`, `YearsCodedJob`, `Country`, `Hobby`, `CompanySizeNumber`, and several job-related variables like `Data_scientist`, `Web_developer`, etc.
   
   These variables should describe the workers sufficiently, ensuring that after matching, the remote and non-remote groups are comparable on these characteristics.

### 2. **T-Test Loop** 🔬
   The **T-tests** are used to check if the means of the continuous variables differ between remote and non-remote workers. This is a crucial step because if the groups are statistically different on these variables, it suggests they are not directly comparable, necessitating matching.

   #### T-Test Results:
   - **Salary**: p-value = `1.057708e-22` (statistically significant)
   - **YearsCodedJob**: p-value = `3.637316e-30` (statistically significant)

   Since both variables show statistically significant differences between remote and non-remote workers, we conclude that the groups are indeed different, and thus **matching** is necessary.

### 3. **Binary Variables** 🔢
   The non-numeric variables (e.g., `Country`, `Hobby`, and job roles) were converted into **binary variables** using one-hot encoding. This transformation is important as matching algorithms require numerical inputs.

   #### Transformation:
   We used `pd.get_dummies()` to convert categorical variables into binary variables.

### 4. **Matching** 🔄
   Using the selected variables, we applied **matching** to account for the differences between remote and non-remote workers. The matching technique pairs treated (remote) and control (non-remote) units based on observed covariates, aiming to estimate the **Average Treatment Effect (ATE)**, **Average Treatment effect on the Treated (ATT)**, and **Average Treatment effect on the Control (ATC)**.

   #### Matching Results:
   - **ATE (Average Treatment Effect)**: `0.114` (p-value = `0.378`) - No significant impact of remote work on career satisfaction.
   - **ATC (Average Treatment Effect on the Control)**: `0.106` (p-value = `0.436`) - Similar result for control group.
   - **ATT (Average Treatment Effect on the Treated)**: `0.187` (p-value = `0.187`) - Slightly higher, but still not statistically significant.

   These results suggest that after controlling for relevant covariates, there is no significant evidence that remote work has a measurable impact on career satisfaction.

### 5. **Robustness Check** 🔍
   To ensure the results were not due to random chance, a **robustness check** was performed by removing one of the confounders (`Hobby`). This step tests the stability of the results under different assumptions.

   #### Robustness Check Results:
   - **ATE**: `0.148` (p-value = `0.259`)
   - **ATC**: `0.140` (p-value = `0.311`)
   - **ATT**: `0.220` (p-value = `0.109`)

   Again, the treatment effects were not statistically significant, reinforcing the conclusion that remote work does not significantly affect career satisfaction after controlling for confounders.

---

## 🧐 Key Takeaways

- **Matching** is a powerful technique to reduce bias in observational studies, particularly when direct comparisons between groups are not possible.
- While remote workers showed some differences in terms of background variables, **matching** adjusted for those differences and showed that the apparent benefits of remote work on career satisfaction disappear.
- The **robustness check** confirmed the stability of these findings, increasing confidence that the observed effects are not due to random variation.

Thus, based on this analysis, there is no significant evidence to suggest that remote work leads to higher career satisfaction compared to non-remote work once we account for background characteristics.

## 📂 Repository Structure

- `/stackoverflow.csv/` → Dataset containing the survey data of remote and non-remote workers.
- `/Matching Challenge.ipynb/` → Jupyter Notebook containing the code for analysis.
- `/Matching Challenge.pdf` → PDF file containing the detailed challenge description.
- `README.md` → This file.

---
