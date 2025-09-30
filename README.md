# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 30.09.2025

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
from statsmodels.tsa.seasonal import seasonal_decompose

# Load dataset (reset index so Month is a normal column)
data = pd.read_csv("air traffic.csv")

# Clean Pax column
data["Pax"] = data["Pax"].str.replace(",", "").astype(int) / 1_000_000  # in millions

# Build proper datetime column
data["Date"] = pd.to_datetime(data["Year"].astype(str) + "-" + data["Month"].astype(str))

# Set Date as index
data.set_index("Date", inplace=True)

# Perform seasonal decomposition (monthly data, yearly seasonality)
decomposition = seasonal_decompose(data["Pax"], model="additive", period=12)

# Plot all components
decomposition.plot()
plt.show()


```
### OUTPUT:

### FIRST FIVE ROWS:
<br>
<br>
<img width="474" height="264" alt="image" src="https://github.com/user-attachments/assets/daffeeb9-d377-4ebd-ab52-88c3cf4599dd" />
<br>
<br>


### PLOTTING THE DATA:
<br>
<br>

<img width="585" height="366" alt="image" src="https://github.com/user-attachments/assets/59564574-fdbd-40d8-99bb-484d9e114883" />

<br>
<br>

### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
