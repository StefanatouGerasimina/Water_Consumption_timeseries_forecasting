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



