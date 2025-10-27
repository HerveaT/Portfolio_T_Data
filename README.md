# Climate Porject - Evolution of Temperature in Algiers: Climate Trend Analysis

### Objective

Analyze decades of temperature records in Algiers to detect central climate tendencies, seasonal variations, and significant long-term trends linked to climate change. Emphasize the connection between temperature dynamics and local socio-economic impacts, supporting decision-making for urban sustainability.

### Data Description
Used over 44 years of daily meteorological data (average, maximum, and minimum values), sourced from trusted climate repositories and validated for consistency. The time series covers January 1980 to November 2023, totaling 16,012 observations

### Tools

- Excel-Initial data cleaning, inspection, and validation
- Python (Pandas, Statsmodels, NumPy)-Time series analysis, regression modeling, and visualization

### Data Cleaning/Preparation

In the initial data preparation phase, we performed the following tasks:

1. Imported, inspected, and formatted data.
2. Managed missing values in temperature columns.
3. Created monthly dummy variables for seasonal analysis.

### Exploratory Data Analysis

EDA involved exploring climate (temperature) data to answer key questions, such as:

- What is the main trend in temperature over time in Algiers?
- Are there distinct seasonal patterns or cycles in the climate data?
- Do we observe any anomalies, outliers, or notable shifts in temperature across decades?

### Methods & Approach

1. Applied OLS linear trend regression to estimate long-term warming patterns.
2. Used HAC (heteroscedasticity- and autocorrelation-consistent) standard errors for robust inference.
3. Modeled seasonality via month-based dummy variables in a regression framework.
4. Presented descriptive statistics, distribution plots, and time-series visualizations.

### Key Findings

The analysis reveals a statistically significant, upward trend in daily average temperatures in Algiers, with a regression coefficient of 0.0002 and a p-value of 0.019, confirming a persistent warming pattern over the studied period. Seasonal modeling highlighted strong, consistent monthly effects, where temperatures peaked in July and August and were lowest in winter, as shown by a high R² of 0.83. While the trend regression is aligned with global warming findings, it accounted for only a small fraction of total temperature variability (R² = 0.006), indicating that additional climatic and environmental factors substantially influence daily temperatures. Rigorous model diagnostics further signaled autocorrelation and possible multicollinearity, so results should be interpreted with caution and considered alongside broader climate dynamics.

### Impact & Business Value

The results highlight clear evidence of warming and pronounced climate seasonality in Algiers, with implications for public health, urban infrastructure planning, and resource management. Insights are applicable for policy adaptation, climate resilience, and long-term sustainability.

### Visual Communication

<img width="986" height="374" alt="Temperature trends in Algiers_Plot" src="https://github.com/user-attachments/assets/e527a400-cfc5-4d9a-bdaf-7ed31ceecc21" />

<img width="708" height="374" alt="Representation of Algiers' density function" src="https://github.com/user-attachments/assets/82f107c0-2cdc-4f2b-9b27-166fdbaec491" />

<img width="704" height="374" alt="Temperature trends in Algiers_Histoplot" src="https://github.com/user-attachments/assets/936ad776-9356-4443-bf74-58e65182b0da" />

<img width="986" height="374" alt="Temperature and Fitted Trend" src="https://github.com/user-attachments/assets/c18951c9-5fda-4412-8efc-71902773a72e" />

<img width="678" height="374" alt="Seasonal Coefficients - Algiers" src="https://github.com/user-attachments/assets/5101585e-7206-4d1e-9da5-d2921a2de33f" />

### Challenges & Limitations

- Trend regression captured only a fraction of variability due to climate complexity.
- Large condition number and low Durbin-Watson suggest autocorrelation and multicollinearity issues, requiring more advanced modeling.
- Recommends future use of additional covariates, more granular meteorological data, and robust climate models for deeper insights.
  
### References:

1. [RPubs](https://rpubs.com/maxlamcoco/portfolio-EDA)
2. 







