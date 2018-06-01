# Anomaly-Detection-Case-Studies
The cases here are ones used in my Anomaly Detection course. We performed Exploratory Data Analysis (EDA) and 
then engineered new features to aid in the final analysis to detect anomalies in the data.

## Case 1: Financial Markets
Combined >7k data files to create a >14.8 mil row by 7 column data set. After EDA I created 10 new features evaluating risk and return. The final dataset was almost 3GB and required skills in memory management and function selection to be able to work with. My laptop only has 8GB of RAM and 2 cores which limited the types of functions I could use. One example, using certain functions together to combine the data sets I was able to reduce it to 11 minutes.

### Merge all the files into one master

Combine all the data to make it easier to create features and apply them accross all stocks.

### Build Features

Added Features: Returns, CumReturns, Covarriance's, Variance, Sharp Ratio, Normalized variance, z-score, high-bound, low-bound, binary out-of-bound

#### Log Returns

  What does the distribution of Open and Close prices look like.
  
  ![alt text](https://github.com/hall24/Anomaly-Detection-Case-Studies/blob/master/images/HW1_2.PNG)

  When comparing stocks the most common metric used is returns. When analyzing returns and market behavior it is customary to use log returns with is log(1+r). My returns feature is therefore log returns. [Why Log Returns?](https://quantivity.wordpress.com/2011/02/21/why-log-returns/)  
 
 ![alt text](https://github.com/hall24/Anomaly-Detection-Case-Studies/blob/master/images/HW1_1.PNG)
  
  The distribuion looks okay but some obvious outliers stand out. After investigating a few occurances they are infact errors in the data. When compared with Yahoo Finance the sample of 5 random occurances all had normal open and close prices that would have produced a return value closer to the distribution.
  
  Let's look at returns over time.
  
   ![alt text](https://github.com/hall24/Anomaly-Detection-Case-Studies/blob/master/images/HW1_3.PNG)

### Cumulative Returns

  Cumulative returns is a way to evaluate overall returns for a specific investment. This can be used to evaluate a break even point, cash-out point, or other specific goals. 
  
 ![alt text](https://github.com/hall24/Anomaly-Detection-Case-Studies/blob/master/images/HW1_4.PNG)
 

### Rolling Mean

  Another way to evaluate the value of a stock is its future value. This can be measured in many ways but the most common is its Expected returns. There are many ways to calculate this value. Some common way's are a simple, moving, moving exponential, or weighted average. The wieghts can be set for various reasons one of which is to create a recency bias. I will use a simple rolling average.
  
  ![alt text](https://github.com/hall24/Anomaly-Detection-Case-Studies/blob/master/images/HW1_5.PNG)

### Rolling Varriance

  Risk is the other aspect of stocks that is used to evaluate performance. Variance, covariance, and standard deviation are different measurements of risk. I will caculate a rolling variance and cumulative variance to try to capture a short term and long term risk feature. 
  
  ![alt text](https://github.com/hall24/Anomaly-Detection-Case-Studies/blob/master/images/HW1_6.PNG)
  
### Sharp Ratio 

  A performance measurement that describes the relationship between risk and return is the sharp ratio. This is used to measure returns over risk. The higher the value the better the score. The equation is (Returns - (risk free rate)) / sqrt(variance).
  
  ![alt text](https://github.com/hall24/Anomaly-Detection-Case-Studies/blob/master/images/HW1_7.PNG)

### Normalized Variance

  One measurement relative to risk that might be interesting is to find out how risky the short term period is relative to the long-term. Therefore normalizing the the risk will allow you to determine if the short term risk is beyond a certain distance, or evaluate the likelyhood of a the short term risk.

### Binary out-of-bounds > +- 1.96 SD's 

This indicator is just an easy way to identify those values that are beyond the 95% quantile for risk. This is a transformation of NormVar. I want to know how many times the risk or variance of stocks goes outside of the expected bounds. I expect no more than 5% since that is the limit I set NormVar. It turns out about 0.7% of observations are OOB. I find it curious that less than 1% of all varianc measurments occure outside the boundaries. This could be due to the fact that we are using a rolling variance and not a more academic approach to calculating variance.

  ![alt text](https://github.com/hall24/Anomaly-Detection-Case-Studies/blob/master/images/HW1_8.PNG)

### Visualizing Corrolations



## Case 2: Telemetry

## Case 3: Credit Card Transaction Fraud

## Case 4: Healthcare Fraud
