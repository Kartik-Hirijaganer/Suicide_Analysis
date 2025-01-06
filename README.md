# Suicide Analysis using World Data

## Overview
This project aims to identify the most influencing factors responsible for the suicide mortality rate in the world.
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


## Dataset Description
The data is collected from the World Bank Data set. Reference: https://data.worldbank.org/  

## Project Workflow

### Installing Libraries and Loading Dataset

### Analyzing and Preprocessing Data

- Created pivot table by converting year columns into single columns setting Country Name, Country Code, and Year as the index. The Series Name column is used as new column headers.
- Removed columns having more than 75% data as Null or NaN. 
- Filled NaN values with the median of each column as columns had about normal distribution.

#### Selecting Relevant Features
- Used the Backward Elimination process to select the best features for analysis.


#### Addressing Multicollinearity
- **Calculated** **Variable Inflation Factor (VIF)** for all independent variables.  
- **Iteratively removed variables** with the highest VIF until all remaining variables had **VIF < 4**.  

#### Checked for Non-Normality
- A scatter plot of fitted vs residuals from the linear regression model was plotted.
- Performed Breusch-Pagan test for Heteroscedasticity.
  - Breusch-Pagan test p-value: 0.5318654520312872.
- Plotted Histogram of Residuals
- Further plotted Q-Q plot to understand non-normality

#### Further Feature Selection
- Further dropped variables having a p-value higher than 0.05 and features that did not affect the model accuracy when dropped.
- Re-checked VIF to see if multi-collinearity still exists.

#### Decision Trees
- Plotted Decision tree to identify best features for the split by first finding the optimal depth of the tree.  

## Ensemble Models: Bagging, Boosting and Random Forest
- Ran Bagging, Boosting, and Random Forest to find the best prediction model.
- Boosting Model has the least RSME value.


### Feature Analysis
- Proceeded with the Boosting Model to find top features responsible for suicide rates.
- Plotted Partial Dependency Plots of the top 4 most influencing factors.
- Further built SHAP explainer to validate the findings.
- Used SHAP force plot to analyze most suicide rate influencing factors for individual countries and whether the factors changed in a decade.

#### Visualizations
- plotted visualizations of suicide rates and the most influencing factors to visualize the effects of factors in suicide rates. 
**Visualizations for UAE**
![image alt](https://github.com/Kartik-Hirijaganer/Suicide_Analysis/blob/6de95686438d3e84d46a3dbde856bf1def233afa/images/factors_effect_UAE.png)
![image alt](https://github.com/Kartik-Hirijaganer/Suicide_Analysis/blob/6de95686438d3e84d46a3dbde856bf1def233afa/images/shap_decade_UAE.png)
![image alt](https://github.com/Kartik-Hirijaganer/Suicide_Analysis/blob/6de95686438d3e84d46a3dbde856bf1def233afa/images/mortality_trend_India.png)
![image alt](https://github.com/Kartik-Hirijaganer/Suicide_Analysis/blob/6de95686438d3e84d46a3dbde856bf1def233afa/images/unemp_vs_suicide_Uk.png)

## How to Run the Project

### 1️⃣ Clone the Repository

### 2️⃣ Install Dependencies

### 3️⃣ Download and Place the Dataset

### 4️⃣ Run the .ipynb file 


### **Top 5 Factors**
1. **Unemployment Rate:** As unemployment increases, there is a rise in suicide rates.
2. **High Tariff Rate** → As the tariff rates increased, there was a corresponding rise in the suicide mortality rate.
3. **Tax Revenue** → Due to the rise in tax revenue, a significant number of people began to take their own lives
4. **Immunization** → Low immunization rates can increase suicide rates by causing more illness and putting pressure on mental health support.
