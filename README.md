# Stock-Price-Prediction-short-term-
Using historical stock data (Tesla) to predict the next day's closing price.

The goal is to build a short-term predictive model that estimates the next day's closing stock price based on past daily trading data.
I Tesla stock (ticker: TSLA) and apply regression modeling to forecast the next day's closing price.
This shows how past prices and volumes influence the next day's price.

Dataset:
Source: Yahoo Finance
Retrived using: yfinance
Ticker: TSLA (Tesla Inc.)
Date Range: 1 year from today (auto updated using python)

Python
data handling: pandas,numpy
visualization: matplotlib, seaborn
stock price retrival: yfinance
regression modeling and evaluation: scikit-learn

Tesla stock data was downloaded for the past 365 days
Data was cleaned and reset with datetime index
To improve predictive performance 5 day and 10 day moving averages, daily returns, standard deviation of returns and previous day's close were added
The final feature set was :
['Open', 'High', 'Low', 'Close', 'Volume', 'MA5', 'MA10', 'Returns', 'Volatility', 'Prev_Close']

shift(-1) method was used to create Next_Close column - for the value we intend to predict

Data Visualization:
-Line chart of Tesla's price over the year
-Correlation heatmap of all the features vs Next_Close
These confirmed that moving averages and previous prices were positively correlated with the next day's closing price.

Model used:
Model: RandomForestRegressor from sklearn.ensemble
-Random forests are good at capturing non-linear patterns and interactions between features.
Scaling : features were standardised using StandardScaler

Result:
MAE = 10.11
RSME =13.85
R^2 Score = 0.8794

-The model follows general price trends but doesn't capture extreme highs/lows perfectly — which is expected due to market volatility.
-R² shows decent performance, suggesting that historical features contain predictive information for short-term movement.
-However, the stock market is influenced by many external factors (e.g., news, events) that aren’t captured here.

A line plot comparing the actual vs predicted closing prices showed that:
-The model correctly follows general up/down movements.
-Predictive power is best during stable price periods and weaker during high volatility.

Adding technical indicators (moving averages, volatility, lag features) improved accuracy.
Random Forest outperforms linear models by capturing complex patterns.
Prediction of next-day stock price is inherently noisy, and perfect accuracy is not realistic — but this model gives us useful approximations.
