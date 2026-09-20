# Build and compare multiple regression models to predict house prices

**What you're learning step by step:**

1. **Data exploration** - understand your dataset before building anything
2. **Train-test split** - learn how to properly split data so you can evaluate fairly
3. **Scaling** - prepare data so models learn better
4. **Multiple models** - try different algorithms (Linear, Ridge, SGD) to see which works best
5. **Baseline comparison** - beat the dummy model that just guesses average prices
6. **Overfitting detection** - compare training versus test performance to spot if your model memorized or actually learned

## Imports

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
sns.set_theme()

from sklearn.datasets import fetch_californai_housing
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler, MinMaxScaler
```

## Loading our data
```python
housing = fetch_california_housing(as_frame=True)

print(housing.DESCR)

# see wat data type it is
type(housing)   ## ans ==> sklearn.utils._bunch.Bunch

#Know the Keys of Housing data
housing.keys()  ##==> dict_keys(['data', 'target', 'frame', 'target_names', 'feature_names', 'DESCR'])

#check the dict_key and then assign x and y
X = housing.data
y = hosuing.target
```

## Explore the data
```python
X.shape
y.shape
X.head()
y.head()
X.info() # this is a simple function that will get us some basic info about our dataframe.
X.isnull().sum() # Checks for missing data

X.describe() # Shows mean, std, min, max for each feature
```

## Ploting
```python
# PLot Histgrams
X.hist(figsize=(12, 10), bins=30)
plt.subplots_adjust(hspace=0.4, wspace=0.4)   # For properly adjusting space for each plot

#Plot single graph for features.
sns.histplot(data=X, x='AveBedrms', bins=30)

# we should also plot the histogram of the traget variable
sns.displot(y)

# Ploting Longitude and Latitude
sns.scatterplot(data=X, x='Longitude', y='Latitude', size=y, hue=y, palette='viridis', alpha=0.5)
plt.legend(title="MedHouseVal", bbox_to_anchor=(1.05, 0.95), loc="upper left") 
plt.title("Median house value depending of their spatial location")

#Ploting PairPlot
columns_drop = ["Longitude", "Latitude"]
subset = X.drop(columns=columns_drop)

subset["MedHouseVal"]= y  #create a new feature MedHouseVal and add target values as value for it.

subset["MedHouseVal"] = pd.qcut(subset["MedHouseVal"], 6, retbins=False)
subset["MedHouseVal"] = subset["MedHouseVal"].apply(lambda x: x.mid)

```

## Train Test Split
```python
#Make sure u imported train_test_split

X_train, X_test, y_train, y_test = train_test_split(X,y, test_size=0.2, random_state=42)

#Check shade of train set and test set
print(X_train.shape)
print(y_train.shape)
```

## Scaling
```python
scaler = StandardScaler() # or MinMaxScaler()
scaler.fit(X_train) # Learn from training data only
X_trained = scaler.transform(X_train)
X_test_scaled = scaler.transform(X_test)
```

## Train our Model
- Ok it's time to train our model.  We will want to choose one of the three options we imported earlier.

	* LinearRegression
	* SGDRegressor
	* Ridge

We are also going to train a [dummy regressor](https://scikit-learn.org/stable/modules/generated/sklearn.dummy.DummyRegressor.html).  This regressor will use a default strategy like 'mean' or 'median'. That means it will always guess the average value in the dataset, which is pretty dumb, but we need to prove to ourselves that our model learned something -- so this is a good way to do it.

```python
#IMPORTS

from sklearn.linear_model import LinearRegression, Ridge, SGDRegressor
from sklearn.dummy import DummyRegressor

model = LinearRegression()
dummy = DummyRegressor(strategy="mean")

model.fit(X_trained, y_train)
dummy.fit(X_trained, y_train)
```

## Make Predict
```python
y_pred_train = model.predict(X_train_scalled)
y_pred_test = model.predict(X_test_scalled)

y_dummy_train = dummy.predict(X_train_scaled)
y_dummy_test  = dummy.predict(X_test_scaled)
```

## Evaluate Performance
```python
##IMPORT
from sklrean.metrics import mean_squared_error, r2_score
```

```python
mse_train = mean_squared_error(y_train, y_pre_train)
mse_test = mean_squared_error(y_test, y_pred_test)

r2_train = r2_score(y_train, y_pred_train)
r2_test = r2_score(y_test, y_pred_test)

print(f"Train MSE: {mse_train:.4f}, Test MSE: {mse_test:.4f}") 
print(f"Train R2: {r2_train:.4f}, Test R2: {r2_test:.4f}")
```