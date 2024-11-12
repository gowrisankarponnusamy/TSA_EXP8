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
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import warnings
from statsmodels.tsa.holtwinters import ExponentialSmoothing
warnings.filterwarnings('ignore')



data = pd.read_csv('raw_sales.csv')

print("Shape of the dataset:", data.shape)
print("First 20 rows of the dataset:")
print(data.head(20))

data['datesold'] = pd.to_datetime(data['datesold'])
data.set_index('datesold', inplace=True)

plt.figure(figsize=(12, 6))
plt.plot(data['price'], label='Original Price', color='blue')
plt.title('Original Price Data')
plt.xlabel('Date')
plt.ylabel('Price')
plt.legend()
plt.grid()
plt.show()

rolling_mean_3 = data['price'].rolling(window=3).mean()

plt.figure(figsize=(12, 6))
plt.plot(data['price'], label='Original Price', color='blue')
plt.plot(rolling_mean_3, label='Moving Average (window=3)', color='red')
plt.title('Moving Average of Price')
plt.xlabel('Date')
plt.ylabel('Price')
plt.legend()
plt.grid()
plt.show()

model = ExponentialSmoothing(data['price'], trend='add', seasonal=None)
model_fit = model.fit()

future_steps = 5
predictions = model_fit.predict(start=len(data), end=len(data) + future_steps - 1)

future_dates = pd.date_range(start=data.index[-1] + pd.Timedelta(days=1), periods=future_steps)

plt.figure(figsize=(12, 6))
plt.plot(data['price'], label='Original Price', color='blue')
plt.plot(future_dates, predictions, label='Exponential Smoothing Forecast', color='red')
plt.title('Exponential Smoothing Predictions for Price')
plt.xlabel('Date')
plt.ylabel('Price')
plt.legend()
plt.xticks(rotation=45)
plt.grid(True)
plt.tight_layout()
plt.show()

```

### OUTPUT:
### Given data:
![image](https://github.com/user-attachments/assets/aa0414f4-5145-4ca5-9cf2-2e720dc1a12c)

### Moving Average
![image](https://github.com/user-attachments/assets/404e61d5-802b-4e28-b157-975a52e9b685)

### Plot Transform Dataset
![Uploading image.png…]()

### Exponential Smoothing
![Uploading image.png…]()


### RESULT:
Thus we have successfully implemented the Moving Average Model and Exponential smoothing using python.
