# Market Momentum Backtester

\# Market Screening Backtester



A backtesting engine that tests whether a simple technical screen —

"hold stocks trading above their 50-day moving average" — beats

buy-and-hold on a basket of US large-cap equities.



Built from scratch with pandas and yfinance, with deliberate attention

to the biases that make backtests lie.



\## Result



Tested on 10 large-cap US stocks, 2015–2024, rebalanced monthly:



| Metric | Screen (monthly) | Buy \& hold |

|---|---|---|

| Total return | 3.96x | 4.89x |

| CAGR | 17.4% | 19.5% |

| Volatility | 18.3% | 18.2% |

| Sharpe | 0.95 | 1.07 |

| Max drawdown | −28.9% | −31.0% |



\*\*The screen underperforms.\*\* It gave up 2.1 points of annual return to

gain 2.1 points of drawdown protection — roughly a 1:1 trade, and a bad

one. Buy-and-hold wins on Sharpe, so it delivered more return per unit

of risk.



This is the expected result. Trend-following rules exit after a decline

has already begun and re-enter after the recovery is underway, which is

punishing in a decade of sharp V-shaped recoveries (2018, 2020, 2022).

A simple screen beating buy-and-hold would more likely indicate a bug

than an edge.



\## Method



1\. Download adjusted OHLCV data via `yfinance`

2\. Compute a 50-day rolling mean per ticker

3\. Generate a boolean signal: price > moving average

4\. Lag the signal by one day to prevent lookahead bias

5\. Equal-weight across all passing tickers

6\. Rebalance monthly rather than daily to control turnover

7\. Compare against equal-weight buy-and-hold on CAGR, Sharpe and drawdown



\## Known limitations



\- \*\*Survivorship bias.\*\* The ticker universe is chosen from companies

&#x20; that exist today, so failed companies are absent by construction.

&#x20; Both strategies are flattered; the comparison between them still holds.

\- \*\*No transaction costs.\*\* Monthly rebalancing produces meaningful

&#x20; turnover that would erode returns in practice.

\- \*\*Single parameter set.\*\* The 50-day window is conventional, not

&#x20; optimised — deliberately, to avoid overfitting to this sample.



\## Running it



```bash

pip install -r requirements.txt

jupyter notebook backtester.ipynb

```



Or open `backtester.ipynb` directly on GitHub to see the code and

output without running anything.

\# Market Screening Backtester



A backtesting engine that tests whether a simple technical screen —

"hold stocks trading above their 50-day moving average" — beats

buy-and-hold on a basket of US large-cap equities.



Built from scratch with pandas and yfinance, with deliberate attention

to the biases that make backtests lie.



\## Result



Tested on 10 large-cap US stocks, 2015–2024, rebalanced monthly:



| Metric | Screen (monthly) | Buy \& hold |

|---|---|---|

| Total return | 3.96x | 4.89x |

| CAGR | 17.4% | 19.5% |

| Volatility | 18.3% | 18.2% |

| Sharpe | 0.95 | 1.07 |

| Max drawdown | −28.9% | −31.0% |



\*\*The screen underperforms.\*\* It gave up 2.1 points of annual return to

gain 2.1 points of drawdown protection — roughly a 1:1 trade, and a bad

one. Buy-and-hold wins on Sharpe, so it delivered more return per unit

of risk.



This is the expected result. Trend-following rules exit after a decline

has already begun and re-enter after the recovery is underway, which is

punishing in a decade of sharp V-shaped recoveries (2018, 2020, 2022).

A simple screen beating buy-and-hold would more likely indicate a bug

than an edge.



\## Method



1\. Download adjusted OHLCV data via `yfinance`

2\. Compute a 50-day rolling mean per ticker

3\. Generate a boolean signal: price > moving average

4\. Lag the signal by one day to prevent lookahead bias

5\. Equal-weight across all passing tickers

6\. Rebalance monthly rather than daily to control turnover

7\. Compare against equal-weight buy-and-hold on CAGR, Sharpe and drawdown



\## Known limitations



\- \*\*Survivorship bias.\*\* The ticker universe is chosen from companies

&#x20; that exist today, so failed companies are absent by construction.

&#x20; Both strategies are flattered; the comparison between them still holds.

\- \*\*No transaction costs.\*\* Monthly rebalancing produces meaningful

&#x20; turnover that would erode returns in practice.

\- \*\*Single parameter set.\*\* The 50-day window is conventional, not

&#x20; optimised — deliberately, to avoid overfitting to this sample.



\## Running it



```bash

pip install -r requirements.txt

jupyter notebook backtester.ipynb

```



Or open `backtester.ipynb` directly on GitHub to see the code and

output without running anything.

