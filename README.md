# EDA on Publicly Traded Stocks (2014-2018)
**Tools used**
Python: Pandas, SeaBorn, Sci-Kit Learn, 

**Datasets used**: \
Indicators: https://www.kaggle.com/cnic92/200-financial-indicators-of-us-stocks-20142018 \
Tickers: http://eoddata.com/symbols.aspx

The purpose of this project is to complete exploratory data analysis on publicly traded stocks in the U.S. and see what insights can be drawn from our datasource. The dataset is quite comprehensive with *226 columns* worth of financial indicators for each of the 4000+ stocks. All of these indicators come from the companies' yearly 10-K's and cover expenditures, revenues, equity, and relevant ratios. The comapanies listed here come from the three major U.S. exchanges (the NYSE, NASDAQ, and AMEX) and are labeled by  economic sector, i.e Technology, Real Estate, etc.

After creating a high level overview of the market, we should look to highlight some of the best and worst performing stocks and create a mock portfolio whose performance we can track and simulate.

**Some tasks to be accomplished:**

* Trim features down to more managable amount. Focus on selecting the indicators that we find most interesting
* Break down dataset into sectors. Find sectors of the market are most profitable, those which spend the most on R&D, etc
* Obtain a view of small, vs. mid, vs. large-cap firms and assess their market performance comparitively

## Transformations

Our original dataset only has Ticker values for each security. To improve the readability, I've brought in a column that has the name of the company associated with each ticker. This can be accomplished using the separate dataframe from EOD Data and performing an INNER join on the Ticker symbol. There is a large amount of missing data in our dataset. Every row has at least one columns with missing information.

## Market Sector Breakdown
![SectorStockVolum](figures/StockVolume_Sector.png)

We can see that the largest portion of stocks traded were those of finance, healthcare, and tech. Very few of the stocks listed were those of communications and utility companies.

![MarketCapBreakdown](figures/MarketCapBreakdown.png)

We also see that the majority of stocks traded are those of small-cap firms.

![MarketCaps](figures/s_caps.png)
![Mid Caps](figures/m_caps.png)
![Large Caps](figures/l_caps.png)

Within the overall cap sizes, we can also create a view to see the proportion of sector representation within these cap sizes. Tech dominates across mid and large caps, while a significantly large proportion of small cap stocks come from healthcare firms.

## Thoughts on Machine Learning

There is a column in our dataset PRICE VAR [%] that tells us how the adjusted closing price for the stock shifted for the following year. We can set this to be our target variable *Y* for machine learning purposes. Due to the large amount of features we have to choose from, a neural network may perform well here to learn which features can predict *Y* best. Of course, linear regression can work as well.