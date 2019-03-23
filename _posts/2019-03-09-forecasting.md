---
layout: post
title:  "Time Series Analysis: Wisconsin Employment"
author: Amir O, Jesus Q, Cesar Ps, Even Q, Mohammad K
categories: [ scholar ]
hidden: false
image: "https://22xmcq37bnw82iclyj35wony-wpengine.netdna-ssl.com/wp-content/uploads/2017/05/sales-forecasting-metrics-1024x768.jpg"
---

## <center>Time Series Analysis: Wisconsin Employment</center>
## <center>1961-1975 </center>
<center><small>Author: Amir O, Jesus Q, Cesar Ps, Even Q, Mohammad K</small></center>

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

![ACF and PACF]({{ site.baseurl }}/assets/images/forecast/2.jpg){:height="230px" width="450px"}{:class="image-centered"}
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

![two models Figure 3]({{ site.baseurl }}/assets/images/forecast/4.jpg){:height="250px" width="500px"}{:class="image-centered"}

{% include advertisements.html %}

<b>(2.2.2) Log Transformation</b>

<small>In order to make the data stationary and stabilize the variance, we used logarithmic transformation. Since
it has the lowest variance compared to the Box-Cox transformation. The variance for the box-cox transformation
is 0.247729 and was reduced to 0.0197 after using logarithmic transformation. Therefore, we picked
logarithmic transformation as our best transformation.</small>
![Figure 4 ACF and PACF]({{ site.baseurl }}/assets/images/forecast/5.jpg){:height="250px" width="600px"}{:class="image-centered"}

<small>The slow decay of the autocorrelations in figure 4 is similar to the original dataset indicating that our
data is still non-stationary. Thus, we remove the seasonality and trend in the next step.</small>

# (2.3) Differencing

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

![Figure 6 ACF and PACF]({{ site.baseurl }}/assets/images/forecast/7.jpg){:height="250px" width="600px"}{:class="image-centered"}

<small> We can further see Figure 6 above having no seasonality nor trend. The ACF and PACF of the
log-transformed, deseasonalized, detrended data is shown in Model Building 3.1.</small>

# (3) Model Building

<small>After removing the trend and seasonality to produce a stationary series, we can fit the data into a SARIMA
model. A SARIMA model is illustrated by SARIMA(p, d, q)x(P,D,Q)s where p = non-seasonal AR order, d
= non-seasonal differencing, q = non-seasonal MA order, P = seasonal AR order, D = seasonal differencing,
Q = seasonal MA order, and S = the length of the season. As the data was collected monthly from
1961 to 1975 we analyzed Figure 7: ACF and PACF of log transformed, seasonalized detrended data The
autocorrelation function of seasonalized detrended data providing D = 1 and S = 12 since we difference at
lag 12 then differenced again at lag 1 to remove trend giving d = D = 1. The trend elements can be chosen
through careful analysis of ACF and PACF plots by looking at the correlations of recent time steps to p, q
and P, Q based off ACF and PACF of the data below in Figure 7..</small>


<b>(3.1) Ananlyzing ACF and PACF</b>

<small> We find the components of P, Q, p and q. First, we look at the first season lags (1-11) to find our p and
q. None are significantly outside the confidence interval which would suggest p = 0 and q = 0 by looking
at ACF. To determine the order of seasonal components P and Q we observe more notable lags at 12, 24
and 36 with a significant lag in the ACF graph at lag 12. When we differenced at lag 12, it resulted in an
SMA component of 1 so P=1. If we compare lag 12 on PACF suggesting SAR component of 1, so Q = 1.
In order to verify our assumption, we build three models based on P = 1 or 0 and Q = 1 or 0 to see which
significant coefficients and low AIC. </small>


![Figure 7 ACF and PACF]({{ site.baseurl }}/assets/images/forecast/8.jpg){:height="250px" width="4500px"}{:class="image-centered"}

<b> (3.2) Model Selection </b> 

<small> Based on our model building criteria, we select the best model for our forecast. We have three models
Model 1 = SARIMA(0, 1, 0)x(0, 1, 1)12 , Model 2 = SARIMA(0, 1, 0)x(1, 1, 0)12 and Model 3 =
SARIMA(0, 1, 0)x(1, 1, 1)12. Of these possible models we identify which model with the lowest AICs and
significant coefficients: coefficients whose absolute value is greater than their standard error values.</small>

![chart]({{ site.baseurl }}/assets/images/forecast/9.jpg){:height="250px" width="4000px"}{:class="image-centered"}

<small> The only model with significant coefficients is Model 2 based on the table above with d = D = 1, P = 0,
p = 0, Q = 1, q = 0 and the second lowest AIC is P = 1 and Q = 1.</small>

<b>(3.3) Model Fitting </b>

<small> In the final analysis, we decided to pick Model 2 as our best SARIMA(0,1,0)x(1,1,0)12. We examined the
roots of the polynomials to check for causality and invertibility. After plotting the roots in red, it was
apparent that the inverse roots lie within the unit circle for both models. We take the absolute values for
all the coefficients that are less than 1 which means they are outside of the unit circle. Thus, we conclude
model 2 is invertible and casual. </small> 

![Inverse Unit Circle]({{ site.baseurl }}/assets/images/forecast/10.jpg){:height="250px" width="500px"}{:class="image-centered"}

#### (3.4) Diagnotics 

<b> (3.4.1) Normality </b>

<small> Another way of checking whether the condition of normality holds in our model is by plotting the residuals on
a Q-Q (Quantile-Quantile) plot, as well as checking their frequencies using a histogram. Using the qqnorm()
function we see our QQ plot is approximately linear which supports our assumption of normality. Moreover,
it is observed that our histogram doesn’t present outliers or skewness in the data, which would present itself
in the form of tails in the graph.</small>


![Figure 7]({{ site.baseurl }}/assets/images/forecast/11.jpg){:height="250px" width="450px"}{:class="image-centered"}

<b> (3.4.2) Independence </b> 

<small> To examine whether or not our model satisfies the condition of normality, we performed both the Box-Pierce
and Ljung-Box test. As shown above, the p-values were calculated to be 0.6192 and 0.6224. Therefore, we
fail to reject the null hypothesis and say with confidence that our model is normal since both p-values  ￿
=.05. </small>
![chart]({{ site.baseurl }}/assets/images/forecast/12.jpg){:height="250px" width="450px"}{:class="image-centered"}

{% include advertisements.html %}

## FORECASTING

<small> Using model 2, we back transformed the logarithmically transformation data by taking the exponential
transformation of the logarithmically transformed data. We can observe the 14 forecasted values in the form
of red circles in figure 8 from September 1974 to October 1975, along with the 95% confidence intervals for
these forecasted values. We cut the last 14 months as our testing data for comparison with our forecasted
values. </small>

![figure 8]({{ site.baseurl }}/assets/images/forecast/13.jpg){:height="250px" width="600px"}{:class="image-centered"}
<small>This final model captures the overall trend and seasonality of the data. Figure 9 shows a zoomed-in view
of the forecasted values resembling the obvious patterns of our original data. The observed and forecasted
values are very close throughout the season which proves the success of our final model.</small>

![figure 9]({{ site.baseurl }}/assets/images/forecast/14.jpg){:height="250px" width="500px"}{:class="image-centered"}

## Conclusion 
<small>Given the monthly data from January 1961 to August 1974, we were able to predict with a 95% confidence
the employment figures until October 1975. We began our analysis of the data by removing all seasonality
and trend by differencing at lag 12 and at lag 1, respectively. Then we attempted a Box-Cox transformation
of the data but later found the logarithmic transformation was more appropriate with lower variance. We
continued our analysis of the data by analyzing the the ACF and PACF graphs and were able to narrow
our focus on 3 SARIMA models. With similar AICs we found that SARIMA(0,1,0)x(1,1,0)12 had significant
coefficients that captures best the overall trend and seasonality of the data. The coefficients for our model
were calculated by figuring out the roots for the MA and AR component of the model, and confirmed with the
arima() function in R. Lastly, we were able to predict the final 14 months of our data with 95% confidence.Our final model
Model2 = SARIMA(0, 1, 0)x(1, 1, 0)12. We will like to thank Professor Bapat for working with us outside of the classroom, email and profoundly inspiring everybody to apply our Time Series knowledge into practice. </small>

## References
<small>[1] Labour market, Source: Hipel and McLeod (1994), in file: wisconsi/trade, Description: Wisconsin
employment time series, trade, Jan. 1961 – OCt. 1975 (https://datamarket.com/data/set/22l8/
wisconsin-employment-time-series-trade-jan-1961-oct-1975#!ds=22l8&display=line)October 2018 </small>

<small>[2] TheBalance, source: Types of https://www.thebalance.com/types-of-unemployment-3305522,Aug
14,2018. Used November 2018 </small>

<small>[3] Hyndsight, Plotting the Characteristics roots for ARIMA models(https://robjhyndman.com/
hyndsight/arma-roots/).Dec2 018</small>

## APPENDEX

```
setwd("~/Desktop/project1")
dat0 = read.table("wisconsin-employment-time-series.csv", header = F,
sep = ",")
head(dat0)
tail(dat0)
dat0 <- ts(dat0[, 2], start = c(1961, 1), end = c(1975, 1), frequency = 12)
var(dat0)
# remove 14 data points from original data to compare
# forecasting accuracy
dat <- dat0[-c(165:178)]
ts.plot(dat0, xlab = "years", ylab = "employment")
acf(dat, lag.max = 150, main = "ACF")
pacf(dat, lag.max = 150, main = "PACF")

library(MASS)
t = 1:length(dat)
fit = lm(dat ~ t)
bcTransform = boxcox(dat ~ t, plotit = TRUE)
lambda = bcTransform$x[which(bcTransform$y == max(bcTransform$y))]
dat.bc = (1/lambda) * (dat^lambda - 1)
title("Figure 3: Log-Likelihood of Box Cox transformation")

ts.plot(dat.bc, main = "Figure 3: Box-Cox tranformed data", ylab = expression(Y[t]))
var(dat) This is the variance of the normal plot
# var(dat.bc) variance after the Box

dat.log = log(dat)
var(dat)
var(dat.bc)
var(dat.log)

acf(dat.log, lag.max = 150, main = "ACF")
pacf(dat.log, lag.max = 150, main = "PACF")

# seasonalize: difference at lag 12
y12 = diff(dat.log, 12)
var(y12)
acf(y12, lag.max = 150, main = "ACF")
pacf(y12, lag.max = 150, main = "PACF")

# detrend: difference at lag 1

y1 = diff(y12, 1)

ts.plot(y1, main = "De-trended Time Series", ylab = expression(nabla ~
Y[t]))
abline(h = 0, lty = 2)

ts.plot(y1, main = "Figure 6: De-trended/seasonalized Time Series",
ylab = expression(nabla^{
12
} ~ nabla ~ Y[t]))
abline(h = 0, lty = 2)

library(tseries)
adf.test(y1, k = 12)
acf(y1, lag.max = 150, main = "ACF")
pacf(y1, lag.max = 150, main = "PACF")
# with d = D = 1, P = 1, p = q = 0, Q = 1 we have the lowest
# AIC selecting SARIMA(0,1,0)X(0,1,1) model.

model_fit1 = arima(dat.log, order = c(0, 1, 0), seasonal = list(order = c(0,
1, 1), period = 12), method = "ML", xreg = 1:length(dat.log))
model_fit1

# with d = D = 1, P = 0, p = 0, Q = 1, q = 0 we have the 1st
# lowest AIC selecting SARIMA(0,1,0)x(0,1,1) model.

model_fit2 = arima(dat.log, order = c(0, 1, 0), seasonal = list(order = c(1,
1, 0), period = 12), method = "ML", xreg = 1:length(dat.log))
model_fit2

# with d = D = 1, P = 1, p = 0, Q = 1, q = 0 we have the 2nd
# lowest AIC selecting SARIMA(0,1,0)x(1,1,1) model.

model_fit3 = arima(dat.log, order = c(0, 1, 0), seasonal = list(order = c(1,
1, 1), period = 12), method = "ML", xreg = 1:length(dat.log))
model_fit3

library(dse)
library(forecast)
library(ggplot2)

fit <- Arima(dat.log, order = c(0, 1, 0), seasonal = list(order = c(0,
1, 1), period = 12), xreg = 1:length(dat.log))
# SARIMA(0,1,1)x(0,1,1) model roots
autoplot(fit)
autoplot(model_fit2)

Box.test(residuals(model_fit2), type = "Ljung")
Box.test(residuals(model_fit2), type = "Box-Pierce")
shapiro.test(residuals(model_fit2))
op = par(mfrow = c(1, 2))
qqnorm(residuals(model_fit2), main = "")
qqline(residuals(model_fit2))
hist(residuals(model_fit2), main = "")
title("Figure 7: QQ Plot and Histogram", line = -1, outer = TRUE)

Box.test(residuals(model_fit2), type = "Ljung")
Box.test(residuals(model_fit2), type = "Box-Pierce")
shapiro.test(residuals(model_fit2))

op = par(mfrow = c(1, 2))

# full view
len <- length(model_fit2)
dat_last14 <- dat0[165:178] # last 14 entries from time series data
mypred <- predict(model_fit2, n.ahead = len, newxreg = (length(dat) +
1):(length(dat) + 14))
# model_ts <- ts(model_fit2) back transforming the log
# transformed data by taking the exponential function of the
# data
pred.orig <- exp(mypred$pred)
pred.se.upper <- exp(mypred$pred + 1.96 * mypred$se)
pred.se.lower <- exp(mypred$pred - 1.96 * mypred$se)
ts.plot(dat, main = "Figure 8: Wisconsin employment data forecasted",
xlim = c(1, length(dat) + 14), ylim = c(230, 430))
points((length(dat) + 1):(length(dat) + 14), pred.orig, col = "red")
lines(pred.se.upper, lty = 2, col = "steelblue")
lines(pred.se.lower, lty = 2, col = "steelblue")
# points((length(dat)+1):(length(dat)+14),dat_last14,
# pch='*', col='black')

# zoomed in view
ts.plot(dat, main = "Figure 9: Wiscounsin employment data forecasted",
xlim = c(length(dat) - 8, length(dat) + 14), ylim = c(320,
430), xlab = "months", ylab = "Wiscounsin employment data")
points((length(dat) + 1):(length(dat) + 14), pred.orig, col = "red")
lines(pred.se.upper, lty = 2, col = "steelblue")
lines(pred.se.lower, lty = 2, col = "steelblue")
points((length(dat) + 1):(length(dat) + 14), dat_last14, pch = "*",
col = "black")
legend("bottomright", c("observed data", "95% confidence interval"),
bg = "white", lty = c(1, 2), lwd = c(1, 1), col = c("black",
"steelblue"))
legend("bottomleft", c("forecasted data", "observed data"), bg = "aliceblue",
pch = c(1, 8), col = c("red", "black"))

```

©GoNumero








