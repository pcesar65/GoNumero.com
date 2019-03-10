---
layout: post
title:  "Time Series Analysis: Wisconsin Employment"
author: cesar
categories: [ scholarly ]
hidden: false
image: "https://22xmcq37bnw82iclyj35wony-wpengine.netdna-ssl.com/wp-content/uploads/2017/05/sales-forecasting-metrics-1024x768.jpg"
---

## <center>Time Series Analysis: Wisconsin Employment</center>
## <center>1961-1975 </center>
<small>Author: Amir O, Jesus Q, Cesar Ps, Even Q, Mohammad K</small>

<b><center>ABSTRACT</center></b>
<small>The goal for this project is to forecast a season (about 12 months) of the monthly employment
figures of Wisconsin from 1961 to 1974. In our analysis of the time series data, we used various techniques
in order to generate a stationary data. From lays within to logarithmic transformations and differencing
to remove the seasonality and trend within our original data. As a result, it allows us to identify potential
models by looking at ACF and PACF plots. We decided that the best SARIMA model is based on whether
the model has significant coefficients and on the significant lags falling below the lower confidence interval
and lowest AIC according to the stationary data. Where we obtained from transforming and differencing
the original data.</small>

<b>INTRODUCTION:</b>
<small>The employment figures measure the extent to which available labor resources (people available to work) are
being used. Throughout our Wisconsin employment data, we realize there’s different types of employment:
Seasonal employment which is caused by seasonal patterns in economic activity. Frictional unemployment
shows temporary employment during the period when people are searching for a job. Structural unemployment
when a required skill is often brought by technological changes that make many workers obsolete.
While plotting our Wisconsin data we noticed our graph has an upward trend and seasonality. Under those
circumstances, we chose to use logarithmic transformation over the box-cox transformation because  = 0
lays within the 95% confidence interval for possible values of . In addition, the variance of the log transformation
was significantly lower than the variance of the box-cox transformation resulting in the logarithmic
transformation that allows us to reduce the variation of the data. We differenced at lag 12 to remove seasonality,
then differencing again at lag 1 to remove the trend. After performing these procedures, our variance
decreased drastically from our original variance. Then, we chose 3 possible SARIMA models based on the
ACF and PACF graphs. Comparing the significant coefficients, significant lags under the lower edge of the
confidence interval and AIC we decided the final model to be SARIMA(0, 1, 0)x(1, 1, 0)12. Throughout
forecasting, we were able to plot a potential trajectory with 95% confidence for 14 months that approximate
close to the true value in the original dataset from September 1974 to October 1975.</small>
(2)<center><b>EXPLORATORY DATA ANALYSIS</b></center>
<small>Our original dataset consists of monthly employment data from January 1961 to October 1975 in which we
decided to removed the last 14 data points in order to compare forecasting accuracy. On Figure 1 below you can see the fixed plot of the employment in Wisconsin with a sample size of 164 months in total.</small>

![intro forecast]({{ site.baseurl }}/assets/images/forecast/1.jpg){:height="300px" width="200px"}{:class="image-centered"}
<small>As shown in our graph, there is an evident seasonality component because the dataset was collected
monthly. In addition, there was an upward trend present throughout the sample dataset. Before applying
any type of transformation, the variance of our original dataset is 2186.5. Since our dataset has a large
variance as well as having an upward trend and seasonality. We can conclude that our time series needs to
be transformed and differenced in order to make it stationary.</small>


