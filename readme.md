# Weather Forecasting Based on LSTM/ARIMA Model

## 1 Environment
Language：Python   
Interpreter：Python 3.10  
Python package：

```
joblib=1.1.0
statsmodels=0.13.2
matplotlib=3.5.1
seaborn=0.11.2
scipy=1.8.0
scikit-learn=1.0.2
tensorflow=2.9.1
pandas=1.4.3
numpy=1.22.3
beautifulsoup4=4.11.1
urllib3=1.26.11
```

## 2 Project Instruction
This project is mainly composed of two parts: LSTM, ARIMA model fitting effect comparison, and weather forecasting system (GUI) interface based on the two models \
The description of each file of this project is as follows: 

`main1.py`: model comparison \
`main2.py`: weather forecast system \
`data_get.py`: gets weather data and builds a dataset \
`data_load.py`: read the data in the dataset, clean the data, visualize the original data, and check the white noise of the original data \
`arima.py`: ARIMA model implementation, including selection of p, d, q parameters, ADF test and white noise test, ARIMA model automatic selection and manual selection \
`lstm.py`: implementation of LSTM model, including data processing, generation and fitting of LSTM network, drawing of loss curve \
`model_analyze.py`: Model fitting effect evaluation, including residual sequence test (residual plot, residual histogram density plot, QQ plot, ACF plot), model accuracy evaluation, fitting plot\
`handle.py`: data acquisition for weather forecast system 

## 3 Model Comparison
__Example:__ Run the `main1.py` file directly, or open this program in the terminal, enter
```
python main1.py
```
Model comparisons are available and will be performed sequentially:\
LSTM model fitting (skipable) -> draw loss curve (skip with the previous step) ->
draw LSTM fitting curve -> draw LSTM model residual line chart, density map, QQ map, ACF map, print white noise test results -> print LSTM model accuracy evaluation index

![](picture/lstm1.png#pic_center)
![](picture/lstm2.png#pic_center)
```
LSTM:  {'MSE': 3.809351612077138, 'RMSE': 1.9517560329296122, 'MAE': 1.3407798945997853, 'MAPE': 0.06877151237127875}
```
-> Draw difference diagram -> Draw ACF PACF diagram -> ARIMA model fitting (skipable) -> Print ARIMA model parameters ->Draw ARIMA fitting curve -> draw ARIMA model residual line chart, density chart, QQ chart, ACF chart,Print white noise test results -> print ARIMA model accuracy evaluation index
![](picture/arima1.png#pic_center)
![](picture/arima2.png#pic_center)

```
                                      SARIMAX Results                                      
===========================================================================================
Dep. Variable:                                   y   No. Observations:                 1000
Model:             SARIMAX(2, 1, 1)x(2, 1, [], 30)   Log Likelihood               -2108.542
Date:                             Mon, 29 Aug 2022   AIC                           4229.085
Time:                                     22:29:38   BIC                           4258.342
Sample:                                          0   HQIC                          4240.222
                                            - 1000                                         
Covariance Type:                               opg                                         
==============================================================================
                 coef    std err          z      P>|z|      [0.025      0.975]
------------------------------------------------------------------------------
ar.L1          0.7687      0.047     16.275      0.000       0.676       0.861
ar.L2         -0.2145      0.025     -8.685      0.000      -0.263      -0.166
ma.L1         -0.7967      0.041    -19.250      0.000      -0.878      -0.716
ar.S.L30      -0.6301      0.024    -26.243      0.000      -0.677      -0.583
ar.S.L60      -0.3619      0.023    -16.052      0.000      -0.406      -0.318
sigma2         4.4711      0.154     28.984      0.000       4.169       4.773
===================================================================================
Ljung-Box (L1) (Q):                   0.04   Jarque-Bera (JB):               304.86
Prob(Q):                              0.84   Prob(JB):                         0.00
Heteroskedasticity (H):               0.45   Skew:                            -0.42
Prob(H) (two-sided):                  0.00   Kurtosis:                         5.61
===================================================================================
```
![](picture/arima3.png#pic_center)
![](picture/arima4.png#pic_center)
```
ARIMA:  {'MSE': 26.621762638482185, 'RMSE': 5.159628149245077, 'MAE': 3.945205074339352, 'MAPE': 0.21063328014251662}
```

## 4 Weather forecast System
__Example:__ Run the `main2.py` file directly, or open this program in the terminal, enter
```
python main2.py
```
You can enter the weather forecast system, select a city and model through the drop-down menu, and click the `查询` button to get the weather forecast for the city in the next 7 days. \
Click the `返回` button to return to the main interface and choose again. \
Click the `退出` button to exit the weather forecast system.


![](picture/gui1.png#pic_center)
![](picture/gui2.png#pic_center)