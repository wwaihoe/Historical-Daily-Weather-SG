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

