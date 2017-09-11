# Motivation: There are too many time series formats

Think about the following situation: 
You have some new time series data and want to develop a classification algorithm on it. 
Because it is a new dataset, you are not sure if you should use a shape based approach or maybe a feature based one. 
In any case, you want to apply different packages on that data and compare the results.

Now, there is no widely aggreed standard for time series data.
For most of the tools, 

* you will have to read the instructions
* understand the format of the respective package, 
* and finally you will have write a script to convert your data.

This is annyoing and slows you down.

With supervised machine learning, using different packages is more convinient. 
Almost all packages expect a feature matrix as input.
In a feature matrix, a column denotes a feature, a row is a sample. 
Objectwise, either `numpy.ndarrays` or their extensions `pandas.DataFrame` are used.

You can use your feature matrix and first apply models from sklearn on it. 
Then you can take the same object and try lightgbm or xgboost models on it, see 

``` Python

X = [[0, 0, 1, 1], 
     [0, 1, 0, 0], 
     [1, 0, 0, 1]]
     
y = [1, 
     1, 
     1]

# first train a model from sklearn
from sklearn.ensemble import RandomForestClassifer()
clf1 = RandomForestClassifer()
clf1.fit(X, y)

# now train a model from another package on the data, there is no transformation necessary
from lightgbm import LGBMClassifier
clf2 = LGBMClassifier()
clf2.fit(X, y)

```

All without every having the need to convert your data, everything works out of the box.

We want the same for time series data.
The purpose of this document is to find a standard for time series data, their analysis should become more user friendly.

# Classification of different time series formats

A time series consists of timely annotated data. 
So, a recording is based on two numbers, the `time` and `value` dimension. 
It has the format 
```
(time, value)
```
An example would be 
```
(2009-06-15T13:45:30, 83°C)
```
which denotes a temperature of `83°C` measured at time `2009-06-15T13:45:30`.

A whole time series, which is a collection of such two dimensional recordings can have meta information, characteristics that will not change over time.
The most important meta information are the entity id and the type of time series for multivariate szenarios.

In that case, a recording is a 4 dimensional vector 
```
(id, time, value, kind)
```
where `value` is the value of the time series of type `kind` recorded at time `time` for the entity `id`.

So, for example 
```
(VW Beetle - SN: 7 4545 4543 ,  2009-06-15T13:45:30, 83°C, Engine Temperature G1)
```
denotes a temperature of `83°C` measured at sensor `Engine Temperature G1` for the VW Beetle with serial number `7 4545 4543` at `2009-06-15T13:45:30`.

There is a myriad of different formats which could be used to save such information.
In the following, I present some formats.
If you have some more ideas, please feel free to submit a pr.
    
### 1.i Stacked Matrix

```
time  id  value kind
0   1       1    a
1   1       2    a
0   1       3    a
3   1       4    a
```

### 1.ii Flat Matrix

```
time  id  value kind
0   1       1    a
1   1       2    a
0   1       3    a
3   1       4    a
```

### 1.iii 3-dimensional Matrix

```
time  id  value kind
0   1       1    a
1   1       2    a
0   1       3    a
3   1       4    a
```


### 2.i Dictionary based

```
time  id  value kind
0   1       1    a
1   1       2    a
0   1       3    a
3   1       4    a
```


## How to pick the right format

Before one can pick the right format, one needs to check a few points

1. Do the time series can have different lengths?
2. Are the time series non uniformly sampled, are the time series allowed to have missing values?
3. Do we inspect multivariate time series?


| Format | 1. Different length  | 2. Non uniformly sampled | 3. Multivariate time series |
| -------| :---: | :---: | :---: |
| Stacked Matrix | _X_ | _X_ | _X_ |

