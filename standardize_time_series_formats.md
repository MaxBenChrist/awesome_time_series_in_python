This page is not yet finished.

TODO: remove question about multivariate time series

# Motivation: There are too many time series formats

Image the following situation:
You inspect a delivery of new time series data and want to develop a classification algorithm for it.
Because it is a new dataset for you, you are not sure if you should use a shape based approach or maybe a feature based one.
In any case, you want to apply different packages on that data and compare the results.

Now, there is no widely agreed standard for time series data.
For most of the tools,

* you will have to read the instructions
* understand the format of the respective package,
* and finally you will have write a script to convert your data.

This is annoying and slows you down.

For the construction of supervised machine learning models, using different packages is way more convenient.
Almost all packages expect a feature matrix as input.
In a feature matrix, a column denotes a feature, a row is a sample.
Object wise, either `numpy.ndarrays` or their extensions `pandas.DataFrame` are used.

You can use your feature matrix and first apply models from sklearn on it.
Then you can take the same object and try lightgbm or xgboost models on it:

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
The purpose of this document is to find a common standard.
The analysis of time series data and the interplay between packages should become more user friendly.

# Classification of different time series formats

A time series consists of timely annotated data, a recording is based on two characteristics, the `time` and `value` dimensions.
Therefore, a singular recording is a two dimensional vector
```
(time, value)
```
An example would be
```
(2009-06-15T13:45:30, 83°C)
```
which denotes a temperature of `83°C` measured at time `2009-06-15T13:45:30`.

A whole time series, which is a collection of such two dimensional recordings can have meta information, characteristics that will not change over time.
The most important meta information is the identifier of the respective entity and in case of multivariate scenarios the type of time series.
Multivariate means that a singular entity has multiple assigned time series.

In that case, a recording is a 4 dimensional vector
```
(id, time, value, kind)
```
where `value` is the value of the time series of type `kind` recorded at time `time` for the entity `id`.

For example
```
(VW Beetle - SN: 7 4545 4543,  2009-06-15T13:45:30, 83°C, Engine Temperature G1)
```
denotes a temperature of `83°C` measured at sensor `Engine Temperature G1` for the VW Beetle with serial number `7 4545 4543` at time `2009-06-15T13:45:30`.

There is a myriad of different formats which could be used to save such information.
We will discuss the following formats.

1. Relational
    1. Stacked matrix
    2. Flat matrix
    3. 3-dimensional matrix
2. Nested
    1. Dictionary based
3. Binary
    1. ?

(If you have some more ideas, please feel free to submit a pr).
Later we will analyze the saving capabilities of the different formats.

    
### 1.i Stacked Matrix

This is the most flexible format. It supports non uniformly sampled time series of different lengths. In this format, each row will contain the four dimensional tuple.

Example: The two time series
```
values [11, 2] for times [0, 1] of kind a for id 1
values [13, 4] for times [0, 3] of kind b for id 1
```
will be saved as
```
time  id  value kind
0     1    11    a
1     1     2    a
0     1    13    b
3     1     4    b
```

### 1.ii Flat Matrix

Is suitable for the multivariate, uniformly sampled case when we want to save  different kinds of time series that all need to have the same length and need to be recorded at the same times.

In this format, we will dedicate a full columns for each type of time series.

Example: The two time series
```
values [11, 2] for times [0, 1] of kind a for id 1
values [13, 4] for times [0, 1] of kind b for id 1
```
will be saved as
```
time  id  a   b
0     1  11  13
1     1   2   4
```

### 1.iii 3-dimensional Matrix

For this format, the time series need to be uniformly sampled and of same length.
Then we use the first two dimensions of the matrix to denote kind and id and the third one for the time scale.

Example: The two time series
```
values [11, 2] for times [0, 1] of kind a for id 1
values [13, 4] for times [0, 1] of kind b for id 1
```
will be recorded as
```
    time         a        b
1   [0, 1]  [11, 2]  [13, 4]
```


### 2.i Dictionary based

We can have  dictionary mapping from the id to another dictionary that maps kind to the time series.
Essentially you are using a singular array for each time series.

Example: The two time series
```
values [11, 2] for times [0, 1] of kind a for id 1
values [13, 4] for times [0, 3] of kind b for id 1
```
will be recorded as
```
{ 1:
  { a: [time: [0, 1], value:[11, 2]],
    b: [time: [0, 3], value:[13, 4]]
  }
}
```

## How to pick the right format

Before one can pick the right format, one needs to check a few points

1. Do the time series can have different lengths?
2. Are the time series non uniformly sampled, are the time series allowed to have missing values?
3. Do we inspect multivariate time series?

Depending of the answers to this questions, different formats are suitable.
The following table lists the characteristics of the different formats

| Format | 1. Different length  | 2. Non uniformly sampled | 3. Multivariate time series | Does not contain redundant information | Tabular format |
| -------| :---: | :---: | :---: | :---: | :---: |
| 1.i Stacked Matrix |  _X_  |  _X_ | _X_ | | _X_|
| 1.ii Flat Matrix | |  |  _X_  | _X_ | _X_ |
| 1.iii 3-dimensional Matrix |  |  |  _X_ | _X_ | |
| 2.ii Dictionary based | _X_ |  _X_ |  _X_  | _X_ | | |
