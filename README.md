JPX Tokyo Stock Exchange Prediction

Final report

Runqi Wang
1. Problem Statement

Success in any financial market requires one to identify solid investments. When a stock or derivative is undervalued, it makes sense to buy. If it's overvalued, perhaps it's time to sell. While these finance decisions were historically made manually by professionals, technology has ushered in new opportunities for retail investors. Data scientists, specifically, may be interested to explore quantitative trading, where decisions are executed programmatically based on predictions from trained models. In this project, for JPX more than 2000 stocks, the best performance portfolios will be generated. 

2. Data Wrangling

This dataset contains historic data for a variety of Japanese stocks and options. To view the data, the original Kaggle SQLite tables provided by Japan Exchange Group, or the import report using the Kaggle API click on the links below:

Kaggle Dataset

The main purpose of this project is to rank all stocks’ performance. So the simple plan for this project is:

Do research about stock_price.csv in train file

Find out features’ relationship in stock_price

Import more features based on old features

Train a model of all features 

Apply the model on stock_price.csv in test file

After a missing data check, we find there is a lot of data missing in one day at 2020-10-01. The reason is The Failure of Equity Trading System on October 1, 2020. 
Also we did search for one example stock whose securitiesCode is 7974 Nintendo Co., Ltd. We find features of open, high, low and close are getting the same trend. Considering features high and low can be very tricky. They are caused by certain people for their own purpose. So we are going to use Open and Close features for prediction. 

ExpectedDividend: Expected dividend value for ex-right date. This value is recorded 2 business days before the ex-dividend date.
SupervisionFlag: "Flag of Securities Under Supervision & Securities to Be Delisted https://www.jpx.co.jp/english/listing/market-alerts/supervision/00-archives/index.html )"

ExpectedDividend and SupervisionFlag features are meaningless features for our prediction.

3. EDA
As we deleted 4 features so we need more features.

MA

Moving Averageis a technical indicator that market analysts and investors may use to determine the direction of a trend. It sums up the data points of a financial security over a specific time period and divides the total by the number of data points to arrive at an average

DMA feature

Displaced Moving Average (DMA) is any moving average (MA) that has all its values shifted forward (positive displacement) or back (negative displacement) in time

divergence

Divergence is when the price of an asset is moving in the opposite direction of a technical indicator, such as an oscillator, or is moving contrary to other data. Divergence warns that the current price trend may be weakening, and in some cases may lead to the price changing direction.

rsi

The Relative Strength Index (RSI) is a momentum indicator that measures the magnitude of recent price changes to analyze overbought or oversold conditions.

Stochastic

Stochastics are used to show when a stock has moved into an overbought or oversold position.
psy

Psychological line (PSY), as an indicator, is the ratio of the number of rising periods over the total number of periods. It reflects the buying power in relation to the selling power.

ICH

The Ichimoku Cloud is a collection of technical indicators that show support and resistance levels, as well as momentum and trend direction.

roc

The Price Rate of Change (ROC) is a momentum-based technical indicator that measures the percentage change in price between the current price and the price a certain number of periods ago.

4. Modeling

For modeling, each stock should have its own model for prediction. So we use LGBMRegressor to build models for each stock. Then we use cross validation to test those models. For different separations, we test them 5 times. The results are:


The overall average cross-validation sharpe ratio is 4.1556 with standard deviation of 0.82. So the models work pretty well. 

5. Predictions

Finally, we apply all models to test datasets. And we got this ranking.



