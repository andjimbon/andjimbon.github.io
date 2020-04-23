## Forecasting Google Searchs 

<p style="font-size:13px">Click <a href="https://github.com/andjimbon/Time-Series-Analysis-and-Forecasting/blob/master/Google_Trends_Time_Series_Analysis_SARIMAX.ipynb">Here </a>to see Code</p>

**Project Description:** The objective of this project is to forecast google trends data appying time-series tools in Python;

We will be using statsmodels libraries to achieve this goal.

#### Get data from Google Trends

As an example, we will use "pajamas" and "bikinis" worldwide searchs. You can get this data directly from [Google Trends](https://trends.google.com/trends/?geo=US)

Plot series:

<img src="images/trends.png?raw=true"/>

Please observe how these series complements one each other. While people search "pajamas" in google, searches for "bikinis" are no longer popular, and viceversa. There is a seasonal component, obviously.

<p>&nbsp;</p>

#### Trend

Statsmodel library can easily get the trending for "pajamas" series. 

<img src="images/trend2.png?raw=true"/>

And if we want decompose the time-series, this library plot a nice graph with Trend, Seasonal and Residuals components of the serie.

<img src="images/decomposition.png?raw=true"/>

<img src="images/first_diff.png?raw=true"/>

<img src="images/portada.png?raw=true"/>


<img src="images/autocorr.png?raw=true"/>

<img src="images/forecast.png?raw=true"/>


