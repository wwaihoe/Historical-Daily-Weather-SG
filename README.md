# Historical-Daily-Weather-SG
 
## Introduction

Exploring a dataset containing daily weather recordings of Singapore to learn about time series analysis and forecasting. Dataset includes temperature, wind speed, rainfall and dates of recordings. 

Dataset retrieved from data.gov.sg, managed by National Environmental Agency. 
https://data.gov.sg/dataset/historical-daily-weather


## Data Preparation

- Dropped highest rainfall columns as more than half of the values were missing.
- Set date as index.
- Added missing dates and used linear interpolation to fill in missing values in the recordings.
- Added temperature range column.
- Checked for erroneous values using boxplots of all colunmns. (None to be found)


## Data Analysis
**Temperature**

![Capture](https://user-images.githubusercontent.com/91514179/179925980-98e53e92-11a9-40d9-b0af-75e58d6e51bb.PNG)
- Increasing trend in mean temperature over the years and temperatures tend to bottom out at the start of the year and peak in the middle of the year.
- Highest temperature recorded was 36.6 degrees celsius on 4/3/14.
- Lowest temperature recorded was 21.6 degrees celsius on 22/1/10.
- Largest temperature range recorded was 13.3 degrees celsius, on 24/3/13, with a max temperature of 36.2 and min temperature of 22.9.

**Rainfall**

![Capture1](https://user-images.githubusercontent.com/91514179/179926144-663d52d7-fe90-4bcb-af84-18655b7e8ef0.PNG)
- Highest total rainfall recorded was 142mm on 9/3/09.

**Windspeed**

![Capture2](https://user-images.githubusercontent.com/91514179/179926272-c8bc6ded-d3df-422a-b7e5-368393de518d.PNG)
- Mean wind speed has an increasing trend over the years. Mean wind speed generally peaks at the start of the year and bottoms out in the middle of the year.
- Highest wind speed ever recorded was 86.8km/h on 21/3/12.

**Correlation**

![Capture3](https://user-images.githubusercontent.com/91514179/179926535-24037500-91a2-45e3-81a6-c1d8c7e61bfd.PNG)
- Daily total rainfall had the strongest linear relationship with mean temperature.


## Time Series Decomposition of Mean Temperature
- Seasonal-Trend decomposition with LOESS

**Daily Time Series**

![Capture4](https://user-images.githubusercontent.com/91514179/180141229-6c353725-530d-428d-9990-091a1feac6ae.PNG)
- Slight upward trend in mean temperatures as observed earlier with peaks at the end of 2009 and 2015. 
- Seasonality with peaks in the middle of the year and troughs at the start/end of the year.

**Monthly Time Series**

- Created new dataframe containing monthly aggregates.

![Capture5](https://user-images.githubusercontent.com/91514179/180142538-042554d1-e7d1-42df-b3d8-6bd4df3e5f24.PNG)
- An expected general increasing trend in mean temperatures with spikes from 2009 to 2010 and 2015 to 2016
- Looking at the seasonsality, mean temperatures peak in May and June and are lowest in January and February.


## Time Series Forecasting

### Statistical Methods (using only mean_temperature)

#### Holt-Winters Exponential Smoothing (HWES)

- 80-20 Train and test data split
- Multiplicative seasonal component

**Daily Time Series**

![Capture6](https://user-images.githubusercontent.com/91514179/180143265-101e787e-60c8-4a0b-95e8-692ed1afc358.PNG)
- Mean absolute error: 0.7294548714374061
- Root mean squared error: 0.951163708477206

**Monthly Time Series**

![Capture8](https://user-images.githubusercontent.com/91514179/180143999-92fac185-7993-4c0d-bd6a-76dab3188db0.PNG)
- Mean absolute error: 0.4720459238247769
- Root mean squared error: 0.5463534143293616
- Easier for model to forecast monthly mean temperatures with less fluctuations compared to daily time series.


#### Seasonal Autoregressive Integrated Moving Average (SARIMA) (Monthly Time Series)

- Used auto_arima from pmdarima to find optimal order for model

![Capture9](https://user-images.githubusercontent.com/91514179/180145862-7bed07e5-44d1-4537-bb96-363dffc833f1.PNG)
- Mean absolute error: 0.2342953586273681
- Root mean squared error: 0.2947873272498163
- Better performance compared to HWES


### Machine Learning

#### RNN - Long Short-term Memory (LSTM) (Using all features to predict mean_temperature)

- 60-20-20 Train, validation and test data split
- Standardisation of data to have mean of 0 and std of 1.

**Daily Time Series**

- Window: Predict mean temperature for 1 day given the data from previous 30 days.

![Capture11](https://user-images.githubusercontent.com/91514179/180151740-821f5610-0018-4a70-9dc7-583be17989cd.PNG)
- Example of windows used for model

![Capture10](https://user-images.githubusercontent.com/91514179/180150150-5a6f5413-6341-4df5-9d1e-1b004796d529.PNG)
- Validation Mean absolute error: 0.5088
- Test Mean absolute error: 0.4547


**Monthly Time Series**

- Window: Predict mean temperature for 1 month given the data from previous 5 months

![Capture12](https://user-images.githubusercontent.com/91514179/180152281-304d297e-5ae9-4e79-9260-ba1589706e80.PNG)
- Example of windows used for model

![Capture13](https://user-images.githubusercontent.com/91514179/180152415-4f31fca4-a2df-4833-a9d9-fe45de13de9b.PNG)
- Validation Mean absolute error: 0.5343
- Test Mean absolute error: 0.2432
