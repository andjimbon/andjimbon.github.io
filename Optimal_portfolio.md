## Financial Analysis and Efficient Frontier for Colombian Stocks

<p style="font-size:13px">Click <a href="https://github.com/andjimbon/Efficient-Frontier-for-Colombian-Stocks/blob/master/Optimal_Portfolio_with_Colombian_Stocks.ipynb">Here </a>to see Code</p>

**Project description:** Financial analysis for colombian stocks. All along this code

With the API provided by [Investpy](https://investpy.readthedocs.io/index.html) it's possible to get historical data for colombian stocks 

### 1. Historical Data

Date|ECO|BIC|ISA|SIS|ARG
----- | ----- |----- | ----- |----- |
2020-01-31 | 3180.0 | 42440.0 | 18800.0 | 32000.0 | 17480.0

```python
{'ECO': 0.0, 'BIC': 0.43204, 'ISA': 0.56796, 'SIS': 0.0, 'ARG': 0.0} 

Expected annual return: 14.4%
Annual volatility: 19.7%
Sharpe Ratio: 0.73
(0.14406456150209906, 0.19653202475586729, 0.7330335179778285)
```

<img src="images/corr_ot.png?raw=true"/>



Results for symbol ECO|
------------ | -------------
Skew of data set | -0.097
Skew test p-value | 0.126
Kurt of data set | 3.276
Kurt test p-value | 0.000
Norm test p-value | 0.000

ECO|BIC|ISA|SIS|ARG
----- | ----- |----- | ----- |
0.09 |0.24|0.19|0.34|0.14


<img src="images/stock_price.png?raw=true"/>


<img src="images/stock_ret.png?raw=true"/>


<img src="images/cummulative_ret.png?raw=true"/>


<img src="images/matrix.png?raw=true"/>


<img src="images/ret_vs_vol.png?raw=true"/>


<img src="images/qqplot.png?raw=true"/>


<img src="images/efficient_front.png?raw=true"/>

statistic | value
------------ | -------------
size | 1481.000
min | -0.104
max | 0.103
mean | -0.000
std | 0.020
skew | -0.097
kurtosis | 3.276

Results for symbol ECO
------------ | -------------
Skew of data set | -0.097
Skew test p-value | 0.126
Kurt of data set | 3.276
Kurt test p-value | 0.000
Norm test p-value | 0.000

ECO|BIC|ISA|SIS|ARG
----- | ----- |----- | ----- |
0.0 |0.4454|0.5546|0.0|0.0


