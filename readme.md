# Econometric Analysis of Inflation Dynamics & Market Volatility

![Python](https://img.shields.io/badge/Python-3.9%2B-blue)
![Status](https://img.shields.io/badge/Status-Completed-green)
![Domain](https://img.shields.io/badge/Domain-Quant%20Research-orange)

## 📌 Project Overview
This project presents a rigorous pseudo-replication and extension of macroeconomic time-series research, applying econometric models to analyze the **Malaysian economy (1990–2006)**.

The primary objective was to investigate the structural relationship between **Inflation (CPI)** and **Economic Growth (GDP)**, while modeling the volatility of market indicators using **GARCH(1,1)** processes. This study tests the hypothesis of whether high inflation regimes negatively impact economic growth and quantifies the persistence of volatility shocks in the region.

## 🛠 Technical Stack & Libraries
* **Language:** Python (Jupyter Notebooks)
* **Statistical Modeling:** `statsmodels` (OLS, HAC), `arch` (GARCH)
* **Data Engineering:** `pandas` (Merging, Null Handling), `numpy`
* **Visualization:** `matplotlib`, `seaborn`
* **Key Tests:** Augmented Dickey-Fuller (Stationarity), Jarque-Bera (Normality), Heteroskedasticity Tests.

## 📊 Methodology
The research pipeline is divided into two distinct stages: Data Engineering and Econometric Modeling.

### 1. Data Pipeline (`DataCleaning.ipynb`)
Raw economic indicators were ingested from World Bank datasets and normalized for analysis:
* **Ingestion:** Aggregated multiple CSV sources including *Consumer Price Index*, *Liquid Liabilities (M2)*, and *GDP Growth*.
* **Cleaning:** Implemented logic to handle missing values (NaNs) and align disparate time-series frequencies.
* **Transformation:** Merged separate indicators into a consolidated time-series dataset (`malaysia_consolidated_data_partial.csv`) indexed by Year.

### 2. Econometric Analysis (`updated.ipynb`)
* **Stationarity Testing:** Applied **Augmented Dickey-Fuller (ADF)** tests to confirm all variables were $I(0)$ or $I(1)$ before modeling.
* **Structural Analysis (OLS):**
    * Modeled GDP Growth as a function of Inflation, Money Supply (M2), and Remittances.
    * **Key Finding:** Inflation ($p < 0.05$) showed a negative coefficient (**-0.0395**), confirming that a 1% increase in inflation correlates with a ~0.04% contraction in GDP.
* **Robustness Checks:** Implemented **HAC (Heteroskedasticity and Autocorrelation Consistent)** standard errors to control for serial correlation.
* **Volatility Modeling (GARCH 1,1):**
    * Modeled the conditional variance of residuals.
    * **Result:** High persistence ($\alpha + \beta \approx 0.98$), indicating that market shocks in this period were long-lasting rather than transient.

## 📂 File Structure
```bash
├── data/
│   ├── raw/                        # Original World Bank CSVs
│   └── malaysia_consolidated.csv   # Cleaned dataset for modeling
├── notebooks/
│   ├── DataCleaning.ipynb          # Data ingestion and cleaning pipeline
│   └── Analysis_Model.ipynb        # OLS regression and GARCH modeling
├── report/
│   └── Research_Report.pdf         # Full academic report with literature review
└── README.md                       # Project documentation