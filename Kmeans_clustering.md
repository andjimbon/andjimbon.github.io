## K-means Clustering 

**Project description**: The goal of this project is to divide stocks into groups with “similar characteristics” using K-means Clustering Method. This approach can help us in portfolio construction to ensure we choose a universe of stocks with sufficient diversification between them.

### Colecting Data

First, we need to colect stock data. To do so, we will run the script below to get the current tickers from S&P 500 Index, a stock market index that measures the stock performance of 500 large companies listed on stock exchanges in the United States.

```python
sp500_wiki = 'https://en.wikipedia.org/wiki/List_of_S%26P_500_companies'

sp = pd.read_html(sp500_wiki)
sp = sp[0]['Symbol'].tolist()

sp500_stocks = []
for stock in sp:
    try:
        close_prices = web.DataReader(stock,'yahoo','01/01/2019')['Adj Close']
        close_prices = pd.DataFrame(close_prices)
        close_prices.columns = [stock]
        sp500_stocks.append(close_prices)
    except:
        pass
    df = pd.concat(sp500_stocks,axis=1)
```

Once stock data is into a Pandas dataframe, we are ready to start the K-Means investigation.

### Selecting the number of Clusters

**How many clusters do we actually need?** Rather than make some arbitrary decision we can use an Elbow Curve, often used to truncate the number of parameters in data-driven models. This method shows us the relationship between the number of clusters and the Sum of Squared Errors (SSE) resulting from using that number of clusters.

Plot the curve.

<img src="images/elbow.PNG?raw=true"/>

You'll notice once the number of clusters reaches 5, the reduction in the SSE begins to slow down for each increase in cluster number. So, for this exercise we will be using 5 clusters.

### Outliers

Regulary, when clustering data we have to deal with outliers. An outlier is an observation point that is distant from other observations.

There's a empirical rule called **"3σ approach"** that states almost all data lies within 3 standard deviations of the mean for a normal distribution. In fact, this rule states that within three standard deviations is 99.7% of the data.

Before continue, as an example we are going to identify outliers from Apple's stock returns using the 3σ approach

Firs, calculate the rolling mean and standard deviation. We will use a monthly window.

```python
df2 = pd.DataFrame(web.DataReader('AAPL','yahoo','01/01/2017')['Adj Close'])

window = 21

df2['daily_ret'] = df2.pct_change()

df_rolling = df2[['daily_ret']].rolling(window=window).agg(['mean', 'std'])
```

Date |	Adj Close |	daily_ret	| mean w=21	| std w=21	
----|----|----|----|----|			
2020-04-13	| 273.250000 |	0.019628	| 0.006123	| 0.056867
2020-04-14	| 287.049988 |	0.050503	| 0.002823	| 0.051718 


"$$\n",
"\\sigma_p^2 =   \\text{Var}(w_1 R_1 + w_2 R_2) = \n",
"w_1^2 \\text{Var}(R_1) + w_2^2\\text{Var}(R_2) + 2w_1 w_2\\text{Cov}(R_1,R_2) =\n",
"w_1^2 \\sigma_1^2 + w_2^2\\sigma_2^2 + 2w_1 w_2\\text{Cov}(R_1,R_2), \n",
"$$\n",


<img src="images/outl.png?raw=true"/>

<img src="images/kmeans.png?raw=true"/>


<img src="images/cluster_ret.png?raw=true"/>


