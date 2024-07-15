# prophet-challenge
# Module 8 Prophet Challenge


## Background


The purpose of this challenge was to analyze financial and user search data for Mercado Libre, the most popular e-commerce site in Latin America. 


## Installation


The following libraries and dependencies are required to successfully run the project:
- !pip install prophet
- import pandas as pd
- from prophet import Prophet
- import datetime as dt
- import numpy as np
- %matplotlib inline


## Repository Files and Starter Code
- [Mercado Libre Google Hourly Search Trends](https://static.bc-edx.com/ai/ail-v-1-0/m8/lms/datasets/google_hourly_search_trends.csv) 

- forecasting_net_prophet.ipynb: starter code provided in the assignment


- forecasting_net_prophet_AKW_solution.ipynb: completed notebook with data analysis, visualizations, and solutions/answers


## Methodology
The project was completed in four steps using Google Colab:
1. Find unusual patterns in hourly Google search traffic
2. Mine the search traffic data for seasonality
3. Relate the search traffic to stock price patterns
4. Create a time series model with Prophet


## Solutions/Answers


- **Question:** Did the Google search traffic increase during the month that MercadoLibre released its financial results?
  
        Yes, traffic increased by approximately 8.6% in May 2020 compared to the monthly median value.


- **Question:** Are there any time based trends that you can see in the data?


        Searches vary significantly over the course of a day, with the highest volume occurring around midnight. In the morning, search volume sharply declines and reaches a low around 8-9 a.m., increasing throughout the remainder of the day. The steepest increases can be seen from 9 a.m. to 3 p.m. and from 8 p.m. to midnight.


        Tuesdays represent the highest average volume of searches. Searches steadily decline over the remainder of the work week and then plummet over the weekend, with Sundays the least active day for searches


        There is quite a bit of variability from week to week. Overall, the first quarter was the most active quarter for searching. The lowest week for searching is around week 35, as well as low points in the first and final weeks of the year, which corresponds with celebrations of winter holidays and celebrations of the new year. In the weeks leading up to these holidays, however, there is a relatively sharp increase in overall searches starting in week 40 that continues until around week 50.


- **Question:** Do both time series indicate a common trend that’s consistent with this narrative?


        Both time series indicate a common trend consistent with the initial shock of COVID lockdowns in March 2020. Both stock closing prices and search trends sharply declined in March 2020. The stock closing time series demonstrates that the closing price not only rebounded but steadily rose after this initial shock. Search trends also recovered after March 2020, but they did not demonstrate a period of growth; instead, they were relatively consistent, albeit slightly lower than prior to March 2020.



- **Question:** Does a predictable relationship exist between the lagged search traffic and the stock volatility or between the lagged search traffic and the stock price returns?

        There is a very weak negative correlation between lagged search traffic and stock volatility since the correlation coefficient is -0.15.

        There is almost no correlation between lagged search traffic and the hourly stock returns because the correlation coefficient is 0.02.


- **Question:**  How's the near-term forecast for the popularity of MercadoLibre?

        Overall, the forecast suggests that MercadoLibre's popularity will return to pretty consistent historic levels.


        Over the first twenty-some days, searches are predicted to plateau and then drop a little before rebounding and increasing around day 22 days. Searches will begin to increase and trend toward historical levels, albeit lower than MercadoLibre's previous peaks in popularity.
- **Question:** What time of day exhibits the greatest popularity?
    
        Midnight
- **Question:** Which day of week gets the most search traffic?
 
        Tuesday
- **Question:** What's the lowest point for search traffic in the calendar year?

        Between October and November




## Resources Consulted
For this challenge, I consulted the starter code files provided in the assignment, which are referenced above.


Additionally, the AI assistant in Colab, “Gemini” offered some suggestions of predictive code. 







