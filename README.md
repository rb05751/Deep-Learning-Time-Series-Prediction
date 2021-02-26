# Deep-Learning-Time-Series-Prediction

This projects goal was explore the application of recurrent neural network variants to time series prediction, more specifically, stock price prediction. There has been ample amounts of research centered around the use of classical techniques such as ARIMA and ETS and non-classical such as recurrent neural networks and other machine learning algorithms. In this project, a variant of a recurrent neural network consisting of convolutional1D and LSTM layers are used to forecast stock prices over a 5-day horizon. The algorithm performed well when fitting the to the validation and test datasets. The model achieved an MAE of ~4 on the train set, ~3 on the validation and ~3 on the test set. This can be intrepretted as having an average error of $3 at each time step in the forecast horizon. 

# Data Source
The data used for training the model was sourced from the AlphaVantage API. A python package was created for streamlining the data injestion process from this API and can be found in this same repository at "AlphaVantage". The API allows for sourcing historical price and technical indicator data on any stock available on the market for trading. 

# Model Architecture
The model was built using the Tf.Keras API in an object-oriented manner. The layers are built as follows:

Input = Tensor of Shape [batch size, sequence length, feature_dim] sequence length (window_size) being 10 and feature dim being 4 consisting of price and 3 MACD signals. <br>
Layer1 = Convolutional1D <br>
Layer2-4 = LSTMs <br>
Layer5-6 = Dense with final layer being a regression output <br>

# Purchasing Instructions Algorithm / Backtesting
There is a plot of how tightly the model fit to the entire dataset including the last ~1000 days. However, the performance of the model in the trading algorithm portion has high variance. When I first tested this model it achieved an average CAGR of 39% on 13 randomly selected stocks, which was roughly 60 days ago. I tested it a few days ago and it is barely clearing 5%. This shows how much an algorithm can change in a short amount of time. There will need to be more analysis done on the algorithm to determine its overall performance and a means of improving it.
