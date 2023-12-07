# Water_Consumption_timeseries_forecasting


## Introduction

The scope of this project is the analysis of the time series for hourly 
water consumption data and the creation of a model to predict the daily water consumption for the next year.

The given dataset, provides hourly data on water consumption for the years 2002 to 2016 and consists of two columns:

- Datetime: This column records the date and time of the observation. The format used is 'YYYY-MM-DD HH:MM:SS’.
- Consumption: This column shows the water consumption, presumably measured in a specific unit during each  datetime.

An example of the hourly, daily and weekly water consumption timeseries is shown bellow:

*Hourly Water Consumption*

<img src="https://github.com/StefanatouGerasimina/Water_Consumption_timeseries_forecasting/blob/main/images/timeseries_hourly.png" width="700" height="320">

*Daily Water Consumption*

<img src="https://github.com/StefanatouGerasimina/Water_Consumption_timeseries_forecasting/blob/main/images/timeseries_daily.png" width="700" height="320">

*Weekly Water Consumption*

<img src="https://github.com/StefanatouGerasimina/Water_Consumption_timeseries_forecasting/blob/main/images/timeseries_weekly.png" width="700" height="320">

## Basic Statistics

- As we take a first look at the dataset's summary, we notice that there are no missing values.
- The average hourly water consumption goes up to 32187 units.
- Standard deviation of 6489.8 units.
- Minimum hourly water consumption of 14544.0 units.
- Maximum hourly water consumption of 62009.0 units.

## Timeseries Distribution

<img src="https://github.com/StefanatouGerasimina/Water_Consumption_timeseries_forecasting/blob/main/images/distribution.png" width="500" height="350">

- The distribution appears to be roughly bell-shaped, indicating a normal distribution. This suggests that most measurements fall near the mean, and the frequency decreases as you move away from the center in either direction.
- The spread or dispersion seems quite large, with significant frequencies ranging from about 10k to over 50k. This indicates a wide range of water consumption values among the measured subjects or entities.
- The distribution appears to be slightly skewed to the right, suggesting that there are more high consumption values than low consumption outliers. This is indicated by the long tail on the right side of the distribution. This refers to the positive skewness.

Positive skewness also can be shown from the wiskers diagram:

<img src="https://github.com/StefanatouGerasimina/Water_Consumption_timeseries_forecasting/blob/main/images/boxplot.png" width="350" height="350">

-The box itself shows the interquartile range, which is the middle 50% of the data. The bottom of the box is Q1, and the top is Q3. In this case, Q1 appears to be just above 20k, and Q3 is just under 40k.
-The boxplot seems to be not symmetrical, with the median closer to the bottom of the box and the upper whisker being longer than the lower whisker. This asymmetry suggests that the distribution of water consumption is positively skewed.
-The spread of water consumption is quite broad, with the bulk of values falling between 20k and 60k. The median consumption is around 35k, indicating that half of the observed values are below this amount and half are above.
- The longer upper whisker compared to the lower whisker indicates that there are consumption values that are significantly higher than the median, which may represent periods of high water use or larger consumers.

**Results**

Q1: 27.664

Q2: 31.543 

Q3: 35.762 => |Q2 - Q1| > |Q2 - Q3|


## Timeseries Components

<img src="https://github.com/StefanatouGerasimina/Water_Consumption_timeseries_forecasting/blob/main/images/timeseries_hourly.png" width="700" height="320">

The pattern seems regular and consists of consistent periods of high and low consumption, suggesting a deterministic seasonality. The variability is also evident with some spikes higher than others, which could be indicative of special events or seasonal changes affecting water usage.

<img src="https://github.com/StefanatouGerasimina/Water_Consumption_timeseries_forecasting/blob/main/images/timeseries_daily.png" width="700" height="320">

Using a daily plot for the year 2002, for simplicity reasons, it seems that it smooths out the hourly spikes but still shows variability from day to day. We can see some patterns that might correspond to specific days marking specific kind of consumption units.

<img src="https://github.com/StefanatouGerasimina/Water_Consumption_timeseries_forecasting/blob/main/images/timeseries_weekly.png" width="700" height="320">

The weekly averages demonstrate that the water consumption marks high spots during the summer months of a year, and lower ones during the cold season. Compared to the daily data, the weekly averages smooth out the noise, making it easier to observe the seasonal patterns.

## Timeseries Decomposition

### Trend

<img src="https://github.com/StefanatouGerasimina/Water_Consumption_timeseries_forecasting/blob/main/images/trend.png" width="700" height="320">
It doesn’t seem to be any specific strong trend for the water consumption, but it is noticeable a downward trend beginning around the year of 2008, suggesting a reduction in the water consumption ever since. Also, there seem to appear some cyclical patterns alternating between rises and falls, probable related to economic trends as well or other external influences.

### Seasonality

<img src="https://github.com/StefanatouGerasimina/Water_Consumption_timeseries_forecasting/blob/main/images/seasonality.png" width="700" height="320">
The seasonal component displays a yearly repeating pattern within the data at regular intervals. The sharp peaks and troughs suggest a strong influence of the season to the water consumption units , potentially related to population & agricultural needs or other periodic events. The steady variation, seems to be accurately captured by the additive model implanted for this decomposition. 

### Residual

<img src="https://github.com/StefanatouGerasimina/Water_Consumption_timeseries_forecasting/blob/main/images/residuals.png" width="700" height="320">
The residual plot displays the random fluctuations after the extraction of its trend and seasonality.  The plot exhibits occasional spikes, potentially indicating outliers or unusual occurrences not accounted for, by the model. However, the absence of a systematic pattern in the residuals is positive, indicating effective isolation of the trend and seasonal components from the initial data.

## Timeseries Correlation

### Lag plot

<img src="https://github.com/StefanatouGerasimina/Water_Consumption_timeseries_forecasting/blob/main/images/lag_plot.png" width="700" height="320">
Positive autocorrelation: Strong relation between the 2 sequenced daily water consumption units. In other words, high water consumption on one day is likely to be followed by high consumption the next day, and similar for the low values. There are some data points that deviate from the diagonal line, which could be outliers or anomalies, but overall the spread of the points is tight which suggests a strong autocorrelation between the data points.

### Autocorrelation Plot

<img src="https://github.com/StefanatouGerasimina/Water_Consumption_timeseries_forecasting/blob/main/images/auto_correlation.png" width="700" height="320">
The first bar indicates the autocorrelation at lag 1, which is close to 0.8 suggesting a strong autocorrelation from one day to another. There seems to be strong Positive Autocorrelation at shorter lags suggesting high day to day relationship in water consumption, while the Gradual decrease of autocorrelation over lag,  suggests that past values have significant effect on the future values, persistently.Finaly there might be a possible weekly seasonality, as the lags 7, 14 21 etc seem to have significant peeks.

## Stationarity

In order to create a sufficient time series forecasting model, we need consistency of distributions (Stationarity).  It doesn’t need to be strongly stationary a weak stationarity is also acceptable as long as the the way the variables relate to each other is consistent through time and depends only on the lag between each observations, while the mean and variance must remain constant over time.

### ADF Testing

H0: Null Hypothesis assuming the time series is non-stationary, based on the presence of a unit-root.
H1: Alternative Hypothesis proving the time series does not have a unit root, thus is stationary.

The ADF test statistic is calculated from the estimated coefficient on the lagged values of the time series. The more negative the test statistic, the stronger the rejection of the null hypothesis

**ADF STATISTIC**: -7.979174
**P VALUE**: 2.651789445842063e-12
**CRITICAL VALUES**: 1%: -3.432, 5%: -2.862, 10%: -2.567

**ADF Statistic:** The value of the ADF statistic indicates strongly against the null hypothesis, thus it suggests a unit root present.
**P-value:** The p value is indeed small, almost zero, suggesting that the null hypothesis can be rejected high quite high degree of confidence.
**Critical Values:** The ads value is more negative than the 1%, 5% and 10%, which means that we can reject the null hypothesis.

## Water Consumption Forecasting
For this water consumption forecasting, I implemented two different lstm models:
LSTM 1: LSTM layer - Dropout layer - Dense layer - Output layer
LSTM 2: LSTM layer - Dropout layer - LSTM layer - Dropout layer - Dense layer - Output layer

### LSTM1

#### 7 DAYS

**Accuracy**
<img src="https://github.com/StefanatouGerasimina/Water_Consumption_timeseries_forecasting/blob/main/images/l1_7_acc.png" width="700" height="320">
**Loss**
<img src="https://github.com/StefanatouGerasimina/Water_Consumption_timeseries_forecasting/blob/main/images/l1_7_loss.png" width="700" height="320">

#### 30 DAYS

**Accuracy**
<img src="https://github.com/StefanatouGerasimina/Water_Consumption_timeseries_forecasting/blob/main/images/l1_30_acc.png" width="700" height="320">
**Loss**
<img src="https://github.com/StefanatouGerasimina/Water_Consumption_timeseries_forecasting/blob/main/images/l1_30_loss.png" width="700" height="320">

#### 365 DAYS

**Accuracy**
<img src="https://github.com/StefanatouGerasimina/Water_Consumption_timeseries_forecasting/blob/main/images/l1_365_acc.png" width="700" height="320">
**Loss**
<img src="https://github.com/StefanatouGerasimina/Water_Consumption_timeseries_forecasting/blob/main/images/l1_365_loss.png" width="700" height="320">

#### Comparison and thoughts:

<img width="350" height="350" alt="image" src="https://github.com/StefanatouGerasimina/Water_Consumption_timeseries_forecasting/assets/63111398/fb5a8dd2-b62e-4838-a455-0da88313eeac">

- **RMSE** tends to highlight large errors more than MAE due to the squaring of errors. This can make RMSE more sensitive to outliers compared to MAE.
- **MAE** gives a linear representation of errors, meaning that all errors are treated equally.
- **MAPE** is a relative measure that expresses error as a percentage.
- As the look-back period increases, all three metrics show improvement. This suggests that including more historical data helps the model make more accurate predictions.
- The model with a look-back of 365 days performs the best, followed by 30 days and then 7 days. This could indicate that there are long-term patterns or seasonal trends in the data that are being better captured by the longer look-back periods.

**RMSE**: 
- The RMSE decreases as the look-back period increases. Since RMSE gives a higher weight to larger errors, the decreasing trend suggests that the model with a longer look-back is making fewer large errors.
- The significant decrease in RMSE when moving from a 7-day to a 365-day look-back period suggests that the annual patterns are important and that the model benefits from considering a full year's data.

**MAE:**
- The MAE also decreases with an increase in the look-back period, which suggests a reduction in the average magnitude of errors. Like RMSE, the improvement in MAE suggests the model's predictions are getting closer to the actual values with a longer look-back.

**MAPE:**
- The MAPE decreases with an increase in the look-back period, indicating that the relative size of the prediction errors compared to the actual values is getting smaller. This is a good sign, especially if the scale of the data and the magnitude of the water consumption values do not change significantly over time.
- A MAPE of 4.22% for the 365-day look-back is quite low, indicating that the predictions are, on average, within 4.22% of the actual values.


- The RMSE being higher than the MAE suggests that there are significant outliers or large variances in some of the errors. 
- A MAPE of under 5% indicates that the model's predictions are relatively close to the actual values in percentage terms. However, depending on the domain, a 5% error rate may or may not be acceptable.

### LSTM2

#### 7 DAYS

**Accuracy**
<img src="https://github.com/StefanatouGerasimina/Water_Consumption_timeseries_forecasting/blob/main/images/l2_7_acc.png" width="700" height="320">
**Loss**
<img src="https://github.com/StefanatouGerasimina/Water_Consumption_timeseries_forecasting/blob/main/images/l2_7_loss.png" width="700" height="320">

#### 30 DAYS

**Accuracy**
<img src="https://github.com/StefanatouGerasimina/Water_Consumption_timeseries_forecasting/blob/main/images/l2_30_acc.png" width="700" height="320">

**Loss**
<img src="https://github.com/StefanatouGerasimina/Water_Consumption_timeseries_forecasting/blob/main/images/l2_30_loss.png" width="700" height="320">
#### 365 DAYS

**Accuracy**
<img src="https://github.com/StefanatouGerasimina/Water_Consumption_timeseries_forecasting/blob/main/images/l2_365_acc.png" width="700" height="320">

**Loss**
<img src="https://github.com/StefanatouGerasimina/Water_Consumption_timeseries_forecasting/blob/main/images/l2_365_loss.png" width="700" height="320">

#### Comparison and thoughts:
<img width="350" height="350" alt="image" src="https://github.com/StefanatouGerasimina/Water_Consumption_timeseries_forecasting/assets/63111398/f3596651-86ba-4247-814f-dc9ae7b52218">

- As the look-back period increases, the model's predictive accuracy improves, which is evident from the decreasing RMSE and MAE. This suggests that including more historical data allows the LSTM to capture long-term dependencies and trends in water consumption more effectively.

- The MAPE values are relatively similar across all look-back periods, suggesting that the model's predictions are generally close to the actual values in percentage terms. However, even small percentage errors can result in large absolute errors when dealing with large numbers, which might be the case here.

- The slight increase in MAPE from 30 days to 365 days, despite improvements in RMSE and MAE, might indicate that while the larger errors are being reduced, smaller errors are having a more significant impact on the MAPE. This could occur if the model's predictions are more consistently close but still not perfect.

### Considerations and next steps:

- The model with a 365-day look-back period doesn't show a substantial improvement in MAPE compared to the 30-day model, which might suggest that a 30-day period strikes a better balance between performance and computational efficiency.
- The improvement in RMSE and MAE with a longer look-back indicates that the model is capturing more of the variance in the data, which can be crucial for making accurate predictions in practice.
- Consider using a longer look-back period. If the slight increase in accuracy is not critical to decision-making, a shorter look-back period may be preferred.
- Further model tuning might be possible to improve performance, such as adjusting the number of LSTM units, adding more layers, or experimenting with different dropout rates, size of units etc.
- Conduct additional diagnostics such as plotting residuals over time to ensure there are no remaining patterns that the model is failing to capture.

### Interpretation and final thoughts:

**Thoughts:**
For both models, as the look-back period increases, the RMSE and MAE decrease, suggesting that having more historical data improves the models' predictive accuracy.
The MAPE also generally decreases as the look-back period increases, suggesting that the models are becoming more accurate in percentage terms with more context.

**Comparison:**
The second model is slightly more complex due to the additional LSTM layer, which may require more computational resources. However, this complexity does not translate into a significant improvement in MAPE for the longer look-back periods, as shown in the tables above.
The first model, despite being simpler, shows very competitive performance and even a slightly better MAPE for the 365-day look-back, suggesting that a simpler list model can successfully capture the patterns and components of the water consumption data.

**Improvements:**
Consider the possibility of overfitting especially on the second more complex network, and apply techniques to overcome it.
Both models may benefit from further hyperparameter tuning, additional feature engineering, or using a different architecture altogether.
Use a base model, coming from a research to be able to compare the results much more efficient.
