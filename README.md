# Predicting Apartment Prices in Mexico City — Regression Pipeline (Ridge)

This project builds an end-to-end **data wrangling + regression** workflow to predict **apartment prices (USD)** in **Mexico City**. It includes data cleaning, feature engineering, exploratory analysis, a strong baseline, and a production-style modeling pipeline using **One-Hot Encoding + Imputation + Ridge Regression**.

---

## Demo / Evidence
- **Project PDF (notebook export):** `Predicting Apartment Prices in Mexico.pdf`
- **Repository:** this GitHub repository

> The PDF contains the full workflow and outputs (histogram, scatter plot, map visualization, model pipeline, and feature-importance chart).

---

## Problem Statement
Real estate prices vary widely across neighborhoods and are influenced by size and location. The objective is to:

1. Build a clean dataset of Mexico City apartment listings.
2. Explore relationships between **area, location, borough**, and **price**.
3. Train a regression model to generate price predictions for unseen listings.
4. Communicate drivers of price using feature importance.

---

## Data Source
- Multiple CSV files (e.g., `mexico-city-real-estate-*.csv`) combined into a single dataset.
- Target: `price_aprox_usd`
- Core features: `surface_covered_in_m2`, `lat`, `lon`, `borough`

---

## Methodology

### 1) Data Wrangling
A `wrangle()` function prepares and cleans each CSV before concatenation. Typical steps include:
- Filtering to Mexico City apartments under a price threshold
- Trimming extreme property sizes using quantiles
- Splitting `"lat-lon"` into numeric `lat` and `lon`
- Creating `borough` from the location hierarchy
- Dropping high-missing columns and leaky price-related columns

### 2) Exploratory Data Analysis (EDA)
Key EDA visuals and checks:
- Histogram: distribution of apartment prices
- Scatter: **Price vs. Area**
- Map visualization: apartments plotted by location, colored by price

### 3) Baseline
A baseline model predicts the **mean training price** for every listing, evaluated using **Mean Absolute Error (MAE)**.

### 4) Modeling (Pipeline)
The final model is a scikit-learn pipeline:
- `OneHotEncoder` (categorical handling for borough)
- `SimpleImputer` (missing value handling)
- `Ridge` regression (regularized linear model)

### 5) Interpretation
Feature importance is derived from the trained Ridge coefficients to identify which inputs most strongly influence price.

---

## Results (Baseline from this run)
- **Mean apartment price (train):** 54,246.53 USD  
- **Baseline MAE:** 17,239.94 USD  

> Results may vary depending on the dataset snapshot and runtime environment.

---

## Repository Contents
Typical contents for this repo:
- `Predicting Apartment Prices in Mexico.pdf` — exported notebook (recommended artifact for reviewers)
- `*.ipynb` — notebook(s) used to build and evaluate the model (if included)
- `README.md` — this file

---

## How to Reproduce (Optional)
If the notebook(s) and data are included in this repository, you can reproduce the work locally.

### 1) Create and activate a Python environment
```bash
python -m venv .venv

# Windows:
.venv\Scripts\activate

# macOS/Linux:
source .venv/bin/activate
```
2) Install dependencies
bash
Copy code
pip install pandas numpy matplotlib seaborn plotly scikit-learn category_encoders ipywidgets
3) Run the notebook
bash
Copy code
jupyter lab
Then open the notebook and run cells top-to-bottom.

Key Skills Demonstrated
Data wrangling and feature engineering (filters, quantiles, parsing latitude/longitude)

Regression modeling with scikit-learn pipelines (encoding + imputation + Ridge)

Baseline evaluation using MAE

Visual communication (histograms, scatter plots, map visualization)

Model interpretability via coefficient-based feature importance

Clean, reproducible notebook workflow

Author
Nouhan Doumbouya
