---
layout: post
title:  "Time Series Analysis: Wisconsin Employment"
author: Amir O, Jesus Q, Cesar Ps, Even Q, Mohammad K
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

![intro forecast]({{ site.baseurl }}/assets/images/forecast/1.jpg){:height="250px" width="450px"}{:class="image-centered"}
<small>As shown in our graph, there is an evident seasonality component because the dataset was collected
monthly. In addition, there was an upward trend present throughout the sample dataset. Before applying
any type of transformation, the variance of our original dataset is 2186.5. Since our dataset has a large
variance as well as having an upward trend and seasonality. We can conclude that our time series needs to
be transformed and differenced in order to make it stationary.</small>

![ACF and PACF]({{ site.baseurl }}/assets/images/forecast/2.jpg){:height="360px" width="750px"}{:class="image-centered"}
<small>Figure 2 shows a strong seasonality component of period 12 and an increasing trend in the data. The
variability of the data changes with time. A visual inspection of the autocorrelation function plot indicates
that the employment times series is nonstationary since the ACF decays very slowly. Suggesting some
transformation needs to be done to the data to render it stationary before choosing and fitting an ARMA
time series model.</small>

<b>Box-Cox Transformation</b>

<small>In order to make the data stationary and reduce the variance, we try a Box-Cox transformation. In Figure
3: Log Likelihood Box-Transformation,  falls between 0 which makes the Box-Cox variable indeterminate
form 0/0. That being the case, rewriting the Box-Cox formula gives us </small>

![formula]({{ site.baseurl }}/assets/images/forecast/3.jpg){:height="100px" width="300px"}{:class="image-centered"}

<small>corresponding to a logarithmic transformation. We can see the seasonal fluctuations and trend in the logtransformed
time series showing constancy over time. In addition, the log(Xt) transformation has smaller
variance than Box-Cox(Xt) transformation.</small>

![two models Figure 3]({{ site.baseurl }}/assets/images/forecast/4.jpg){:height="450px" width="700px"}{:class="image-centered"}


<b>(2.2.2) Log Transformation</b>

<small>In order to make the data stationary and stabilize the variance, we used logarithmic transformation. Since
it has the lowest variance compared to the Box-Cox transformation. The variance for the box-cox transformation
is 0.247729 and was reduced to 0.0197 after using logarithmic transformation. Therefore, we picked
logarithmic transformation as our best transformation.</small>
![Figure 4 ACF and PACF]({{ site.baseurl }}/assets/images/forecast/5.jpg){:height="450px" width="700px"}{:class="image-centered"}

<small>The slow decay of the autocorrelations in figure 4 is similar to the original dataset indicating that our
data is still non-stationary. Thus, we remove the seasonality and trend in the next step.</small>

<b>(2.3) Differencing </b>

<b>(2.3.1) De-Seasonalizing</b>

<small> We use differencing to deseasonalize and detrend the data. Since our data has a seasonal component of period
12, we used this to remove the seasonality of period 12. After taking the differenced, the variance decreased
even more to 0.0002516346. Next, we remove the trend based on the deseasonalized data we obtained. </small> 

![Figure 5 ACF and PACF]({{ site.baseurl }}/assets/images/forecast/6.jpg){:height="450px" width="700px"}{:class="image-centered"}

<small>Since the ACF still has a cyclical pattern, we need to remove trending by differencing by lag 1.</small>


<b>(2.3.2) De-Trending</b>

<small> We use the differencing transformation to remove the trend from our data. The differenced sequence is
inverted using the prior values from the original sequence, as the primer for each transformation applying
at lag 1. After de-trending, the variance is now 0.000002317563 which falls to a stationary time series. In
order to check whether our time series is stationary we used the Augmented Dickey-Fuller Test, to create a
hypothesis test. Null Hypothesis is that Xt is non-stationary and the alternative hypothesis Ha is stationary.
The test resulted in a significant p-value of 0.01951, so we reject the null hypothesis and conclude that our
time series is stationary.</small>

![Figure 6 ACF and PACF]({{ site.baseurl }}/assets/images/forecast/7.jpg){:height="450px" width="700px"}{:class="image-centered"}

<small> We can further see Figure 6 above having no seasonality nor trend. The ACF and PACF of the
log-transformed, deseasonalized, detrended data is shown in Model Building 3.1.</small>








