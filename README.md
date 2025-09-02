# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
Date: 02-09-2025

### AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.
### ALGORITHM:
1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Implement the correlation using necessary logic and obtain the results
4. Store the results in an array
5. Represent the result in graphical representation as given below.
### PROGRAM:
```
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd

data=pd.read_csv("/content/car_price_prediction.csv")
data1=data["Price"]
N=len(data1)

lags = range(35)


#Pre-allocate autocorrelation table
autocorr_values = []

#Mean
mean_data = np.mean(data1)

#Variance
variance_data = np.var(data1)

#Normalized data
normalized_data = (data1 - mean_data) / np.sqrt(variance_data)

#Go through lag components one-by-one
for lag in lags:
 if lag == 0:
  autocorr_values.append(1)
 else:
  auto_cov = np.sum((data1[:-lag] - mean_data) * (data1[lag:] - mean_data)) / N 
  autocorr_values.append(auto_cov / variance_data)
  
#display the graph
plt.figure(figsize=(10, 6))
plt.stem(lags, autocorr_values)
plt.title('Autocorrelation of Data')
plt.xlabel('Lag')
plt.ylabel('Autocorrelation')
plt.grid(True)
plt.show()
```
### OUTPUT:
<img width="1226" height="720" alt="image" src="https://github.com/user-attachments/assets/6eee9f2d-4340-40f4-b4eb-dcb183aae92f" />


### RESULT:
Thus we have successfully implemented the auto correlation function in python.
