# Sustainable Fashion Business Analytics

## The Influence of Sustainable Fashion Consciousness on Consumer Purchase Behavior

An MSc Business Analytics project investigating the factors that influence sustainable fashion purchasing decisions, willingness to pay a premium, and consumer segmentation.

The project combines **psychometric analysis, exploratory data analysis, inferential statistics, econometric regression, supervised machine learning, and unsupervised customer segmentation**.

---

## Project Overview

The fashion industry faces a persistent **attitude–behavior gap**: consumers may express strong environmental and sustainability concerns, but these attitudes do not always translate into sustainable purchasing behavior.

This study examines five key explanatory constructs:

- **SFC — Sustainable Fashion Consciousness**
- **GS — Greenwashing Skepticism**
- **SI — Social Identity Signaling**
- **ELT — Eco-Label Trust**
- **PF — Practical Filtering / Purchasing Barriers**

Two key outcome constructs are also analyzed:

- **SPB — Sustainable Purchase Behavior**
- **WTP — Willingness to Pay a Premium**

The analysis uses a primary survey dataset containing **200 respondents** and 21 Likert-scale psychometric items across seven latent constructs.

---

## Research Objectives

The project aims to:

1. Examine the relationship between sustainable fashion consciousness and sustainable purchase behavior.
2. Identify the factors associated with consumers' willingness to pay a premium for sustainable fashion.
3. Investigate the role of greenwashing skepticism and eco-label trust.
4. Assess the influence of social identity signaling and practical purchasing barriers.
5. Identify meaningful consumer segments based on sustainability-related attitudes and behaviors.
6. Develop predictive models for identifying consumers with high willingness to pay.
7. Translate analytical findings into actionable business recommendations.

---

## Analytical Framework

### Psychometric Constructs

Each construct is measured using three standardized reflective survey items on a five-point Likert scale:

| Construct | Code | Items |
|---|---|---|
| Sustainable Fashion Consciousness | `SFC` | 3 |
| Greenwashing Skepticism | `GS` | 3 |
| Social Identity Signaling | `SI` | 3 |
| Eco-Label Trust | `ELT` | 3 |
| Practical Filtering | `PF` | 3 |
| Sustainable Purchase Behavior | `SPB` | 3 |
| Willingness to Pay Premium | `WTP` | 3 |

### Likert Scale

- `1` = Strongly Disagree
- `2` = Disagree
- `3` = Neither Agree nor Disagree
- `4` = Agree
- `5` = Strongly Agree

---

## Methodology

The notebook follows a quantitative business analytics workflow:

### 1. Data Preparation

- Dataset ingestion using Pandas
- Structural inspection
- Missing-value audit
- Demographic standardization
- Likert-scale encoding
- Construct-score generation

### 2. Reliability and Construct Validation

The project evaluates:

- Cronbach's Alpha
- Kaiser-Meyer-Olkin (KMO) measure
- Bartlett's Test of Sphericity
- Principal Component Analysis (PCA)

Key validation results from the compiled notebook:

- **Overall Cronbach's Alpha: 0.886**
- **KMO: 0.842**
- **Bartlett's Test: χ² = 2871.24, df = 210, p < 0.001**

These results support strong internal consistency and factorability of the survey instrument.

### 3. Exploratory Data Analysis

The notebook examines:

- Sample demographics
- Construct distributions
- Mean and median
- Standard deviation
- Skewness and kurtosis
- Shapiro-Wilk normality testing
- Correlation structure
- Distribution visualizations

### 4. Inferential Statistics

Demographic differences are examined using:

- Independent-samples t-tests
- Mann-Whitney U tests
- One-way ANOVA
- Kruskal-Wallis tests
- Cohen's d effect sizes

### 5. Econometric Regression

Three Ordinary Least Squares (OLS) models are specified.

#### Model 1 — Willingness to Pay

Predicts `WTP` using:

`GS + ELT + SFC + SI + PF`

The model explains approximately **26.9% of the variance in WTP (R² = 0.269)**.

In the estimated model:

- Greenwashing Skepticism was positively associated with WTP (`p = 0.018`)
- Eco-Label Trust was positively associated with WTP (`p = 0.015`)

#### Model 2 — Sustainable Purchase Behavior

Predicts `SPB` using:

`SFC + GS + SI + ELT + PF`

The model achieved **R² = 0.076**.

Within the estimated model, Practical Filtering was statistically significant (`p = 0.037`), while the other individual predictors were not statistically significant at the 5% level.

#### Model 3 — Value–Action Gap

Predicts `SPB` using:

`SFC + WTP + PF + ELT`

The model achieved **R² = 0.091**.

- WTP was positively associated with SPB (`p = 0.004`)
- Practical Filtering was statistically significant (`p = 0.026`)
- SFC was not statistically significant (`p = 0.165`)

Together, these results illustrate the project's central **value–action gap**: sustainability consciousness alone does not necessarily translate directly into purchasing behavior.

---

## Econometric Diagnostics

The notebook includes diagnostic testing for:

- Multicollinearity using Variance Inflation Factor (VIF)
- Heteroscedasticity using Breusch-Pagan and White tests
- Autocorrelation using Durbin-Watson
- Residual normality using Jarque-Bera
- Normal Q-Q plots

For Model 1:

- Breusch-Pagan: `p = 0.7715`
- White test: `p = 0.0040`
- Durbin-Watson: `1.87`
- Jarque-Bera: `p = 0.1220`

The results demonstrate why multiple diagnostic tests are required rather than relying on a single assumption test.

---

## Machine Learning

The project extends traditional statistical analysis with predictive machine learning.

### Target Variable

`High_WTP` is defined as:

- `1` = WTP ≥ 3.0
- `0` = WTP < 3.0

Among the 200 respondents:

- **119 (59.5%)** were classified as High WTP
- **81 (40.5%)** were classified as lower WTP

### Models

Two classification algorithms are evaluated:

- Random Forest Classifier
- Regularized Logistic Regression

### Validation

A **5-fold stratified cross-validation** framework is used.

| Model | Cross-Validated ROC-AUC |
|---|---:|
| Random Forest | **0.772 ± 0.074** |
| Logistic Regression | **0.742 ± 0.062** |

Random Forest produced the stronger predictive performance.

### Random Forest Test Performance

On the held-out test set:

- Accuracy: **0.66**
- High-WTP precision: **0.71**
- High-WTP recall: **0.73**
- High-WTP F1-score: **0.72**

### Feature Importance

The Random Forest model identified the following relative feature importance:

| Feature | Importance |
|---|---:|
| Eco-Label Trust (`ELT`) | 29.8% |
| Greenwashing Skepticism (`GS`) | 29.5% |
| Social Identity Signaling (`SI`) | 22.3% |
| Sustainable Fashion Consciousness (`SFC`) | 10.6% |
| Practical Filtering (`PF`) | 7.8% |

---

## Customer Segmentation

K-Means clustering is used to identify consumer archetypes from standardized construct scores.

The analysis evaluates candidate cluster solutions using:

- Elbow Method
- Within-cluster inertia
- Silhouette coefficient
- PCA-based two-dimensional visualization
- Cluster-level demographic profiling
- Multi-attribute persona analysis

### Identified Consumer Personas

The analysis produced three principal consumer segments:

| Persona | Description | Respondents | Share |
|---|---|---:|---:|
| Persona 1 | Committed Advocates — High WTP & High Trust | 79 | 39.5% |
| Persona 2 | Low-Involvement / Detached Buyers | 51 | 25.5% |
| Persona 3 | Skeptical & Price-Sensitive Conscious Buyers | 70 | 35.0% |

These segments demonstrate that sustainable-fashion consumers should not be treated as a single homogeneous market.

---

## Key Empirical Findings

The correlation analysis identified several important relationships:

- **Greenwashing Skepticism ↔ Eco-Label Trust:** `r = 0.722`, `p < 0.001`
- **Eco-Label Trust ↔ WTP:** `r = 0.483`, `p < 0.001`
- **Greenwashing Skepticism ↔ WTP:** `r = 0.469`, `p < 0.001`
- **Sustainable Fashion Consciousness ↔ Sustainable Purchase Behavior:** `r = 0.140`

The relatively weak relationship between SFC and SPB provides empirical evidence consistent with the project's **attitude–behavior gap**.

---

## Business Implications

The analysis suggests several practical implications for sustainable fashion brands:

### 1. Build Verifiable Trust

Eco-label trust is one of the strongest predictors of willingness to pay. Brands should use credible, verifiable certifications and provide transparent evidence behind sustainability claims.

### 2. Reduce Greenwashing Concerns

Consumers who are more skeptical of sustainability claims may still demonstrate stronger willingness to pay when credible evidence is available.

Marketing should therefore emphasize:

- Evidence
- Traceability
- Third-party certification
- Supply-chain transparency
- Measurable sustainability outcomes

### 3. Segment Consumers

Different consumer groups require different strategies rather than a single sustainability message.

For example:

- **Committed Advocates:** Premium products, loyalty programmes, advocacy campaigns
- **Skeptical & Price-Sensitive Buyers:** Transparent claims, value communication, accessible pricing
- **Low-Involvement Buyers:** Simple messaging, convenience, product visibility and low-friction sustainable choices

### 4. Address the Value–Action Gap

High sustainability consciousness does not automatically produce high purchasing behavior.

Brands should reduce practical friction through:

- Competitive pricing
- Wider product availability
- Attractive design
- Convenient purchasing
- Clear product information

---

## Technologies and Libraries

The notebook is implemented in Python using:

- Python
- Pandas
- NumPy
- SciPy
- Statsmodels
- Scikit-learn
- Matplotlib
- Seaborn

The analysis includes statistical modelling, dimensionality reduction, clustering and machine learning.

---

## Repository Structure

```text
.
├── README.md
├── sustainable_fashion_business_analytics.ipynb
└── Untitled form.csv
```

> **Data note:** The survey dataset contains primary respondent data. If the repository is made public, ensure that the dataset is appropriately anonymized and that its publication is permitted under the applicable research ethics and data-protection requirements.

---

## Running the Notebook

### 1. Clone the repository

```bash
git clone <your-repository-url>
cd <your-repository-folder>
```

### 2. Install dependencies

```bash
pip install pandas numpy scipy statsmodels scikit-learn matplotlib seaborn jupyter
```

### 3. Launch Jupyter Notebook

```bash
jupyter notebook
```

Open:

```text
sustainable_fashion_business_analytics.ipynb
```

### 4. Dataset Location

The notebook expects the primary dataset to be available as:

```text
Untitled form.csv
```

in the working directory.

---

## Research Framework

The overall analytical architecture can be summarized as:

```text
Sustainable Fashion Consciousness
                │
                ├──────────────┐
                │              │
                ▼              ▼
       Greenwashing       Social Identity
        Skepticism           Signaling
                │              │
                └──────┬───────┘
                       │
                       ▼
                Eco-Label Trust
                       │
                       ▼
             Willingness to Pay
                       │
                       ▼
          Sustainable Purchase
                Behavior
                       ▲
                       │
              Practical Filtering
          (Price / Availability /
               Style Barriers)
```

---

## Academic Context

**Programme:** MSc Business Analytics  
**Module:** BUSI 1783 — Business Analytics Project  
**Institution:** University of Greenwich / QA Higher Education  
**Project Date:** September 2026  
**Sample Size:** N = 200

The project uses a quantitative research design and combines classical statistical inference with predictive and segmentation analytics.

---

## Author

**MSc Business Analytics Candidate**

This repository contains the analytical notebook and supporting documentation for the Sustainable Fashion Business Analytics project.
