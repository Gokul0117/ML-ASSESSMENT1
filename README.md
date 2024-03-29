# <center>  ASSIGNMENT - LINEAR REGRESSION 
</center>
### Developed by: GOKUL J<br>
### Reg no: 212222230038

## Q1. Create a scatter plot between cylinder vs Co2Emission (green color):
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error, r2_score
df = pd.read_csv("FuelConsumption.csv")
df = pd.read_csv("FuelConsumption.csv")
plt.scatter(df['CYLINDERS'], df['CO2EMISSIONS'], color='green')
plt.xlabel('CYLINDERS')
plt.ylabel('CO2EMISSIONS')
plt.title('CYLINDER vs CO2EMISSION')
plt.show()
```
 ## Output:
 ![311208507-d7f29014-a036-4744-bd8b-8569eaf3ba56](https://github.com/Gokul0117/ML-ASSESMENT1/assets/121165938/cec974a8-07eb-4469-a9aa-217e9f5407d7)

 ## Q2Using scatter plot compare data cylinder vs Co2Emission and Enginesize Vs Co2Emission using different colors:
 ```
 # Scatter plot for cylinder vs Co2Emission (green color)
plt.scatter(df['CYLINDERS'], df['CO2EMISSIONS'], color='green', label='CYLINDERS vs CO2EMISSIONS')

# Scatter plot for Enginesize vs Co2Emission (blue color)
plt.scatter(df['ENGINESIZE'], df['CO2EMISSIONS'], color='blue', label='ENGINESIZE vs CO2EMISSIONS')

plt.xlabel('FEATURE')
plt.ylabel('CO2EMISSIONS')
plt.title('Comparison between Cylinder and Enginesize vs Co2Emission')
plt.legend()
plt.show()
```
## Output:
![311209059-f5c324db-3210-4fd2-82e5-e3b6b99f8cdb](https://github.com/Gokul0117/ML-ASSESMENT1/assets/121165938/65fbcbbc-d387-4c0f-bd71-06fb1a8fefbe)

## Q3Using scatter plot compare data cylinder vs Co2Emission and Enginesize Vs Co2Emission and FuelConsumption_comb Co2Emission using different colors:
```
# Scatter plot for cylinder vs Co2Emission (green color)
plt.scatter(df['CYLINDERS'], df['CO2EMISSIONS'], color='green', label='Cylinder vs Co2Emission')
plt.scatter(df['ENGINESIZE'], df['CO2EMISSIONS'], color='blue', label='Enginesize vs Co2Emission')

# Scatter plot for FuelConsumption_comb vs Co2Emission (red color)
plt.scatter(df['FUELCONSUMPTION_COMB'], df['CO2EMISSIONS'], color='red', label='FuelConsumption_comb vs Co2Emission')
plt.xlabel('Feature')
plt.ylabel('Co2Emission')
plt.title('Comparison between Cylinder, Enginesize, and FuelConsumption_comb vs Co2Emission')
plt.legend()
plt.show()
```
## Output:
![311209554-91e3d89d-8499-47d0-b110-d34c5415a97b](https://github.com/Gokul0117/ML-ASSESMENT1/assets/121165938/18146d19-85db-4855-badf-c84c28fa8bd3)

## Q4 Train your model with independent variable as cylinder and dependent variable as Co2Emission:
```
X = df[['CYLINDERS']]
y = df['CO2EMISSIONS']

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

model_fuel = LinearRegression()
model_fuel.fit(X_train, y_train)

plt.scatter(X_test, y_test, color='blue', label='Actual Data')
plt.plot(X_test, model_fuel.predict(X_test), color='red', label='Regression Line')
plt.xlabel('Cylinder')
plt.ylabel('CO2EMISSION')
plt.title('CYLINDER vs CO2 EMISSION')
plt.legend()
plt.show()
```
## Output:
![313450796-774c8166-ea2d-4704-b012-b548385145b3](https://github.com/Gokul0117/ML-ASSESMENT1/assets/121165938/fd8e8a1e-5d52-4bd9-a900-80dd50648a67)

## Q5 Train another model with independent variable as FuelConsumption_comb and dependent variable as Co2Emission:
```
data = pd.read_csv("/content/FuelConsumption.csv")
X = data['FUELCONSUMPTION_COMB'].values.reshape(-1, 1)
y = data['CO2EMISSIONS'].values

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

model_fuel = LinearRegression()
model_fuel.fit(X_train, y_train)

plt.scatter(X_test, y_test, color='blue', label='Actual Data')
plt.plot(X_test, model_fuel.predict(X_test), color='red', label='Regression Line')
plt.xlabel('FUELCONSUMPTION_COMB')
plt.ylabel('CO2EMISSIONS')
plt.title('Fuel Consumption vs Co2 Emission')
plt.legend()
plt.show()
```
## Output:
![313450848-b1d295f4-8ce9-4bee-ac7c-e1d920bcff2c](https://github.com/Gokul0117/ML-ASSESMENT1/assets/121165938/744fbcb2-c226-4e9f-8af3-1a3bcf3012b5)

## Q6 Train models with different train-test ratios and note down accuracies:
```
# Train models with different train-test ratios and note down accuracies
X_2 = df.iloc[:, 10:11].values
Y_1 = df['CO2EMISSIONS'].values
X_train_1, X_test_1, Y_train_1, Y_test_1 = train_test_split(X_2, Y_1, test_size=1/3, random_state=0)
regressor = LinearRegression()
regressor.fit(X_train_1, Y_train_1)
Y_train_pred = regressor.predict(X_train_1)
plt.scatter(X_train_1, Y_train_1, color='blue', label='Actual Data')
plt.plot(X_train_1, Y_train_pred, color='red', label='Regression Line')
plt.title("Fuel Consumption Combined vs CO2 Emission (Training set)")
plt.xlabel("Fuel Consumption Combined")
plt.ylabel("CO2 Emission")
plt.legend()
plt.show()




X_2 = df.iloc[:, 10:11].values
Y_1 = df['CO2EMISSIONS'].values
X_train_1, X_test_1, Y_train_1, Y_test_1 = train_test_split(X_2, Y_1, test_size=1/3, random_state=0)
regressor = LinearRegression()
regressor.fit(X_train_1, Y_train_1)
Y_pred = regressor.predict(X_test_1)
plt.scatter(X_test_1, Y_test_1, color='blue')
plt.plot(X_test_1, regressor.predict(X_test_1), color='red')
plt.title("Fuel Consumption Combined vs CO2 Emission (Training set)")
plt.xlabel("Fuel Consumption Combined")
plt.ylabel("CO2 Emission")
plt.show()



X_2 = df.iloc[:, 10:11].values
Y_1 = df['CO2EMISSIONS'].values
X_train_1, X_test_1, Y_train_1, Y_test_1 = train_test_split(X_2, Y_1, test_size=0.2, random_state=0)
regressor = LinearRegression()
regressor.fit(X_train_1, Y_train_1)
Y_train_pred = regressor.predict(X_train_1)
plt.scatter(X_train_1, Y_train_1, color='red', label='Actual Data')
plt.plot(X_train_1, Y_train_pred, color='blue', label='Regression Line')
plt.title("Fuel Consumption Combined vs CO2 Emission (Training set)")
plt.xlabel("Fuel Consumption Combined")
plt.ylabel("CO2 Emission")
plt.legend()
plt.show()




X_2 = df.iloc[:, 10:11].values
Y_1 = df['CO2EMISSIONS'].values
X_train_1, X_test_1, Y_train_1, Y_test_1 = train_test_split(X_2, Y_1, test_size=0.2, random_state=0)
regressor = LinearRegression()
regressor.fit(X_train_1, Y_train_1)
Y_pred = regressor.predict(X_test_1)
plt.scatter(X_test_1, Y_test_1, color='red')
plt.plot(X_test_1, regressor.predict(X_test_1), color='blue')
plt.title("Fuel Consumption Combined vs CO2 Emission (Test set)")
plt.xlabel("Fuel Consumption Combined")
plt.ylabel("CO2 Emission")
plt.show()
```
## Ouptut:
![313450916-2f38cec5-a8ab-40d6-b935-d1aff8e1285d](https://github.com/Gokul0117/ML-ASSESMENT1/assets/121165938/c106b66d-9ffe-4d7c-97f8-ab99a66e258a)

![313450933-54f692e6-329e-4366-8645-83768d3c04bd](https://github.com/Gokul0117/ML-ASSESMENT1/assets/121165938/9716fe9f-baaf-4611-88a2-0cda1c84b467)

![313450944-5663fb2e-10ee-4599-b550-c4b70be17584](https://github.com/Gokul0117/ML-ASSESMENT1/assets/121165938/e9633440-2d05-4dd9-9940-d04d1af63fba)

![313450953-8add74a4-bae0-4e53-b8b8-cb91e1e63022](https://github.com/Gokul0117/ML-ASSESMENT1/assets/121165938/777f8708-1fec-4177-895f-9c19f95057f7)





