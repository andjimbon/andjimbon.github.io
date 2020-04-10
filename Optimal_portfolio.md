## Financial Analysis and Efficient Frontier for Colombian Stocks

<p style="font-size:13px">Click <a href="https://github.com/andjimbon/Efficient-Frontier-for-Colombian-Stocks/blob/master/Optimal_Portfolio_with_Colombian_Stocks.ipynb">Here </a>to see Code</p>

**Project description:** Financial analysis for colombian stocks and portfolio optimization methods (Monte Carlo approach and Scipy’s “optimize” function for minimizing or maximizing objective functions subject to constraints)

This Project uses the API provided by [Investpy](https://investpy.readthedocs.io/index.html) to get historical data for colombian stocks.

The historical data for U.S Stocks can easily get from Yahoo Finance.


### Historical Data

For the purpose of this project we will get the historical prices from Ecopetrol (**ECO**), Bancolombia (**BIC**), Interconnection Electric SA (**ISA**), Grupo de Inversiones Suramericana (**SIS**) and Grupo Argos (**ARG**). The history range for the analysis is from **'01/01/2014'** to **'01/02/2020'** ('%d/%m/%Y').

Note: Investpy just let us get the historical price for one stock at a time, so we need to iterate over the ticker list and concatenate dataframes for each stock. The result will be a one dataframe containing the daily close price for each ticker

Date|ECO|BIC|ISA|SIS|ARG
----- | ----- |----- | ----- |----- |
2020-01-31 | 3180.0 | 42440.0 | 18800.0 | 32000.0 | 17480.0


### Plotting useful information

With Python and a few lines of code we can easily plot the stocks prices, the log mean return and the cumulative return over time.

<img src="images/stock_price.png?raw=true"/>

<img src="images/stock_ret.png?raw=true"/>

Cumulative return shows us that if we were invested 1 monetary unit in ISA in 2014, at the end of the analyzed period, we would get almost 225 monetary units (fee free)

<img src="images/cummulative_ret.png?raw=true"/>

We can plot the daily returns for ISA and below plot its daily realized volatility.

The formula for realized volatility is as follows:

![RV \equiv \sqrt{\sum_{i=1}^{T} r_t^2}](https://render.githubusercontent.com/render/math?math=RV%20%5Cequiv%20%5Csqrt%7B%5Csum_%7Bi%3D1%7D%5E%7BT%7D%20r_t%5E2%7D)

Where ![\large r_t =](https://render.githubusercontent.com/render/math?math=%5Clarge%20r_t%20%3D) return at period t

The grahp shows us that the maximum daily volatility for ISA is ![\large sigma \approx 1](https://render.githubusercontent.com/render/math?math=%5Csigma%20%5Capprox%201)

<img src="images/ret_vs_vol.png?raw=true"/>


### Log Return Distributions and Correlation Matrix

Pandas provides us an easy way to plot a scatter matrix and observe the distribution of returns for each stock and the correlation between them

<img src="images/matrix.png?raw=true"/>

Selecting two stock we can run an OSL (ordinary least-squares) analysis and then examine the correlation for a fixed window over time (Window period = 252 days.

<img src="images/linear_r.png?raw=true"/>

The graph shows postive corretation over time between the two stocks

<img src="images/corr_ot.png?raw=true"/>
 

### Statistics and Normality Tests

Next graph shows the QQ plot for ECO. Clearly, the sample quantile values do not lie on a straight line, indicating “non-normality.” On the left and right sides there are many values that lie well below the line and well above the line, respectively. In other words, the time series data exhibits fat tails,

<img src="images/qqplot.png?raw=true"/>

We can run a few statistics to validate the hypothesis that the sample data are normally distributed.

Results for symbol ECO | Value
------------ | -------------
Skew of data set | -0.097
Skew test p-value | 0.126
Kurt of data set | 3.276
Kurt test p-value | 0.000
Norm test p-value | 0.000

The **p -values** of the different tests are all zero, strongly rejecting the test hypothesis. We might have to use richer models that are able to generate fat tails (e.g., models with stochastic volatility or jump diffusion models).


## Opmitization Methods


### Monte Carlo Approach: : Optimal Portfolio

With this method we will try to discover the optimal weights by simply creating a large number of random portfolios, and extract within all these randomly portfolios the one who has the maximum sharpe Ratio (Optimal Portfolio) and in the other hand, the one who has the minimun variance (Minimun Variance Portfolio)

Before to do that, we will refresh some formulas: 

**Portfolio Standard Deviation**
![\large \sigma_{port} = \sqrt{\sum_{i=1}^{n}w_i^2\sigma_i^2 + \sum_{i=1}^{n}\sum_{i=1}^{n}w_iw_jCov_{ij}}](https://render.githubusercontent.com/render/math?math=%5Csigma_%7Bport%7D%20%3D%20%5Csqrt%7B%5Csum_%7Bi%3D1%7D%5E%7Bn%7Dw_i%5E2%5Csigma_i%5E2%20%2B%20%5Csum_%7Bi%3D1%7D%5E%7Bn%7D%5Csum_%7Bi%3D1%7D%5E%7Bn%7Dw_iw_jCov_%7Bij%7D%7D)

wehere:
![\large \sigma_{port} =](https://render.githubusercontent.com/render/math?math=%5Csigma_%7Bport%7D%20%3D) the standard deviation of the portfolio
![\large \w_{i} =](https://render.githubusercontent.com/render/math?math=%5Cw_%7Bi%7D%20%3D) the weights of individual assets in the portfolio, where weights are determined by the proportion of value in the portfolio
![\large \sigma_i^2 =](https://render.githubusercontent.com/render/math?math=%5Csigma_i%5E2%20%3D) the variance of rates of return for asset i
![\large \Cov_{ij} =](https://render.githubusercontent.com/render/math?math=%5CCov_%7Bij%7D%20%3D) the variance of rates of return for asset i, where ![\large \Cov_{ij} = r_{ij}\sigma_i\sigma_j](https://render.githubusercontent.com/render/math?math=%5CCov_%7Bij%7D%20%3D%20r_%7Bij%7D%5Csigma_i%5Csigma_j)


**Portfolio Expected Return**

 ---- | ----
Returns     |  0.069986
Volatility   | 0.164826
Sharpe Ratio | 0.424605
ECO Weight   | 0.078844
BIC Weight   | 0.240285
ISA Weight   | 0.204278
SIS Weight   | 0.348250
ARG Weight   | 0.128342 


 ---- | ----      
Returns      | 0.140984
Volatility   | 0.194283
Sharpe Ratio | 0.725665
ECO Weight   | 0.020040
BIC Weight   | 0.410700
ISA Weight   | 0.561843
SIS Weight   | 0.006014
ARG Weight   | 0.001402


<img src="images/EF_monte_carlo.png?raw=true"/>



### Linear Programming with Scipy: Optimal Portfolio



ECO|BIC|ISA|SIS|ARG
----- | ----- |----- | ----- |
0.09 |0.24|0.19|0.34|0.14


ECO|BIC|ISA|SIS|ARG
----- | ----- |----- | ----- |
0.0 |0.4454|0.5546|0.0|0.0



```python
array([0.1437 , 0.196  , 0.73318])
```

```python
array([0.06907, 0.16479, 0.41915])
```

<img src="images/efficient_front.png?raw=true"/>


## PyPortfolioOpt Library


```python
{'ECO': 0.0, 'BIC': 0.43204, 'ISA': 0.56796, 'SIS': 0.0, 'ARG': 0.0} 

Expected annual return: 14.4%
Annual volatility: 19.7%
Sharpe Ratio: 0.73
(0.14406456150209906, 0.19653202475586729, 0.7330335179778285)
```


```python
Discrete Allocation: {'BIC': 102.0, 'ISA': 301.0}
Funds Remaining: $12320.00
```
