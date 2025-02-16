# Options_Analysis

## Description
This package aims to use historical option and stock prices to evaluate the performance of various models. Historical and current stock prices for a given ticker are pulled from [Alpha Vantage](https://www.alphavantage.co/) and [Questrade API](https://www.questrade.com/api), respectively. Current option prices also come from the Questrade API. Historical option prices, due to their lesser availability, were obtained from [Discount Option Data]( https://discountoptiondata.com/). Currently, I am only using option data from 2016, as most options go out for a maximum of 4 years.

This package is currently only concerned with the selling of options. In other words, it is trying to deduce which thetas are worth the risk for tickers of low volatility. The scope of this package can easily be expanded to include all combinations of option strategies.


## Folders
- **data**:
  - *adjusted_daily_closing*: Daily closing prices of various stock tickers obtained from Alpha Vantage adjusted for forward/reverse splits. To ensure training data remains constant, a local history is kept.
  
  - *dividends*: For each ticker symbol in local history, two files can be created.
      - "ticker.csv" contains the start and end dates of each dividend period, as well as amount paid. Note that "div_start" is the ex-dividend date for the previous dividend.
      - "ticker_ts.csv" contains the contribution to total price due to dividends as a time series. For each day on record, a dividend contribution is calculated.
      
  - *questrade_data*: Unadjusted option data scraped from Questrade API. Recorded prices may not represent "end of day" prices as snapshots are taken upon execution of scraping script.
  
  - *adjusted_options*: Adjusted historical option data obtained from Discount Option Data and used for training of model. Prices are end of day as indicated on their website.


- **results**: This folder contains analyzed performance of different call and put option pairs for a given ticker on a given date.


## Dependencies
- python
  - numpy
  - pandas
  - plotly
  - numba
  - questrade_api
  - tqdm
