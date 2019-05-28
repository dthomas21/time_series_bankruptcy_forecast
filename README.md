# Time Series Forecast - Forecasting Canadian bankruptcy rates using a VAR (Vector Autoregression) model.

##### Contributors: Donya Fozoonmayeh, Nicole Kacirek, Darren Thomas, Yuhan Wang

### Motivation
Bankruptcy rate is an issue of concern for various interested parties, including banks, insurance companies, and politicians. Accurately forecasting the bankruptcy rate would provide valuable, actionable information to individuals working in these fields. To this end, our bankruptcy rate forecasting analysis was performed using two datasets. The first, `train.csv`, contains data on bankruptcy rate, unemployment rate, population, and house price index in Canada for 28 years, from January 1987 to December 2014. Our goal is to determine which information and which time series model is most effective in forecasting the bankruptcy rate. After finalizing the model, we will then test its efficacy by forecasting the bankruptcy rate in Canada in the ensuing three years (2015 to 2017) using information from the second dataset, the `test.csv` file. This file, like the train.csv file, also contains data on unemployment rate, population and house price index. The goal is to do the best possible forecasting with a proper time series model or a set of models.

### Analyzing Available Modeling Approaches
The type of model we used is referred to as a time series. A time series is a collection of
data points that model the relationship between a numerical value at designated time
intervals. For example, the data points in this time series will be the bankruptcy rate for
every month in Canada beginning in January, 1987. Visually, this can be displayed on a
graph with the bankruptcy rate recorded on the y axis, and the corresponding months
indicated on the x axis. Because we are currently only looking at one variable over time,
bankruptcy rate, we can define this as a univariate time series.
