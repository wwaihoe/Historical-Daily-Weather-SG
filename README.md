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
![Capture](https://user-images.githubusercontent.com/91514179/179922868-ce266a07-ddf5-4dce-9be1-fbf122c84f38.PNG)
- Increasing trend in mean temperature over the years and temperatures tend to bottom out at the start of the year and peak in the middle of the year.

- Highest temperature recorded was 36.6 degrees celsius on 4/3/14.

- Lowest temperature recorded was 21.6 degrees celsius on 22/1/10.

- Largest temperature range recorded was 13.3 degrees celsius, on 24/3/13, with a max temperature of 36.2 and min temperature of 22.9.

**Rainfall**
![Capture2](https://user-images.githubusercontent.com/91514179/179924074-15b4cad5-4853-478a-b74d-799db3c50317.PNG)
Highest total rainfall recorded was 142mm on 9/3/09.

**Windspeed**
![Capture3](https://user-images.githubusercontent.com/91514179/179924244-f3cf3846-b05b-46e4-8ed1-a0dcf8b601dd.PNG)
- Mean wind speed has an increasing trend over the years. Mean wind speed generally peaks at the start of the year and bottoms out in the middle of the year.

- Highest wind speed ever recorded was 86.8km/h on 21/3/12.
