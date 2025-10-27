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

### Data Analysis

````Python
# Summary statistics
print(temp_ts.describe())

# Boxenplot for temperature distribution
sns.boxenplot(x=algern['TAVG'])
plt.show()

# Time series plot
plt.figure(figsize=(12,4))
plt.plot(temp_ts, color='grey')
plt.title("Temperature trends in Algiers")
plt.show()

# Histogram with density overlay
plt.figure(figsize=(8,4))
sns.histplot(temp_ts.dropna(), kde=True, color='brown')
plt.title("Temperature trends in Algiers")
plt.show()

plt.figure(figsize=(8,4))
sns.kdeplot(temp_ts.dropna(), color='blue')
plt.title("Kernel Density Estimate of Temperature")
plt.show()

# Trend regression with HAC robust errors
trend = np.arange(len(temp_ts))
X = add_constant(trend)
model = OLS(temp_ts.values, X, missing='drop').fit(cov_type='HAC', cov_kwds={'maxlags':18})
print(model.summary())

# Original vs fitted trend plot
temp_fit = pd.Series(model.fittedvalues, index=temp_ts.index)
plt.figure(figsize=(12,4))
plt.plot(temp_ts, label='Original', color='blue')
plt.plot(temp_fit, label='Fitted Trend', color='yellow', linewidth=2)
plt.title("Temperature and Fitted Trend")
plt.legend()
plt.show()

# STL decomposition for trend and seasonality
stl = STL(temp_ts.dropna(), period=365, seasonal=7)
res = stl.fit()
res.plot()
plt.show()

# Detrended series
detrended = temp_ts - res.trend
plt.figure(figsize=(12,4))
plt.plot(detrended, color='blue')
plt.title("Detrended Temperature Series")
plt.show()

# Monthly dummy regression for seasonality
month_dummies = pd.get_dummies(algern['Date'].dt.month)
month_dummies.index = algern['Date']
month_dummies = month_dummies.loc[detrended.dropna().index]
mod_seas = OLS(detrended.dropna(), month_dummies).fit()
print(mod_seas.summary())

# Seasonal coefficients plot
plt.figure(figsize=(8,4))
plt.step(range(1,13), mod_seas.params, where='mid', color='red')
plt.xticks(ticks=range(1,13), labels=["J","F","M","A","M","J","J","A","S","O","N","D"])
plt.title("Seasonal Coefficients - Algiers")
plt.show()
````

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







