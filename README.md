# DA-IBM - Python Project - web scraping and parsing
IBM Data Analyst Certification

# Revenue & Stock Price Dashboard — Tesla vs GameStop

A project for extracting and visualizing financial data: historical stock prices are pulled via the `yfinance` API library, while quarterly revenue data is obtained through web scraping with `BeautifulSoup`. The result is a comparative "stock price + revenue" dashboard for two companies: Tesla and GameStop.

## Contents

- `Revenue_Data_and_Building_a_Dashboard.ipynb` — main notebook with the full analysis pipeline

## What the project does

1. **Stock price extraction** — via `yfinance` (`Ticker.history(period="max")`) for Tesla (`TSLA`) and GameStop (`GME`)
2. **Revenue data extraction** — web scraping an HTML page (`requests` + `BeautifulSoup`): locating the correct table, parsing `<tr>`/`<td>` rows, and assembling the results into a `pandas.DataFrame`
3. **Data cleaning** — stripping `$` and `,` characters from the `Revenue` column, dropping empty/null values
4. **Visualization** — two synchronized charts (stock price and revenue over time) for each company

## Tech stack

`Python` · `pandas` · `yfinance` · `requests` · `BeautifulSoup` · `matplotlib`

## How to run

```bash
pip install -r requirements.txt
jupyter notebook Revenue_Data_and_Building_a_Dashboard.ipynb
```

## Sample code

```python
tesla = yf.Ticker("TSLA")
tesla_data = tesla.history(period="max")
tesla_data.reset_index(inplace=True)
```

```python
soup = BeautifulSoup(html_data, "html5lib")
tesla_revenue = pd.DataFrame(columns=["Date", "Revenue"])

for row in soup.find_all("tbody")[1].find_all("tr"):
    col = row.find_all("td")
    tesla_revenue = pd.concat([
        tesla_revenue,
        pd.DataFrame({"Date": [col[0].text], "Revenue": [col[1].text]})
    ], ignore_index=True)
```

## Key takeaways

- Demonstrates two different approaches to data extraction: via a ready-made API (`yfinance`) versus web scraping (`BeautifulSoup`) — in practice, the choice depends on whether the needed data is available through an official source
- Produces a clear dashboard comparing a company's stock price trend against its actual revenue over the same period

## Source

This project was completed as part of the IBM/Skills Network course "Python Project for Data Science."
