# Time Series Forecast - Forecasting Canadian bankruptcy rates using a VAR (Vector Autoregression) model.

### Motivation
Bankruptcy rate is an issue of concern for various interested parties, including banks, insurance companies, and politicians. Accurately forecasting the bankruptcy rate would provide valuable, actionable information to individuals working in these fields. `train.csv`, contains data on bankruptcy rate, unemployment rate, population, and house price index in Canada for 28 years, from January 1987 to December 2014. Our goal is to determine which information and which time series model is most effective in forecasting the bankruptcy rate. The goal is to do the best possible forecasting with a proper time series model or a set of models.

Source code can be viewed in `bankruptcy_forecast.rmd`, however, it can also be viewed in a more user read friendly way in an R Markdown file in `bankruptcy_forecast.pdf`, which includes both source code and graphs.

`final_report_and_model_explanation.pdf` further discusses why a VAR model was chosen. Additionally, it highlights the different modeling approaches in both univariate and multivaraite time series including Holt-Winters, Box-Jenkins, ARMA (autoregressive moving average), ARIMA (autoregressive integrated moving average), SARIMA (seasonal autoregressive moving average), double exponential smoothing, triple exponential smoothing and SARIMAX. 

While the previously mentioned models are highlighted in the final report, I made a flow diagram that helps with understanding the flow of when to use which model:

![Alt text](images/flow_chart.png?raw=true "Title")

## Analyzing VAR Model 
*please see `final_report_and_model_explanation.pdf` for further explanation and `bankruptcy_forecast.rmd` for supporting R code*

The dataset was divided into two parts - one part for training our model and one for testing it. The training data is from January 1987 to December 2009 and the test data is from January 2010 to December 2014. The value of p that minimized the AIC was p=10, therefore VAR(10) is our optimal model. Below a graph of the model and the actual observations can be seen.

![Alt text](images/fitted_observed.png?raw=true "Title")


RMSE was calculated (root mean squared error) for the model by taking the square root of the squared difference between the observed values and the predicted values. A small RMSE indicates that the fitted values are close to the observed values, and that the model is doing a good job at forecasting. The RMSE of our model is 2.31. Considering that having an RMSE close to zero suggests that the predicted values are close to the observed values, this model was picked to forecast the bankruptcy rate for 2015-2017.

![Alt text](images/forecast.png?raw=true "Title")
