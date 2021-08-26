# Future of NBA Three Pointer
  
## Methodology - Time Series: 
We attempted to forecast the future of the NBA 3 Point Shot through time series analysis. Our data of interest was the percentage of shots that were 3 pointers of each NBA season since the 3 point line was added in 1979. We excluded the 2019-2020 season because the season is still in progress at the time of this project.

![image](https://user-images.githubusercontent.com/51941454/76173011-a4e97100-6158-11ea-97e1-0e9d7fb14ac5.png)

We created two datasets, a training set with the observations from 1979 - 2016 and a test set of all observations (1979 - 2019). Our goal was to create an ARIMA model of the training set, forecast until 2019, and compare it to the test set. If our model was accurate, then we would forecast the next few years.

We employed a Box-Cox transformation on our data in an attempt to stabilize variance. This slightly increased our variance, but we found that the Box-Cox transformed data yielded more accurate forecasts, when compared to the test set.

We concluded that our time series was not seasonal, but there is a clear upward trend, implying that the percentage of shots that are from the 3 point line is increasing.

We differenced our data at a lag value of 1, once at a time until our time series resembled white noise. From there, we examined several ACF and PACF plots in order to identify any preliminary models. Ultimately, we decided to automate this process, using the auto.arima() function in R. We settled on an ARIMA(0,1,2) model.

We ran diagnostics testing to see if our model was accurate. The residuals were normally distributed and resembled white noise, so we decided to use this model.

![image](https://user-images.githubusercontent.com/51941454/76173032-c5193000-6158-11ea-9ea1-e47a4ec9db9b.png)

We plotted our forecasts against the test set observations. We found that they matched fairly well.

![image](https://user-images.githubusercontent.com/51941454/76173036-dbbf8700-6158-11ea-8a04-1c79b08d59c6.png)

Once we began forecasting several years into the future, we noticed a particular phenomenon. The forecasts converged to a nonzero, constant value, namely 0.35. This supports our hypothesis that the 3 point shot percentage will eventually converge to an equilibrium point.

![image](https://user-images.githubusercontent.com/51941454/76173043-e843df80-6158-11ea-9ce7-904b426d1577.png)

## Key Results - Time Series:
Our model suggests that the NBA 3 point shot percentage will eventually converge to a nonzero, constant value of 35%. 

Our model could be improved simply by training our model on more data. Since there's only been about 40 years since the 3 point line was added, this limits the amount of data we can use. Regardless, our model suggests that the percentage of shots taken from the 3 point line will continue to rise slightly in the next couple years and then likely converge to a point where it's no longer beneficial to increase the number of 3's taken.
