# DA-IBM — Python Data Analysis Projects

A collection of data analysis projects completed as part of the IBM/Skills Network "Python Project for Data Science" and "Data Analysis with Python" courses. Each notebook covers a different stage of a typical data analysis workflow: data extraction, cleaning, exploratory analysis, and predictive modeling.

## Contents

| Notebook | Topic | Techniques |
|---|---|---|
| `Revenue_Data_and_Building_a_Dashboard_Sergey_Lyskin.ipynb` | Stock price & revenue dashboard (Tesla vs GameStop) | API data extraction (`yfinance`), web scraping (`BeautifulSoup`), data visualization (`matplotlib`) |
| `House_Sales_in_King_Count_USA_Sergey_Lyskin.ipynb` | House price prediction (King County, USA) | Data wrangling, exploratory data analysis, linear regression, pipelines, model evaluation (`pandas`, `seaborn`, `scikit-learn`) |

---

## 1. Revenue Data & Building a Dashboard (Tesla vs GameStop)

A project for extracting and visualizing financial data: historical stock prices are pulled via the `yfinance` API library, while quarterly revenue data is obtained through web scraping with `BeautifulSoup`. The result is a comparative "stock price + revenue" dashboard for two companies.

**What it does:**
1. Extracts stock price history via `yfinance` (`Ticker.history(period="max")`) for Tesla (`TSLA`) and GameStop (`GME`)
2. Extracts revenue data via web scraping (`requests` + `BeautifulSoup`): locating tables, parsing `<tr>`/`<td>` rows, assembling into a `pandas.DataFrame`
3. Cleans the data — strips `$` and `,` from the `Revenue` column, drops empty/null values
4. Builds two synchronized charts (stock price and revenue over time) per company

**Tech stack:** `pandas` · `yfinance` · `requests` · `BeautifulSoup` · `matplotlib`

---

## 2. House Sales in King County, USA

A data analyst project for a Real Estate Investment Trust: analyzing and predicting residential house prices in King County (which includes Seattle), based on a dataset of homes sold between May 2014 and May 2015.

**What it does:**
1. **Data wrangling** — loads the dataset, inspects data types, drops irrelevant columns (`id`, `Unnamed: 0`), handles missing values in `bedrooms`/`bathrooms` (mean imputation)
2. **Exploratory data analysis** — value counts by number of floors, boxplot of price by waterfront view, regression plot of price vs. `sqft_above`, correlation analysis
3. **Model development** — fits linear regression models using single and multiple features; builds a `Pipeline` combining `StandardScaler`, `PolynomialFeatures`, and `LinearRegression`
4. **Model evaluation and refinement** — train/test split, Ridge regression with regularization, polynomial transform + Ridge regression, R² comparison

**Tech stack:** `pandas` · `numpy` · `seaborn` · `matplotlib` · `scikit-learn`

**Dataset source:** [Kaggle — House Sales in King County, USA](https://www.kaggle.com/harlfoxem/housesalesprediction)

---

## How to run

```bash
pip install pandas numpy matplotlib seaborn scikit-learn yfinance requests beautifulsoup4 html5lib lxml
jupyter notebook
```

Then open either notebook from the Jupyter file browser.

## Source

Both projects were completed as part of IBM/Skills Network courses on Coursera ("Python Project for Data Science" and "Data Analysis with Python").
