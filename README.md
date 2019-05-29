# Time Series Forecast - Forecasting Canadian bankruptcy rates using a VAR (Vector Autoregression) model.

### Motivation
Bankruptcy rate is an issue of concern for various interested parties, including banks, insurance companies, and politicians. Accurately forecasting the bankruptcy rate would provide valuable, actionable information to individuals working in these fields.`train.csv`, contains data on bankruptcy rate, unemployment rate, population, and house price index in Canada for 28 years, from January 1987 to December 2014. Our goal is to determine which information and which time series model is most effective in forecasting the bankruptcy rate. The goal is to do the best possible forecasting with a proper time series model or a set of models.

Source code can be viewed in `bankruptcy_forecast.rmd`, however, it can also be viewed in a more user read friendly way in an R Markdown file in `bankruptcy_forecast.pdf`, which includes both source code and graphs.

`final_report_and_model_explanation.pdf` further discusses why we chose our VAR model. Additionally it highlights the different modeling approaches in both univariate and multivaraite time series including Holt-Winters, Box-Jenkins, ARMA (autoregressive moving average), ARIMA (autoregressive integrated moving average), SARIMA (seasonal autoregressive moving average), double exponential smoothing, triple exponential smoothing and SARIMAX. 

While the previously mentioned models are highlighted in the final report, I made a flow diagram that helps with understanding the flow of when to use which model:


![Alt text](images/flow_chart.png?raw=true "Title")


### Analyzing Available Modeling Approaches

*Univariate Time Series*
The type of model we used is referred to as a time series. A time series is a collection of data points that model the relationship between a numerical value at designated time intervals. For example, the data points in this time series will be the bankruptcy rate for every month in Canada beginning in January, 1987. Visually, this can be displayed on a graph with the bankruptcy rate recorded on the y axis, and the corresponding months indicated on the x axis. Because we are currently only looking at one variable over time, bankruptcy rate, we can define this as a *univariate time series*.

Using the univariate modeling approach allows for the option of two different methods to establish a model: *Holt-Winters* and *Box-Jenkins*. The key difference between these two models, is that the Box-Jenkins method applies some version of an autoregressive moving average (ARMA), while Holt-Winters uses some version of exponential smoothing to find the best fit of a time series model to past values of a time series. With ARMA, the past observations are weighted equally, but with Holt-Winters, exponentially is used to assign exponentially decreasing weights over time. Different versions of both ARMA and exponential smoothing exist and choosing the best depends on the trend and seasonality of the data. If the model is stationary, ARMA and single exponential smoothing can be used. If the model exhibits trend, but no seasonality, autoregressive integrated moving average (ARIMA) and double exponential smoothing must be used. Lastly, if the model demonstrates seasonality, regardless of trend, seasonal autoregressive moving average (SARIMA) or triple exponential smoothing must be used.

*Multivariate Time Series*
While univariate models use only the temporal observations of one variable (in this case bankruptcy), it can sometimes be helpful to also use additional variables in the model. Additional variables may add value to the model if they are 1) collected at the same frequency and for the same duration as bankruptcy and 2) are highly correlated with bankruptcy. For this project, the dataset contains three other variables - unemployment rate, population, and house price index. This data was collected at the same monthly time intervals as bankruptcy. Therefore, so long as they are correlated with bankruptcy, they could potentially be useful to help formulate a predictive model. If these variables are not correlated with bankruptcy, their behavior does not provide any indication as to how bankruptcy changes over time and including them would not give any more information than the univariate model.

After computing the correlations (see `bankruptcy_forecast.rmd`) between the additional variables and bankruptcy, we found population and house price index to be highly correlated with bankruptcy and unemployment rate moderately correlated with it. Thus, it might be a good idea for us to try to model bankruptcy using a multivariate model that includes one or more of these additional variables.

The specific model we choose depends on how we view the relationship between bankruptcy and these additional variables. We say that the relationship is *exogenous* if we believe that population, house price index, and unemployment rate influence the behavior of bankruptcy, but bankruptcy has no influence on them. If this were true, we would use a *SARIMAX* model. However, we believe bankruptcy does actually affect population, house price index, and unemployment rate - or in other words the relationship is endogenous. Therefore, a SARIMAX model would not be appropriate since it doesn’t account for the influence of bankruptcy on the other variables. Instead, we should try a *Vector Autoregression (VAR) model* to try and account for this bidirectional relationship.
