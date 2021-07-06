# Can machine predict financial time series?
This repository is to apply machine learning algorithms in the field of financial time series. The notebook ***LSTM_ARIMA_OOP_version.ipynb*** compares the widely used RNN structure **LSTM** with the traditional **ARIMA** model.
* Aim: predict the adjusted close price of the stock index SSEC
* Raw data is provided in *SZ.csv*
* Performance metric: RMSE(Root Mean Squared Error)
* OCHLV(open,close,high,low,volume) serves as the feature vector of LSTM cf. ARIMA only takes adjusted close price as input
* **LSTM decreased RMSE by 70.90%**

## LSTM
LSTM is trained for only one time. It takes OCHLV of the past 60 trading days as input to predict the price of the next day. In the test set, LSTM predicts 250 trading days in total. RMSE reaches 137.91055.
![LSTM prediction](/ssec_2021_07_06-15_52_53_LSTM.png)
**Tensorboard** provides visualization of the train & validation loss(**needs installation in advance**). To launch Tensorboard, run the following command in the shell(`logdir` is the working directory of training log) and type `http://localhost:6006/` in the url box of your browser:

`tensorboard --logdir=...\LSTM\logs\ssec_2021_07_06-15_52_53_2layers_mean_squared_error_mean_squared_error_adam --port=6006`

The decline of train loss and validation loss means the training process works.

![tensorboard](/tensorboard_train_validation_loss.png)

## ARIMA
ARIMA(P,I,Q) is determined by AIC. It forecasts 250 steps ahead at one time. RMSE reaches 473.85797.
![ARIMA_prediction](/ssec_2021_07_06-15_52_53_arima.png)
