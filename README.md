### DEVELOPED BY : GOWRISANKAR P 
### REG NO : 212222230041
# Ex.No: 08     MOVINTG AVERAGE MODEL AND EXPONENTIAL SMOOTHING
### Date: 


### AIM:
To implement Moving Average Model and Exponential smoothing Using Python.
### ALGORITHM:
1. Import necessary libraries
2. Read the Final uso data from a CSV file,Display the shape and the first 20 rows of
the dataset
3. Set the figure size for plots
4. Suppress warnings
5. Plot the first 50 values of the 'Value' column
6. Perform rolling average transformation with a window size of 5
7. Display the first 10 values of the rolling mean
8. Perform rolling average transformation with a window size of 10
9. Create a new figure for plotting,Plot the original data and fitted value
10. Show the plot
11. Also perform exponential smoothing and plot the graph
### PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.api import SimpleExpSmoothing

file_path = 'FINAL_USO.csv'
data = pd.read_csv(file_path)

data['Date'] = pd.to_datetime(data['Date'])
data.set_index('Date', inplace=True)

close_prices = data['USO_Close']

print("Shape of the dataset:", data.shape)
print(data.head(20))

plt.figure(figsize=(10, 6))

import warnings
warnings.filterwarnings("ignore")

plt.plot(close_prices.head(50), label='Original Data')
plt.title('First 50 USO_Close Prices')
plt.xlabel('Date')
plt.ylabel('USO Close Price')
plt.grid(True)
plt.legend()
plt.show(
rolling_mean_5 = close_prices.rolling(window=5).mean()

print("First 10 values of rolling mean (window=5):")
print(rolling_mean_5.head(10))

rolling_mean_10 = close_prices.rolling(window=10).mean()

plt.figure(figsize=(10, 6))

plt.plot(close_prices, label='Original Data')
plt.plot(rolling_mean_5, label='Rolling Mean (window=5)', color='orange')
plt.plot(rolling_mean_10, label='Rolling Mean (window=10)', color='red')
plt.title('USO Close Price with Rolling Mean')
plt.xlabel('Date')
plt.ylabel('USO Close Price')
plt.legend()
plt.grid(True)
plt.show()

exp_smoothing = SimpleExpSmoothing(close_prices.dropna()).fit(smoothing_level=0.2, optimized=False)
plt.show()
+
plt.figure(figsize=(10, 6))
plt.plot(close_prices, label='Original Data')
plt.plot(exp_smoothing.fittedvalues, label='Exponential Smoothing', color='green')
plt.title('USO Close Price with Exponential Smoothing')
plt.xlabel('Date')
plt.ylabel('USO Close Price')
plt.legend()
plt.grid(True)
plt.show()

```

### OUTPUT:

### Moving Average
![image](https://github.com/user-attachments/assets/e1558536-af0a-4fc3-84f7-495c39194ba2)

### Plot Transform Dataset
![image](https://github.com/user-attachments/assets/a2addd76-a413-4aa9-8bfb-c03da2acf1ee)

### Exponential Smoothing
![image](https://github.com/user-attachments/assets/1417efb2-51ce-4d3f-b5d5-2d34fe66370d)

### RESULT:
Thus we have successfully implemented the Moving Average Model and Exponential smoothing using python.
