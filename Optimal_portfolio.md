## Financial Analysis and Efficient Frontier for Colombian Stocks

<p style="font-size:13px">Click <a href="https://github.com/andjimbon/Efficient-Frontier-for-Colombian-Stocks/blob/master/Optimal_Portfolio_with_Colombian_Stocks.ipynb">Here </a>to see Code</p>

**Project description:** Financial analysis for colombian stocks and portfolio optimization methods (Monte Carlo approach and Scipy’s “optimize” function for minimizing or maximizing objective functions subject to constraints)

This Project uses the API provided by [Investpy](https://investpy.readthedocs.io/index.html) to get historical data for colombian stocks.

The historical data for U.S Stocks can easily get from Yahoo Finance.

### 1. Historical Data

For the purpose of this project we will get the historical prices from Ecopetrol (ECO), Bancolombia (BIC), Interconnection Electric SA (ISA), Grupo de Inversiones Suramericana (SIS) and Grupo Argos (ARG). The history range for the analysis is from '01/01/2014' to '01/02/2020' ('%d/%m/%Y').

Note: Investpy just let us get the historical price for one stock at a time, so we need to iterate over the ticker list and concatenate dataframes for each stock. The result will be a one dataframe containing the daily close price for each ticker

Date|ECO|BIC|ISA|SIS|ARG
----- | ----- |----- | ----- |----- |
2020-01-31 | 3180.0 | 42440.0 | 18800.0 | 32000.0 | 17480.0

### Plotting useful information

With Python and a few lines of code we can easily plot the stocks prices, the log mean return and the cumulative return over time.

<img src="images/stock_price.png?raw=true"/>

<img src="images/stock_ret.png?raw=true"/>

Cumulative return shows us that if we were invested 1 monetary unit in ISA in 2014, at the end of the analyzed period, we would get almost 225 monetary units (free fee)

<img src="images/cummulative_ret.png?raw=true"/>

To calculate the monthly realized volatilities for ISA we use daily returns and then annualize the values.
The formula for realized volatility is as follows:
![RV \equiv \sqrt{\sum_{i=1}^{T} r_t^2}](https://render.githubusercontent.com/render/math?math=RV%20%5Cequiv%20%5Csqrt%7B%5Csum_%7Bi%3D1%7D%5E%7BT%7D%20r_t%5E2%7D)

 Where r_t \equiv return at period t

<img src="images/ret_vs_vol.png?raw=true"/>

```python
{'ECO': 0.0, 'BIC': 0.43204, 'ISA': 0.56796, 'SIS': 0.0, 'ARG': 0.0} 

Expected annual return: 14.4%
Annual volatility: 19.7%
Sharpe Ratio: 0.73
(0.14406456150209906, 0.19653202475586729, 0.7330335179778285)
```

<img src="images/corr_ot.png?raw=true"/>


ECO|BIC|ISA|SIS|ARG
----- | ----- |----- | ----- |
0.09 |0.24|0.19|0.34|0.14





<img src="images/matrix.png?raw=true"/>





<img src="images/qqplot.png?raw=true"/>


<img src="images/efficient_front.png?raw=true"/>

statistic | value
- | -
size | 1481.000
min | -0.104
max | 0.103
mean | -0.000
std | 0.020
skew | -0.097
kurtosis | 3.276

Results for symbol ECO | 
------------ | -------------
Skew of data set | -0.097
Skew test p-value | 0.126
Kurt of data set | 3.276
Kurt test p-value | 0.000
Norm test p-value | 0.000

ECO|BIC|ISA|SIS|ARG
----- | ----- |----- | ----- |
0.0 |0.4454|0.5546|0.0|0.0


Date|ECO|BIC|ISA|SIS|ARG
----- | ----- |----- | ----- |----- |
2020-01-31 | 3180.0 | 42440.0 | 18800.0 | 32000.0 | 17480.0

```python
array([0.1437 , 0.196  , 0.73318])
```
```python
array([0.06907, 0.16479, 0.41915])
```
```python
Discrete Allocation: {'BIC': 102.0, 'ISA': 301.0}
Funds Remaining: $12320.00
```

<img src="images/linear_r.png?raw=true"/>



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


