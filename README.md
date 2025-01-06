# Suicide Ananlysis using World Data

## Overview
This project aims to identify most influencing factors responsible for suicide mortality rate in the world.
## Tech Stack
- **Programming Language:** Python  
- **Libraries & Frameworks:**
  - **Pandas** – Data manipulation and analysis  
  - **NumPy** – Numerical computing  
  - **Matplotlib** & **Seaborn** – Data visualization  
  - **Plotly** – Interactive visualizations  
  - **Scikit-Learn** – Machine learning algorithms and tools  
  - **StatsModels** – Statistical modeling and tests  
  - **SHAP** – Explainability of machine learning models  
  - **DMBA** – Model selection, regression diagnostics, and visualizations  
  - **pydotplus** – Graph visualization (for decision trees)  
  - **IPython** – Interactive computing and display  
  - **SciPy** – Statistical and scientific functions  
  - **sklearn.tree** – Decision tree models and visualizations  
  - **sklearn.ensemble** – Ensemble learning models like Random Forest and Gradient Boosting


## Dataset Description
The dataset is collected from World Bank Data set. Reference: https://data.worldbank.org/  

## Project Workflow

### Installing Libraries and Loading Dataset

### Analyzing and Preprocessing Data

- Created pivot table by converting year columns into single column setting Country Name, Country Code, and Year as the index. The Series Name column is used as new column headers.
- Removed columns having more than 75% data as Null or NaN. 
- Filled NaN values with median of each column as columns had about normal distribution.

#### Selecting Relevant Features
- Used Backward Elimination process to select best features for analysis.


#### Addressing Multicollinearity
- **Calculated** **Variable Inflation Factor (VIF)** for all independent variables.  
- **Iteratively removed variables** with the highest VIF until all remaining variables had **VIF < 4**.  

#### Checked for Non-Normality
- Plotted a scatter plot of fitted vs residuals from the Linear Regression model generated.
- Performed Breusch-Pagan test for Heteroscedasticity.
-- Breusch-Pagan test p-value: 0.5318654520312872.
- Plotted Histogram of Residuals
- Further plotted Q-Q plot to understand non-normality

#### Further Feature Selection
- Further dropped variables having p-value higher than 0.05 and features which had no effect on the model accuracy when dropped.
- Rechecked VIF to check if multi-collinearity still exists.

#### Decision Trees
- Plotted Decision tree to identify best features for the split by first finding the optimal dept of the tree.  

## Ensemble Models: Bagging, Boosting and Random Forest
- Ran Bagging, Boosting and Random Forest to find best model for prediction.
- Boosting Model has the least RSME value.


### Feature Analysis
- Proceeded with Boosting Model to find top features responsible for suicide rates.
- Plotted Partial Dependency Plots of the top 4 most influencing factors.
- Further built SHAP explainer to validate the findings.
- Used SHAP force plot to analyse most suicide rate influcing factors for individual countries and whether the factors changed in a decade.

#### Visualizations
- plotted visualizations of sucide rates and its most influencing factors to visualize the effects of factors in suicide rates. 


## How to Run the Project

### 1️⃣ Clone the Repository

### 2️⃣ Install Dependencies

### 3️⃣ Download and Place the Dataset

### 4️⃣ Run the .ipynb file 


### **Top 5 Features Increasing Risk (Hazard Ratio > 1)**
1. **Unemployment Rate:** As umployment increases, there is a rise in suicide rates.
2. **High Tariff Rate** → As the tariff rates increased, there was a corresponding rise in the suicide mortality rate.
3. **Tax Revenue** → Due to the rise in tax revenue, a significant number of people began to take their own lives
4. **Immunization** → Low immunization rates can increase suicide rates by causing more illness and putting pressure on mental health support.
