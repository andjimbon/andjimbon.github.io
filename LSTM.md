## Neuronal Networks to Predict Stock Price

<p style="font-size:13px">Click <a href="https://github.com/andjimbon/LSTM-Stock-Prediction/blob/master/Ecopetrol_Stock_Forecasting_LSTM.ipynb">Here</a> to see Code</p>

**Proeject Description:** Employing neural networks to approach financial time series and trying to make predictions of the price movements.

One special type of neural networks is a Long Short-Term Memory (LSTM), an artificial recurrent neural network (RNN) architecture extremely powerful for time series modelling. In a simple way, LSTM predictions are always conditioned by the past experience of the network’s inputs.

Using LSTMs to predict stock prices can actually produce impressive results compared to other, more traditional statistical methods of technical analysis.

We will be using Ecopetrol Stock as an example. Please to get the stock price data, you have to use [Investpy](https://investpy.readthedocs.io/usage.html) library.

#### Get Data

<img src="images/lstm_eco.png?raw=true"/>

#### Drawdown Analysis

The Drawdown is defined as the worst return we would experience if we buy at very highest peak and sell at very lowest point. It measures potential losses, and therefore it is a downside risk measure.

First calculate the max peaks:

<img src="images/eco_max.png?raw=true"/>

Then, plot the percentage of losses. In this case  there's a huge loose within 2014 and 2016. In 2016 reaches the max drawdown:

<img src="images/eco_drawdown.png?raw=true"/>

```python
Max drawdown: -78.0%
Date max drawdown: 2016-01-18 00:00:00
```

### Dive into the LSTM Model

The model uses historical data from the past 6 years. To train the model, 80% of this data will be used, i.e. daily closing prices. At the end, we will check how well would the model have predicted the stock price for the last 90 days, and finally, we will predict the next day close price and compare it to real close price.

First, we have to normalize the close prices:

```python
scaler = MinMaxScaler(feature_range=(0,1))
scaled_price = scaler.fit_transform(close_price)
```

Then, reshape data:

```pyhon
x_train = np.reshape(x_train, (x_train.shape[0], x_train.shape[1], 1))
x_train.shape
```
And set the model parameters:

```python
model = Sequential()
model.add(LSTM(50, return_sequences=True, input_shape= (x_train.shape[1], 1)))
model.add(LSTM(50, return_sequences= False))
model.add(Dense(25))
model.add(Dense(1))
```

Compile and run the model:

```python
model.compile(optimizer='adam', loss='mean_squared_error')

model.fit(x_train, y_train, batch_size=1, epochs=30)
```

Plot the test and predicted values:

<img src="images/lstm_portada.png?raw=true"/>


The prediction fitted quite well the actual stock movements, although there are some gaps between predicted and true movements


#### Next day prediction

If we want to check this model, we just need to pass the next value to predict. We got this:

```python
# Real Close Price vs. Prediction: 

Real:  3140.0
Prediction: 3108.30
Difference: -1.01%
```
