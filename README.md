# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 11.05.2026


### AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average temperature of a city/country and for airline passengers.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```
import pandas as pd
import matplotlib.pyplot as plt
import matplotlib.dates as mdates
from statsmodels.tsa.seasonal import seasonal_decompose

data = pd.read_csv(
    "Google_Stock_Price_Test.csv",
    parse_dates=['Date'],
    index_col='Date'
)

print(data.head())

stock_data = data['Close']

decomposition = seasonal_decompose(
    stock_data,
    model='additive',
    period=7
)

# Step 4: Plot the decomposition graphs
plt.figure(figsize=(10, 12))

# Original Data Plot
plt.subplot(411)
plt.plot(stock_data,
         label='Google Stock Close Price')
plt.legend(loc='upper left')
plt.title('Google Stock Price')

# Trend Plot
plt.subplot(412)
plt.plot(decomposition.trend,
         label='Trend',
         color='orange')
plt.legend(loc='upper left')
plt.title('Trend Plot')

# Seasonal Plot
plt.subplot(413)
plt.plot(decomposition.seasonal,
         label='Seasonal',
         color='green')
plt.legend(loc='upper left')
plt.title('Seasonality Plot')

# Residual Plot
plt.subplot(414)
plt.plot(decomposition.resid,
         label='Residual',
         color='red')
plt.legend(loc='upper left')
plt.title('Residual Plot')

for i in range(411, 415):
    plt.subplot(i)
    plt.gca().xaxis.set_major_formatter(
        mdates.DateFormatter('%Y-%m-%d')
    )
    plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```

### OUTPUT:
FIRST FIVE ROWS:

<img width="587" height="110" alt="image" src="https://github.com/user-attachments/assets/4f1db72d-df86-4fa2-842b-8784248bfee6" />

PLOTTING THE DATA:

<img width="921" height="282" alt="image" src="https://github.com/user-attachments/assets/74b0e3ad-7126-4ff9-aace-efb85995f908" />


SEASONAL PLOT REPRESENTATION :

<img width="917" height="287" alt="image" src="https://github.com/user-attachments/assets/329c21cf-56d0-4043-9b85-f540c80b89d8" />

TREND PLOT REPRESENTATION :

<img width="918" height="287" alt="image" src="https://github.com/user-attachments/assets/a4dca89a-1e9a-44a9-93f3-795ffeffc648" />

Residual Plot REPRESENTATION:

<img width="911" height="282" alt="image" src="https://github.com/user-attachments/assets/51a3a14d-20a9-4cfc-bf39-96e4224beb0d" />

### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
