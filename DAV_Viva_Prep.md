# 📊 DAV — Data Analytics & Visualization | Complete Viva Preparation
### Mumbai University | T.E. Sem VI | All Modules Covered

> **How to use this**: Every Q&A is written the way your examiner will ask it.
> Formulas are boxed. 🔴 = Most likely to be asked. Read section by section.

---

## TABLE OF CONTENTS

1. [Module 1 — Data Analytics Lifecycle](#module1)
2. [Module 2 — Regression Models](#module2)
   - [Simple Linear Regression](#slr)
   - [Multiple Linear Regression](#mlr)
   - [Logistic Regression](#logistic)
3. [Module 3 — Time Series Analysis](#module3)
4. [Module 4 — Text Analytics](#module4)
5. [Module 5 — Data Analytics with R](#module5)
6. [Module 6 — Data Analytics with Python](#module6)
7. [Quick Formula Cheat Sheet](#formulas)

---

## MODULE 1 — Data Analytics Lifecycle {#module1}

### 🔴 Q1. What is Data Analytics? Why is it important?

**Answer:** Data Analytics is the process of **examining, cleaning, transforming, and modeling data** to discover useful information, draw conclusions, and support decision-making.

**Why important:**
- Turns raw data into actionable insights
- Helps businesses reduce costs, increase revenue, improve customer experience
- Drives decisions in healthcare, finance, marketing, sports, government

**Types of Analytics:**
| Type | What it answers | Example |
|---|---|---|
| **Descriptive** | What happened? | Sales report for last month |
| **Diagnostic** | Why did it happen? | Why did sales drop in March? |
| **Predictive** | What will happen? | Will this customer churn next month? |
| **Prescriptive** | What should we do? | Which customers to target for a campaign? |

---

### 🔴 Q2. What are the 6 phases of the Data Analytics Lifecycle?

**Answer:** The Data Analytics Lifecycle is a **repeating, iterative** process with 6 phases:

```
Phase 1: Discovery
     ↓
Phase 2: Data Preparation
     ↓
Phase 3: Model Planning
     ↓
Phase 4: Model Building
     ↓
Phase 5: Communicate Results
     ↓
Phase 6: Operationalize
     ↑_________________________↑ (iterative feedback loop)
```

---

### 🔴 Q3. Explain Phase 1 — Discovery.

**Answer:** Discovery is about **understanding the problem before touching any data**.

Activities:
- **Learning the Business Domain** — understanding industry context, terminology, goals
- **Resources** — identifying available team, tools, infrastructure, budget
- **Framing the Problem** — clearly defining what problem we are solving
- **Identifying Key Stakeholders** — who will use the results, who has authority
- **Interviewing the Analytics Sponsor** — understanding sponsor's goals, success criteria, timeline
- **Developing Initial Hypotheses** — forming educated guesses about what the data might show
- **Identifying Potential Data Sources** — internal databases, APIs, external datasets, surveys

> **Key output**: A clear problem statement, list of data sources, and initial hypotheses to test.

---

### 🔴 Q4. Explain Phase 2 — Data Preparation.

**Answer:** Data Preparation is the most **time-consuming phase** (60–80% of project time). It transforms raw data into a clean, usable form.

Activities:
- **Preparing the Analytic Sandbox** — creating a dedicated workspace/environment for data exploration
- **Performing ETLT** — Extract, Transform, Load, Transform again
  - Extract: pull data from sources
  - Transform: clean, format, aggregate
  - Load: store in sandbox
- **Learning About the Data** — understand structure, distributions, ranges
- **Data Conditioning** — fix errors, handle outliers, normalize
- **Survey and Visualize** — quick plots to understand data shape
- **Common Tools**: Apache Hadoop, MapReduce, Pig, Hive, SQL, R, Python

**Key tasks in Data Preparation:**
1. Handling missing values (drop/impute)
2. Removing duplicates
3. Fixing inconsistencies (e.g., "Male" vs "M")
4. Type conversion (string dates to datetime)
5. Feature engineering (creating new columns from existing ones)
6. Normalization/Standardization

---

### 🔴 Q5. What is ETLT? How is it different from ETL?

**Answer:**
- **ETL** = Extract → Transform → Load (traditional data warehouse approach)
- **ETLT** = Extract → Transform → Load → Transform again (modern analytics approach)

In ETLT, data is loaded into the analytic sandbox first (partially transformed), then **further transformed in the sandbox** using analytics tools. This is more flexible for exploratory analytics.

---

### Q6. Explain Phase 3 — Model Planning.

**Answer:** Model Planning is about deciding **which statistical or machine learning model** to use.

Activities:
- **Data Exploration** — deep EDA (Exploratory Data Analysis) on the prepared data
- **Variable Selection** — choosing which features (columns) are relevant predictors
- **Model Selection** — deciding between regression, classification, clustering, time series, etc.
- **Common Tools**: R, Python, SAS, SQL, MATLAB

Key questions in model planning:
1. Is the target variable continuous → Regression
2. Is it categorical (yes/no, class) → Classification
3. No target variable → Clustering
4. Is data ordered over time → Time Series

---

### Q7. Explain Phase 4 — Model Building.

**Answer:** Model Building is the phase where the team **actually builds and tests the models**.

Activities:
- Train models on training data
- Evaluate on test/validation data
- Tune hyperparameters (model settings)
- Run multiple models and compare performance

**Common Tools:**
- R: `lm()`, `glm()`, `randomForest`
- Python: `scikit-learn`, `statsmodels`, `TensorFlow`, `Keras`
- SAS, SPSS, MATLAB, Weka, RapidMiner

---

### Q8. Explain Phase 5 — Communicate Results.

**Answer:** Results must be communicated **to stakeholders in a way they understand** (non-technical audience).

Activities:
- Summarize findings into key insights
- Create visualizations (charts, dashboards)
- Relate findings back to original business problem
- Explain model performance in business terms
- Use storytelling — data storytelling

Deliverables: Presentation, report, interactive dashboard

> The analyst must answer: "So what? What should the business DO with these findings?"

---

### Q9. Explain Phase 6 — Operationalize.

**Answer:** Operationalize means **deploying the model into production** so it runs automatically on new data.

Activities:
- Deploy model to production environment
- Create APIs so other apps can use the model
- Set up automated data pipelines
- Monitor model performance over time
- Retrain model when performance degrades (model drift)

> Example: A churn prediction model is deployed so it runs every week on new customer data and flags at-risk customers automatically.

---

### 🔴 Q10. What are the Key Roles in a Data Analytics project?

| Role | Responsibility |
|---|---|
| **Analytics Sponsor** | Business leader who funds and champions the project |
| **Business Intelligence Analyst** | Understands business needs, translates to analytics requirements |
| **Data Engineer / DBA** | Manages data infrastructure, pipelines, databases |
| **Data Scientist** | Builds models, statistical analysis, feature engineering |
| **Data Analyst** | Explores data, creates reports, visualizations |
| **Project Manager** | Coordinates team, manages timeline and deliverables |

---

## MODULE 2 — Regression Models {#module2}

---

## SIMPLE LINEAR REGRESSION {#slr}

### 🔴 Q11. What is Simple Linear Regression?

**Answer:** Simple Linear Regression (SLR) models the **linear relationship** between one **independent variable (X)** and one **dependent variable (Y)**.

It assumes:
- There is a straight-line (linear) relationship between X and Y
- The residuals (errors) are normally distributed with constant variance

---

### 🔴 Q12. What is the Regression Equation?

**THE FORMULA:**
```
Ŷ = β₀ + β₁X
```

Where:
- **Ŷ** (Y-hat) = Predicted value of Y
- **β₀** (beta-zero) = Y-intercept (value of Y when X = 0)
- **β₁** (beta-one) = Slope (how much Y changes for each 1-unit increase in X)
- **X** = Independent variable (predictor)

**Formulas to calculate β₁ and β₀:**

```
β₁ = Σ(Xᵢ - X̄)(Yᵢ - Ȳ) / Σ(Xᵢ - X̄)²

β₀ = Ȳ - β₁ × X̄
```

Where X̄ = mean of X, Ȳ = mean of Y

---

### 🔴 Q13. What are Fitted Values and Residuals?

**Answer:**
- **Fitted Value (Ŷᵢ)** = The value predicted by the regression equation for observation i
- **Residual (eᵢ)** = The difference between the actual value and the predicted value

```
eᵢ = Yᵢ - Ŷᵢ
```

Residuals tell us **how far off** our model's predictions are from reality.

**Properties of residuals:**
- Sum of residuals = 0 (always, in OLS regression)
- Should be randomly scattered (no pattern) — if there is a pattern, the model is wrong

---

### 🔴 Q14. What is the Least Squares Method?

**Answer:** The Least Squares method finds the regression line that **minimizes the sum of squared residuals** (SSE — Sum of Squared Errors).

```
Minimize: SSE = Σ(Yᵢ - Ŷᵢ)² = Σeᵢ²
```

Why squared?
- Prevents positive and negative errors from cancelling out
- Penalizes large errors more than small ones

The line found by this method is called the **Ordinary Least Squares (OLS)** regression line — the uniquely "best fit" line.

---

### Q15. What is R-squared (Coefficient of Determination)?

**Answer:** R² measures **how much of the variation in Y is explained by X** (the model).

```
R² = 1 - SSE/SST = SSR/SST
```

Where:
- **SST** = Total Sum of Squares = Σ(Yᵢ - Ȳ)² (total variation in Y)
- **SSE** = Sum of Squared Errors = Σ(Yᵢ - Ŷᵢ)² (unexplained variation)
- **SSR** = Sum of Squares Regression = SST - SSE (explained variation)

**Interpretation:**
- R² = 1.0 → Perfect fit (model explains 100% of variation)
- R² = 0.8 → Model explains 80% of variation
- R² = 0.0 → Model explains nothing

> **Good R² is context-dependent.** In social sciences, 0.5 is good. In physics, 0.99 might be expected.

---

### Q16. What are the assumptions of Linear Regression?

1. **Linearity** — relationship between X and Y is linear
2. **Independence** — observations are independent of each other
3. **Homoscedasticity** — residuals have constant variance (not increasing/decreasing)
4. **Normality** — residuals are normally distributed
5. **No multicollinearity** (for MLR) — predictors are not highly correlated with each other

---

## MULTIPLE LINEAR REGRESSION {#mlr}

### 🔴 Q17. What is Multiple Linear Regression?

**Answer:** Multiple Linear Regression (MLR) extends SLR to use **two or more independent variables** to predict Y.

**THE FORMULA:**
```
Ŷ = β₀ + β₁X₁ + β₂X₂ + β₃X₃ + ... + βₚXₚ
```

Where:
- X₁, X₂, ..., Xₚ = independent variables (predictors/features)
- β₁, β₂, ..., βₚ = regression coefficients
- β₀ = intercept
- p = number of predictors

**Example:** Predicting house price:
`Price = β₀ + β₁(Area) + β₂(Bedrooms) + β₃(Location_Score)`

---

### 🔴 Q18. What is Adjusted R-squared? Why use it instead of R-squared?

**Answer:**
```
Adjusted R² = 1 - [(1 - R²)(n - 1) / (n - p - 1)]
```

Where:
- n = number of observations
- p = number of predictor variables

**Why Adjusted R²?**
- Regular R² **always increases** when you add more variables — even useless ones
- Adjusted R² **penalizes** adding variables that don't improve the model
- Adjusted R² decreases if a new variable adds less than expected by chance

> Use Adjusted R² to compare models with different numbers of predictors.

---

### Q19. What is Cross-Validation in regression?

**Answer:** Cross-validation is a technique to **evaluate how well the model generalizes** to unseen data.

**k-Fold Cross-Validation:**
1. Split data into k equal parts (folds)
2. For each fold: train on the remaining k-1 folds, test on the held-out fold
3. Average the performance across all k folds

**Common choice:** k = 5 or k = 10

**Why?** Prevents overfitting — model may perform well on training data but poorly on new data.

---

### 🔴 Q20. What is Stepwise Regression? What are its types?

**Answer:** Stepwise Regression is an **automatic variable selection** method that adds or removes variables based on statistical criteria.

| Type | How it works |
|---|---|
| **Forward Selection** | Start with no variables, add the most significant one at each step |
| **Backward Elimination** | Start with ALL variables, remove the least significant one at each step |
| **Stepwise (Both)** | Combination — adds and removes variables at each step |

**Criterion used:** AIC (Akaike Information Criterion) or p-values

```
AIC = 2k - 2ln(L)
```
Where k = number of parameters, L = maximum likelihood

Lower AIC = better model

---

## LOGISTIC REGRESSION {#logistic}

### 🔴 Q21. What is Logistic Regression? When do you use it?

**Answer:** Logistic Regression is used when the **dependent variable is categorical** (binary — Yes/No, 0/1, True/False).

Unlike Linear Regression which predicts a continuous value, Logistic Regression predicts the **probability** that an observation belongs to a particular class.

**Examples:**
- Will this email be spam? (Yes/No)
- Will this customer buy? (Yes/No)
- Is this tumor malignant? (Yes/No)

---

### 🔴 Q22. What is the Logistic Response Function?

**Answer:** The Logistic (Sigmoid) function maps any input to a value between 0 and 1:

```
P(Y=1 | X) = 1 / (1 + e^-(β₀ + β₁X))
```

Or in compact form:
```
p = 1 / (1 + e^(-z))
where z = β₀ + β₁X₁ + β₂X₂ + ...
```

**Graph shape:** S-curve (sigmoid curve)
- As z → +∞, p → 1
- As z → −∞, p → 0
- At z = 0, p = 0.5

---

### 🔴 Q23. What is the Logit (Log-Odds)?

**Answer:** The logit is the **log of the odds ratio** — it transforms the probability p (0 to 1) to an unbounded value (−∞ to +∞):

```
logit(p) = log(p / (1-p)) = β₀ + β₁X₁ + β₂X₂ + ...
```

Where:
- **p / (1-p)** = odds of the event occurring
- **log(p/(1-p))** = log-odds = logit

**Why logit?** Because probabilities are bounded (0 to 1), but regression needs unbounded output. The logit transformation allows us to model probabilities using a linear equation.

---

### 🔴 Q24. What are Odds and Odds Ratio?

**Answer:**
- **Odds** = probability of event / probability of no event = p / (1-p)
- **Odds Ratio (OR)** = how much the odds change when X changes by 1 unit

```
Odds Ratio = e^β₁
```

**Interpretation:**
- OR = 1 → X has no effect on odds
- OR > 1 → X increases odds of Y=1
- OR < 1 → X decreases odds of Y=1

**Example:** If β₁ = 0.5 for age, then OR = e^0.5 = 1.65
→ For each 1-year increase in age, the odds of the event increase by **65%**

---

### Q25. What is a Generalized Linear Model (GLM)?

**Answer:** A Generalized Linear Model is a flexible extension of linear regression that allows:
1. The **response variable** to have distributions other than normal (Poisson, Binomial, Gamma)
2. A **link function** that relates the linear predictor to the mean of the distribution

| Model | Distribution | Link Function |
|---|---|---|
| Linear Regression | Normal (Gaussian) | Identity (g(μ) = μ) |
| Logistic Regression | Binomial | Logit (g(p) = log(p/(1-p))) |
| Poisson Regression | Poisson | Log (g(μ) = log(μ)) |

Logistic Regression is a **special case of GLM** with Binomial distribution and logit link.

---

### 🔴 Q26. What is the difference between Linear and Logistic Regression?

| Feature | Linear Regression | Logistic Regression |
|---|---|---|
| **Output** | Continuous value | Probability (0 to 1) |
| **Used for** | Regression problems | Classification problems |
| **Dependent variable** | Continuous | Binary (0/1) |
| **Equation** | Ŷ = β₀ + β₁X | P = 1/(1+e^-z) |
| **Error distribution** | Normal | Binomial |
| **Method** | Least Squares | Maximum Likelihood |
| **Evaluation** | R², RMSE, MSE | Accuracy, AUC-ROC, Confusion Matrix |

---

### Q27. How do you assess a Logistic Regression model?

**Metrics:**

1. **Confusion Matrix:**
```
                 Predicted
                 Pos    Neg
Actual  Pos  |  TP  |  FN  |
        Neg  |  FP  |  TN  |
```

2. **Accuracy** = (TP + TN) / (TP + TN + FP + FN)

3. **Precision** = TP / (TP + FP) — of all predicted positive, how many are actually positive?

4. **Recall (Sensitivity)** = TP / (TP + FN) — of all actual positive, how many were correctly predicted?

5. **F1-Score** = 2 × (Precision × Recall) / (Precision + Recall)

6. **AUC-ROC** — Area Under the ROC Curve (closer to 1 = better model)

7. **Log-Loss (Cross-Entropy):**
```
Log-Loss = -(1/n) Σ [yᵢlog(p̂ᵢ) + (1-yᵢ)log(1-p̂ᵢ)]
```

---

## MODULE 3 — Time Series Analysis {#module3}

### 🔴 Q28. What is a Time Series?

**Answer:** A Time Series is a **sequence of data points collected over time at regular intervals**.

Examples:
- Daily stock prices
- Monthly sales revenue
- Hourly temperature readings
- Weekly COVID case counts

**Components of a Time Series:**
| Component | Description |
|---|---|
| **Trend (T)** | Long-term upward or downward movement |
| **Seasonality (S)** | Regular repeating patterns (yearly, quarterly, weekly) |
| **Cyclical (C)** | Irregular fluctuations over longer periods (business cycles) |
| **Irregular/Noise (I)** | Random, unpredictable variations |

**Decomposition:**
- Additive: Y = T + S + C + I (components add up)
- Multiplicative: Y = T × S × C × I (components multiply)

---

### 🔴 Q29. What is the Box-Jenkins Methodology?

**Answer:** The Box-Jenkins method is a **systematic approach to identifying, estimating, and forecasting using ARIMA models**.

**Four steps:**

1. **Identification** — look at ACF and PACF plots to determine p, d, q values
2. **Estimation** — estimate the model parameters (coefficients)
3. **Diagnostic Checking** — verify residuals are white noise (random, no pattern)
4. **Forecasting** — use the fitted model to forecast future values

> The Box-Jenkins approach is **iterative** — if diagnostic checks fail, go back to step 1.

---

### 🔴 Q30. What is Stationarity? Why does ARIMA need it?

**Answer:** A time series is **stationary** if its statistical properties (mean, variance, covariance) do not change over time.

**Why needed?** ARIMA models assume the data is stationary. Non-stationary data with trends or seasonality will produce unreliable results.

**How to test for stationarity:**
- **ADF Test (Augmented Dickey-Fuller)** — H₀: series is non-stationary. If p < 0.05, reject H₀ → stationary
- **KPSS Test** — complementary test

**How to make data stationary:**
- **Differencing** — subtract previous value from current value
- First difference: ΔYₜ = Yₜ - Yₜ₋₁
- Second difference: Δ²Yₜ = ΔYₜ - ΔYₜ₋₁

---

### 🔴 Q31. What is the Autocorrelation Function (ACF)?

**Answer:** The ACF measures the **correlation between a time series and its lagged (past) versions**.

```
ACF(k) = Correlation(Yₜ, Yₜ₋ₖ)
```

Where k = lag (how many steps back)

- ACF at lag 1 = correlation between Yₜ and Yₜ₋₁ (yesterday)
- ACF at lag 12 = correlation with 12 periods ago (monthly seasonality)

**ACF plot:** Plots correlation values vs. lag numbers
- Values outside the **blue confidence bands** (±1.96/√n) are statistically significant
- **Gradual decline** in ACF → AR process
- **Sharp cutoff** at lag q → MA process of order q

---

### Q32. What is PACF (Partial Autocorrelation Function)?

**Answer:** PACF measures the correlation between Yₜ and Yₜ₋ₖ **after removing the effect of the intermediate lags**.

Used to identify the order of the **AR (Autoregressive)** component:
- **Sharp cutoff at lag p** in PACF → AR(p) model

| | ACF | PACF |
|---|---|---|
| **AR(p)** | Gradual decline (tails off) | Sharp cutoff at lag p |
| **MA(q)** | Sharp cutoff at lag q | Gradual decline (tails off) |
| **ARMA(p,q)** | Tails off | Tails off |

---

### 🔴 Q33. What is an Autoregressive (AR) Model?

**Answer:** An AR model predicts Y using **its own past values** (lagged values).

```
AR(p): Yₜ = c + φ₁Yₜ₋₁ + φ₂Yₜ₋₂ + ... + φₚYₜ₋ₚ + εₜ
```

Where:
- p = order (number of past values used)
- φ₁, φ₂, ..., φₚ = AR coefficients
- c = constant
- εₜ = white noise (random error)

**Example:** AR(1): Tomorrow's price = c + φ₁ × (Today's price) + noise

---

### 🔴 Q34. What is a Moving Average (MA) Model?

**Answer:** An MA model predicts Y using **past forecast errors** (residuals), not past Y values.

```
MA(q): Yₜ = μ + εₜ + θ₁εₜ₋₁ + θ₂εₜ₋₂ + ... + θqεₜ₋q
```

Where:
- q = order (number of past errors used)
- θ₁, ..., θq = MA coefficients
- μ = mean of the series
- εₜ = white noise at time t

**Key distinction:** MA uses past *errors*, AR uses past *values*.

---

### 🔴 Q35. What is an ARMA Model?

**Answer:** ARMA combines both AR and MA components:

```
ARMA(p,q): Yₜ = c + φ₁Yₜ₋₁ + ... + φₚYₜ₋ₚ + εₜ + θ₁εₜ₋₁ + ... + θqεₜ₋q
```

Used when the series is **stationary** and has both autoregressive and moving average patterns.

---

### 🔴 Q36. What is ARIMA? What do p, d, q mean?

**Answer:** ARIMA = **AutoRegressive Integrated Moving Average**

```
ARIMA(p, d, q)
```

| Parameter | Name | Meaning |
|---|---|---|
| **p** | AR order | Number of autoregressive terms (past Y values) |
| **d** | Integration order | Number of times the series is differenced to make it stationary |
| **q** | MA order | Number of moving average terms (past error terms) |

**ARIMA model equation (after d-th differencing):**
```
Yₜ' = c + φ₁Yₜ₋₁' + ... + φₚYₜ₋ₚ' + εₜ + θ₁εₜ₋₁ + ... + θqεₜ₋q
```
Where Yₜ' = d-th difference of Yₜ

**Special cases:**
- ARIMA(0,0,0) = White Noise
- ARIMA(1,0,0) = AR(1)
- ARIMA(0,0,1) = MA(1)
- ARIMA(0,1,0) = Random Walk
- ARIMA(p,0,q) = ARMA(p,q)

---

### Q37. How do you build an ARIMA model? (Step-by-step)

**Answer:**

**Step 1: Check and achieve stationarity**
- Plot the time series
- Run ADF test
- If non-stationary → difference the series (d = number of differences needed)

**Step 2: Identify p and q using ACF and PACF plots**
- Look at ACF → determines q (MA order): sharp cutoff at lag q
- Look at PACF → determines p (AR order): sharp cutoff at lag p

**Step 3: Estimate parameters**
- Fit ARIMA(p,d,q) model using Maximum Likelihood Estimation

**Step 4: Diagnostic checking**
- Check residuals — should look like white noise
- Run Ljung-Box test: H₀ = residuals are white noise (want p > 0.05)
- Check ACF/PACF of residuals — no significant spikes

**Step 5: Model selection**
- Compare models using AIC or BIC:
```
AIC = -2 × log(L) + 2k
BIC = -2 × log(L) + k × log(n)
```
Lower AIC/BIC = better model

**Step 6: Forecasting**
- Use the fitted model to generate h-step ahead forecasts
- Forecast comes with prediction intervals (confidence bands)

---

### Q38. What is RMSE and MAE in time series evaluation?

**Answer:**

```
RMSE = sqrt( (1/n) × Σ(Actual - Forecast)² )
MAE  = (1/n) × Σ|Actual - Forecast|
MAPE = (100/n) × Σ|( Actual - Forecast ) / Actual|
```

- **RMSE** — Root Mean Square Error. Penalizes large errors more. In same units as data.
- **MAE** — Mean Absolute Error. Average absolute difference. Less sensitive to outliers.
- **MAPE** — Mean Absolute Percentage Error. Scale-independent, expressed as %.

Lower values = better forecast.

---

## MODULE 4 — Text Analytics {#module4}

### 🔴 Q39. What is Text Analytics / Text Mining?

**Answer:** Text Analytics (Text Mining) is the process of **extracting useful information and patterns from unstructured text data** — emails, social media posts, reviews, articles, documents.

**History:**
- Roots in **Information Retrieval (IR)** (1950s) — library cataloguing, search engines
- Natural Language Processing (NLP) — 1960s onward
- Modern text mining uses ML + statistical methods on large text corpora

**Why important?**
- 80% of enterprise data is unstructured text
- Sources: emails, chat logs, reviews, social media, news, medical records

---

### 🔴 Q40. What are the 7 Practices of Text Analytics?

1. **Information Extraction** — pull structured data from unstructured text (e.g., named entities)
2. **Text Categorization/Classification** — assign predefined categories (e.g., spam/not spam)
3. **Text Clustering** — group similar documents without predefined categories
4. **Concept Extraction** — identify key concepts and relationships
5. **Sentiment Analysis** — determine emotional tone (positive/negative/neutral)
6. **Question Answering** — extract answers to natural language questions
7. **Summarization** — generate concise summaries of longer documents

---

### 🔴 Q41. What are the steps in Text Analysis?

**Answer:**

```
Step 1: Collecting Raw Text
    ↓
Step 2: Pre-processing (cleaning)
    ↓
Step 3: Representing Text (vectorization)
    ↓
Step 4: Feature Extraction (TF-IDF, embeddings)
    ↓
Step 5: Modeling (classify, cluster, summarize)
    ↓
Step 6: Evaluation
    ↓
Step 7: Gaining Insights
```

**Step 1 — Collecting Raw Text:**
- Web scraping, APIs, databases, PDF extraction, OCR

**Step 2 — Pre-processing:**
- **Tokenization** — split text into words/tokens
- **Lowercasing** — "Apple" → "apple"
- **Stop word removal** — remove "the", "is", "at", "which"
- **Punctuation removal** — remove ., !, ?, etc.
- **Stemming** — "running" → "run", "studies" → "studi" (Porter Stemmer)
- **Lemmatization** — "better" → "good", "running" → "run" (context-aware, dictionary based)

---

### 🔴 Q42. What is TF-IDF? Give the formula.

**Answer:** TF-IDF = **Term Frequency — Inverse Document Frequency**

Purpose: Measures how **important a word is to a specific document** in a collection (corpus). Common words like "the" get penalized; rare, meaningful words get rewarded.

**Formula:**
```
TF-IDF(t, d) = TF(t, d) × IDF(t)
```

**Term Frequency (TF):**
```
TF(t, d) = (Number of times term t appears in document d) / (Total terms in document d)
```

**Inverse Document Frequency (IDF):**
```
IDF(t) = log( N / df(t) )
```
Where:
- N = total number of documents in corpus
- df(t) = number of documents containing term t
- log = natural log (base e) or log base 10

**Combined:**
```
TF-IDF(t, d) = TF(t, d) × log( N / df(t) )
```

**Example:**
- Word "cloud" appears 5 times in a 100-word document → TF = 5/100 = 0.05
- "cloud" appears in 10 of 1000 documents → IDF = log(1000/10) = log(100) = 2
- TF-IDF = 0.05 × 2 = 0.10

> Word "the" might appear in all 1000 docs → IDF = log(1000/1000) = log(1) = 0 → TF-IDF = 0 (penalized to zero)

---

### 🔴 Q43. What is Sentiment Analysis?

**Answer:** Sentiment Analysis determines the **emotional tone** of a piece of text.

**Types:**
| Type | Output |
|---|---|
| **Binary** | Positive / Negative |
| **Ternary** | Positive / Negative / Neutral |
| **Fine-grained** | Very Positive / Positive / Neutral / Negative / Very Negative |
| **Aspect-based** | Sentiment per aspect (e.g., "battery good, camera bad") |

**Approaches:**
1. **Lexicon-based** — use a pre-built dictionary of words with sentiment scores (e.g., VADER, AFINN, SentiWordNet)
2. **Machine Learning** — train a classifier (Naïve Bayes, SVM, LSTM) on labeled data
3. **Deep Learning** — BERT, RoBERTa

**Use cases:**
- Product review analysis
- Social media monitoring (brand reputation)
- Customer feedback analysis
- Political opinion polling

---

### Q44. What is the difference between Stemming and Lemmatization?

| Feature | Stemming | Lemmatization |
|---|---|---|
| **Method** | Rule-based chopping of suffixes | Dictionary lookup + POS tagging |
| **Output** | May not be a real word ("studi") | Always a real dictionary word ("study") |
| **Speed** | Faster | Slower |
| **Accuracy** | Lower | Higher |
| **Example** | "better" → "better" (unchanged) | "better" → "good" |
| **Algorithm** | Porter Stemmer, Snowball | WordNet Lemmatizer |

---

### Q45. What is a Bag of Words (BoW) model?

**Answer:** BoW is the simplest way to represent text as numbers. It:
1. Creates a vocabulary of all unique words in the corpus
2. Represents each document as a vector of word counts

```
Corpus: ["I love data", "I hate data", "Data is great"]
Vocabulary: [I, love, data, hate, is, great]

"I love data"  → [1, 1, 1, 0, 0, 0]
"I hate data"  → [1, 0, 1, 1, 0, 0]
"Data is great"→ [0, 0, 1, 0, 1, 1]
```

**Limitation:** BoW ignores word order and context (semantic meaning is lost).

TF-IDF improves on BoW by weighting terms by their importance.

---

### Q46. What is Document Categorization and Topic Modeling?

**Answer:**

**Document Categorization** = assigning predefined labels/categories to documents
- Techniques: Naïve Bayes, SVM, Decision Trees, BERT
- Example: categorizing news into Sports/Politics/Tech

**Topic Modeling** = discovering hidden thematic structure in documents (unsupervised)
- **LDA (Latent Dirichlet Allocation)** — most popular
- Determines groups of words (topics) that tend to appear together
- Each document is a mixture of topics
- Example: topic 1 = {cloud, server, AWS, storage}, topic 2 = {stock, market, price, share}

---

## MODULE 5 — Data Analytics with R {#module5}

### 🔴 Q47. What is R? Why is it used in Data Analytics?

**Answer:** R is a **free, open-source programming language and environment** specifically designed for **statistical computing and graphics**.

**Why R?**
- Built-in statistical functions (mean, median, regression, tests)
- Excellent visualization (`ggplot2`, `plot`)
- Rich package ecosystem (CRAN — 18,000+ packages)
- Reproducible research (R Markdown)
- Widely used in academia and research

**How to install:** Download from `cran.r-project.org`
**IDE:** RStudio

---

### 🔴 Q48. What are the basic data types in R?

| Type | Description | Example |
|---|---|---|
| **numeric** | Decimal numbers | `3.14`, `42.0` |
| **integer** | Whole numbers | `5L`, `100L` |
| **character** | Text/strings | `"Hello"`, `"Data"` |
| **logical** | Boolean | `TRUE`, `FALSE` |
| **complex** | Complex numbers | `2+3i` |
| **factor** | Categorical with levels | `factor(c("A","B","A"))` |

**Data structures in R:**
| Structure | Description |
|---|---|
| **Vector** | 1D sequence of same type |
| **Matrix** | 2D, same type |
| **Data Frame** | 2D table, different types per column |
| **List** | Collection of different types |
| **Array** | Multi-dimensional |

---

### 🔴 Q49. How do you import and export data in R?

```r
# Import CSV
df <- read.csv("data.csv")

# Import Excel
library(readxl)
df <- read_excel("data.xlsx")

# Import from URL
df <- read.csv("https://example.com/data.csv")

# Export CSV
write.csv(df, "output.csv", row.names = FALSE)

# View data
head(df)       # First 6 rows
tail(df)       # Last 6 rows
str(df)        # Structure
summary(df)    # Summary statistics
dim(df)        # Rows and columns
nrow(df)       # Number of rows
ncol(df)       # Number of columns
names(df)      # Column names
```

---

### 🔴 Q50. What are descriptive statistics in R?

**Answer:** Descriptive statistics summarize the basic features of a dataset.

```r
mean(x)     # Arithmetic mean
median(x)   # Middle value
sd(x)       # Standard deviation
var(x)      # Variance
min(x)      # Minimum
max(x)      # Maximum
range(x)    # Min and max
quantile(x) # Quartiles (Q1, Q2, Q3)
IQR(x)      # Interquartile Range = Q3 - Q1
sum(x)      # Sum
length(x)   # Count
table(x)    # Frequency table
```

**Formulas:**
```
Mean (μ) = Σxᵢ / n

Variance (σ²) = Σ(xᵢ - μ)² / (n-1)   [sample variance]

Standard Deviation (σ) = √(Variance)

IQR = Q3 - Q1
```

---

### 🔴 Q51. What is Exploratory Data Analysis (EDA)?

**Answer:** EDA is the process of **exploring and understanding data before building formal models**.

**Goals of EDA:**
1. Understand the distribution of each variable
2. Detect outliers and anomalies
3. Discover relationships between variables
4. Check assumptions for models
5. Identify missing data

**Anscombe's Quartet** — classic example showing why visualization is needed: 4 datasets with nearly identical means, variances, and correlations — but completely different shapes. EDA would catch this; summary statistics alone would not.

---

### Q52. How do you visualize a single variable in R?

```r
# Histogram — distribution of numeric variable
hist(df$age, main="Age Distribution", xlab="Age", col="skyblue")

# Boxplot — detect outliers
boxplot(df$salary, main="Salary Distribution")

# Bar chart — frequency of categorical variable
barplot(table(df$gender))

# Density plot
plot(density(df$age))

# Using ggplot2
library(ggplot2)
ggplot(df, aes(x=age)) + geom_histogram(bins=30, fill="steelblue")
ggplot(df, aes(x=age)) + geom_boxplot()
ggplot(df, aes(x=gender)) + geom_bar()
```

---

### Q53. How do you examine multiple variables in R?

```r
# Scatter plot — two continuous variables
plot(df$age, df$salary)
ggplot(df, aes(x=age, y=salary)) + geom_point()

# Correlation matrix
cor(df[, c("age","salary","experience")])

# Pairs plot — all variable combinations
pairs(df[, c("age","salary","experience")])

# Boxplot by group
boxplot(salary ~ gender, data=df)
ggplot(df, aes(x=gender, y=salary)) + geom_boxplot()

# Heatmap
library(reshape2)
melted <- melt(cor(df[, numeric_cols]))
ggplot(melted, aes(x=Var1, y=Var2, fill=value)) + geom_tile()
```

---

### Q54. What is "Dirty Data"? How do you handle it?

| Problem | Detection | Treatment |
|---|---|---|
| **Missing values** | `is.na(df)`, `sum(is.na(df))` | Delete rows, impute with mean/median/mode |
| **Outliers** | Boxplot, z-score `> 3` | Remove, cap, or transform |
| **Duplicates** | `duplicated(df)` | `df[!duplicated(df),]` |
| **Inconsistent values** | `unique(df$col)` | Standardize (e.g., "M"/"Male" → "Male") |
| **Wrong data types** | `class(df$col)` | Convert: `as.numeric()`, `as.factor()` |
| **Encoding errors** | visual inspection | Re-encode in correct format |

---

## MODULE 6 — Data Analytics with Python {#module6}

### 🔴 Q55. What is Pandas? What are its key data structures?

**Answer:** Pandas is a Python library for **data manipulation and analysis**. Built on top of NumPy.

```python
import pandas as pd
```

**Key data structures:**
| Structure | Description | Created by |
|---|---|---|
| **Series** | 1D labeled array | `pd.Series([1,2,3])` |
| **DataFrame** | 2D labeled table (rows + columns) | `pd.DataFrame({'A':[1,2],'B':[3,4]})` |

**Essential Pandas operations:**
```python
df = pd.read_csv('data.csv')   # Read CSV
df.head()                       # First 5 rows
df.info()                       # Data types, null counts
df.describe()                   # Statistical summary
df.shape                        # (rows, cols)
df.columns                      # Column names
df['col']                       # Select column (Series)
df[['col1','col2']]            # Select multiple columns

# Filtering
df[df['age'] > 30]
df.loc[0:5, 'name':'age']       # Label-based indexing
df.iloc[0:5, 0:3]              # Position-based indexing

# Handling missing values
df.isnull().sum()
df.dropna()
df.fillna(0)
df.fillna(df.mean())

# Grouping
df.groupby('city')['salary'].mean()

# Sorting
df.sort_values('salary', ascending=False)

# Adding column
df['tax'] = df['salary'] * 0.3

# Merging
pd.merge(df1, df2, on='id', how='inner')
```

---

### 🔴 Q56. What is NumPy? How is it different from Pandas?

**Answer:** NumPy (Numerical Python) = foundational library for **numerical computation** in Python. Uses N-dimensional arrays (ndarray) for fast mathematical operations.

```python
import numpy as np
```

| Feature | NumPy | Pandas |
|---|---|---|
| Data structure | ndarray | Series, DataFrame |
| Data type | Homogeneous (same type) | Heterogeneous |
| Labels | No labels (integer index) | Row/column labels |
| Use | Math, linear algebra | Data manipulation, analysis |

**Key NumPy operations:**
```python
a = np.array([1, 2, 3, 4, 5])
a.mean()      # 3.0
a.std()       # Standard deviation
a.sum()       # 15
a.min()       # 1
a.max()       # 5
a.shape       # (5,)

# Matrix operations
A = np.array([[1,2],[3,4]])
np.dot(A, A)           # Matrix multiplication
np.transpose(A)        # Transpose
np.linalg.inv(A)       # Inverse
np.linalg.det(A)       # Determinant

# Random
np.random.rand(3, 4)   # 3×4 random matrix (0 to 1)
np.random.randn(100)   # Normal distribution
np.linspace(0, 1, 50) # 50 equally spaced values from 0 to 1
```

---

### Q57. What is SciPy? How is it different from NumPy?

**Answer:** SciPy (Scientific Python) builds on NumPy and provides **advanced scientific and statistical computing functions**.

```python
from scipy import stats, optimize, signal
```

| Library | Focus |
|---|---|
| **NumPy** | Array operations, basic math |
| **SciPy** | Statistics, optimization, signal processing, integration |

**Key SciPy modules:**
```python
# Statistical tests
from scipy import stats
stats.ttest_ind(group1, group2)    # Independent t-test
stats.pearsonr(x, y)               # Pearson correlation + p-value
stats.normaltest(data)             # Test for normality
stats.chi2_contingency(table)      # Chi-squared test

# Descriptive statistics
stats.describe(data)               # All stats at once

# Distributions
stats.norm.pdf(x, mu, sigma)       # Normal distribution PDF
stats.norm.cdf(x, mu, sigma)       # CDF
```

---

### 🔴 Q58. What is Matplotlib? How do you create basic plots?

**Answer:** Matplotlib is Python's **foundational plotting library**. Creates static, animated, and interactive visualizations.

```python
import matplotlib.pyplot as plt
```

**1. Line Plot:**
```python
x = [1, 2, 3, 4, 5]
y = [10, 20, 15, 30, 25]
plt.plot(x, y, color='blue', marker='o', linestyle='--')
plt.title('Line Plot')
plt.xlabel('X Axis')
plt.ylabel('Y Axis')
plt.grid(True)
plt.show()
```

**2. Histogram:**
```python
import numpy as np
data = np.random.randn(1000)
plt.hist(data, bins=30, color='steelblue', edgecolor='black')
plt.title('Histogram')
plt.xlabel('Value')
plt.ylabel('Frequency')
plt.show()
```

**3. Bar Chart:**
```python
categories = ['A', 'B', 'C', 'D']
values = [25, 40, 35, 50]
plt.bar(categories, values, color=['red','green','blue','orange'])
plt.title('Bar Chart')
plt.show()

# Horizontal bar chart
plt.barh(categories, values)
```

**4. Pie Chart:**
```python
sizes = [30, 25, 20, 15, 10]
labels = ['Python', 'R', 'SQL', 'Excel', 'Other']
explode = (0.1, 0, 0, 0, 0)  # explode first slice
plt.pie(sizes, labels=labels, explode=explode, autopct='%1.1f%%', startangle=90)
plt.title('Tool Usage')
plt.show()
```

**5. Scatter Plot:**
```python
x = np.random.rand(50)
y = np.random.rand(50)
plt.scatter(x, y, color='coral', alpha=0.7, s=100)  # s = marker size
plt.title('Scatter Plot')
plt.show()
```

---

### 🔴 Q59. What is a Box Plot? What does it show?

**Answer:** A box plot (box-and-whisker plot) shows the **distribution and spread of data** and highlights outliers.

```python
data = [np.random.randn(100) for _ in range(5)]
plt.boxplot(data, labels=['A','B','C','D','E'])
plt.title('Box Plot')
plt.show()
```

**What each part shows:**
```
    |-------|
    |   Q3  | ← 75th percentile (upper quartile)
    |-------|
    |Median | ← 50th percentile (Q2)
    |-------|
    |   Q1  | ← 25th percentile (lower quartile)
    |-------|
       |
    --------  ← Whiskers extend to 1.5 × IQR
       
    *          ← Outliers (beyond 1.5 × IQR)
```

**IQR = Q3 - Q1** (Interquartile Range)
- **Lower fence** = Q1 - 1.5 × IQR
- **Upper fence** = Q3 + 1.5 × IQR
- Points beyond fences = **outliers** (plotted as dots)

---

### Q60. What is a Violin Plot? How is it different from a Box Plot?

**Answer:** A violin plot combines a **box plot** with a **kernel density estimate** — shows not just summary stats but the full distribution shape.

```python
import seaborn as sns
import pandas as pd

df = sns.load_dataset('tips')
sns.violinplot(x='day', y='total_bill', data=df)
plt.title('Violin Plot')
plt.show()
```

| Feature | Box Plot | Violin Plot |
|---|---|---|
| Shows median, IQR | Yes | Yes |
| Shows outliers | Yes | Not always |
| Shows distribution shape | No | Yes (density curve) |
| Useful for | Comparing groups | Comparing + seeing modality |

---

### 🔴 Q61. What is Seaborn? How is it different from Matplotlib?

**Answer:** Seaborn is a **high-level statistical visualization library** built on top of Matplotlib. Produces **aesthetically pleasing** statistical plots with minimal code.

```python
import seaborn as sns
```

| Feature | Matplotlib | Seaborn |
|---|---|---|
| Level | Low-level (full control) | High-level (simpler syntax) |
| Default aesthetics | Basic | Beautiful defaults |
| Statistical plots | Manual | Built-in (heatmaps, violin, pair plots) |
| Integration with Pandas | Indirect | Direct (accepts DataFrames) |
| Use case | Any plot, full customization | Statistical analysis plots |

**Common Seaborn plots:**
```python
# Distribution
sns.histplot(data=df, x='age', kde=True)
sns.kdeplot(data=df, x='age')

# Categorical
sns.boxplot(x='gender', y='salary', data=df)
sns.violinplot(x='gender', y='salary', data=df)
sns.barplot(x='gender', y='salary', data=df)
sns.stripplot(x='gender', y='salary', data=df)

# Relational
sns.scatterplot(x='age', y='salary', data=df, hue='gender')
sns.lineplot(x='year', y='sales', data=df)

# Comparison
sns.heatmap(df.corr(), annot=True, cmap='coolwarm')
sns.pairplot(df, hue='species')  # All variable combinations

# Regression
sns.regplot(x='age', y='salary', data=df)
sns.lmplot(x='age', y='salary', hue='gender', data=df)
```

---

### Q62. What is `sns.regplot()` and `sns.lmplot()`?

**Answer:**

- **`regplot()`** — Scatterplot with a linear regression line and **95% confidence interval** band
```python
sns.regplot(x='sqft', y='price', data=df)
# Shows: scatter points + regression line + shaded CI band
```

- **`lmplot()`** — Like `regplot()` but allows **faceting by categories** using `hue`, `col`, `row`
```python
sns.lmplot(x='sqft', y='price', hue='city', data=df)
# Shows separate regression lines for each city
```

The shaded band = **95% confidence interval** for the regression line.

---

### Q63. What are Multiple Plots in Matplotlib?

**Answer:** Use `plt.subplot()` or `plt.subplots()` to display multiple plots in one figure:

```python
# Method 1: subplot
plt.figure(figsize=(12, 4))

plt.subplot(1, 3, 1)  # 1 row, 3 columns, plot 1
plt.hist(data)
plt.title('Histogram')

plt.subplot(1, 3, 2)  # plot 2
plt.boxplot(data)
plt.title('Box Plot')

plt.subplot(1, 3, 3)  # plot 3
plt.scatter(x, y)
plt.title('Scatter')

plt.tight_layout()  # prevents overlap
plt.show()


# Method 2: subplots (preferred)
fig, axes = plt.subplots(2, 2, figsize=(10, 8))
axes[0,0].hist(data)
axes[0,1].boxplot(data)
axes[1,0].scatter(x, y)
axes[1,1].bar(categories, values)
plt.tight_layout()
plt.show()
```

---

### Q64. What is `plt.figure(figsize=(width, height))`?

**Answer:** `figsize=(w, h)` controls the **size of the figure** in inches.
- Default is (6.4, 4.8) inches
- For larger, clearer figures: `figsize=(12, 6)` or `figsize=(10, 10)` for square plots

```python
fig, ax = plt.subplots(figsize=(10, 6))
ax.plot(x, y)
```

---

## QUICK FORMULA CHEAT SHEET {#formulas}

### Regression Formulas

```
Simple Linear Regression: Ŷ = β₀ + β₁X

β₁ = Σ(Xᵢ - X̄)(Yᵢ - Ȳ) / Σ(Xᵢ - X̄)²
β₀ = Ȳ - β₁X̄

Residual: eᵢ = Yᵢ - Ŷᵢ
SSE = Σeᵢ² (Least Squares minimizes this)
SST = Σ(Yᵢ - Ȳ)²
SSR = SST - SSE

R² = SSR/SST = 1 - SSE/SST

Adjusted R² = 1 - [(1-R²)(n-1)/(n-p-1)]

Multiple Linear Regression: Ŷ = β₀ + β₁X₁ + β₂X₂ + ... + βₚXₚ
```

### Logistic Regression Formulas

```
Sigmoid: P(Y=1|X) = 1 / (1 + e^-z), where z = β₀ + β₁X₁ + ... + βₚXₚ

Logit: logit(p) = log(p / (1-p)) = z

Odds = p / (1-p)
Odds Ratio = e^βᵢ

Log-Loss = -(1/n) Σ [yᵢlog(p̂ᵢ) + (1-yᵢ)log(1-p̂ᵢ)]

Accuracy      = (TP + TN) / (TP + TN + FP + FN)
Precision     = TP / (TP + FP)
Recall        = TP / (TP + FN)
F1-Score      = 2 × Precision × Recall / (Precision + Recall)
```

### Time Series Formulas

```
AR(p):  Yₜ = c + φ₁Yₜ₋₁ + φ₂Yₜ₋₂ + ... + φₚYₜ₋ₚ + εₜ
MA(q):  Yₜ = μ + εₜ + θ₁εₜ₋₁ + θ₂εₜ₋₂ + ... + θqεₜ₋q
ARIMA(p,d,q): d-th differenced AR(p) + MA(q)

First Difference: ΔYₜ = Yₜ - Yₜ₋₁

ACF(k) = Correlation(Yₜ, Yₜ₋ₖ)

AIC = -2×log(L) + 2k
BIC = -2×log(L) + k×log(n)

RMSE = √[ (1/n) × Σ(Actual - Forecast)² ]
MAE  = (1/n) × Σ|Actual - Forecast|
MAPE = (100/n) × Σ|(Actual - Forecast)/Actual|
```

### Text Analytics Formulas

```
TF(t, d) = (Count of t in d) / (Total words in d)

IDF(t) = log( N / df(t) )
       Where N = total docs, df(t) = docs containing t

TF-IDF(t, d) = TF(t, d) × IDF(t)

Cosine Similarity(A, B) = (A · B) / (|A| × |B|)
```

### Descriptive Statistics Formulas

```
Mean = Σxᵢ / n

Variance (sample) = Σ(xᵢ - x̄)² / (n-1)

Standard Deviation = √Variance

IQR = Q3 - Q1
Lower Fence = Q1 - 1.5 × IQR
Upper Fence = Q3 + 1.5 × IQR
```

---

## MOST LIKELY VIVA QUESTIONS — Ranked

### MUST KNOW (100% will be asked):
1. What are the 6 phases of Data Analytics Lifecycle? Explain each briefly.
2. What is the regression equation for Simple Linear Regression? Explain β₀ and β₁.
3. What is the Least Squares method? What does it minimize?
4. What is R-squared? Give the formula and interpretation.
5. What is Logistic Regression? What is the Sigmoid function?
6. What is the Logit / Log-Odds? Write the formula.
7. What is TF-IDF? Write the formula and explain with an example.
8. What is ARIMA? What do p, d, q stand for?
9. What is ACF and PACF? What do they tell you?
10. What is Sentiment Analysis? What are its types?

### VERY LIKELY:
11. What is the difference between Linear and Logistic Regression?
12. What is Adjusted R-squared? Why use it instead of R-squared?
13. What is stepwise regression?
14. What is stationarity? How do you achieve it?
15. What are AR and MA models? Write their equations.
16. What is a confusion matrix? What are Precision and Recall?
17. What is Pandas? What are DataFrames?
18. What is Matplotlib? Show a histogram/bar chart.
19. What is Seaborn? How is it different from Matplotlib?
20. What is EDA? What is "dirty data"?

### BONUS (shows depth):
21. What is the Box-Jenkins methodology?
22. What is AIC and BIC? How are they used in model selection?
23. What is Cross-Validation?
24. What is the difference between Stemming and Lemmatization?
25. What is Cosine Similarity in text analytics?
26. What is LDA (Latent Dirichlet Allocation)?
27. What is a Violin Plot and how does it differ from a Box Plot?
28. What is a GLM (Generalized Linear Model)?
29. What is `sns.regplot()` and what does the shaded band represent?
30. What is ETLT and how is it different from ETL?

---

## QUICK CONCEPT COMPARISON TABLE

| Topic | Simple Version | Formula |
|---|---|---|
| Simple LR | Y = line fitted through data | Ŷ = β₀ + β₁X |
| Multiple LR | Y = line fitted using multiple X's | Ŷ = β₀ + β₁X₁ + ... + βₚXₚ |
| Logistic Regression | P(event) = S-curve | P = 1/(1+e^-z) |
| R-squared | % of Y variation explained | SSR/SST |
| TF-IDF | Word importance score | TF × log(N/df) |
| ARIMA(p,d,q) | Time series model | p=AR, d=difference, q=MA |
| ACF | Correlation with own past | Correlation(Yₜ, Yₜ₋ₖ) |
| Precision | Correct positive predictions | TP/(TP+FP) |
| Recall | How many actual positives caught | TP/(TP+FN) |
| IQR | Middle 50% spread | Q3 - Q1 |

---

*Document prepared for: DAV — Data Analytics and Visualization Viva*
*Mumbai University | T.E. Semester VI*
