# Motivation: There are too many time series formats

Think about the following situation: 
You have some new time series data and want to develop a classification algorithm on it. 
Because it is a new dataset, you are not sure if you should use a shape based approach or maybe a feature based one. 
In any case, you want to apply different packages on that data and compare results.

Now, what happens is that there is no aggreed standard for time series data.
For most of the tools, 

* you will have to read the instructions
* understand the format of the respective package, 
* and finally you will have write a script to convert your data.

This is annyoing and slows you down in your work as a Data Scientist! 

With supervised machine learning, it is more easy. 
Almost all packages expect a feature matrix as input.
In a feature matrix, a column denotes a feature, a row is a sample. 
Objectwise, either `numpy.ndarrays` or their extensions `pandas.DataFrame` are used.

So you can use your feature matrix and first apply models from sklearn on it. 
Then you can take the same object and try lightgbm or xgboost models on it, see 

``` Python

X = [[0, 0, 1], 
     [0, 1, 0], 
     [1, 0, 0]]
y = [1, 1, 1]


from sklearn.ensemble import RandomForestClassifer()
clf1 = RandomForestClassifer()
clf1.fit(X, y)

from lightgbm import LGBMClassifier
clf2 = LGBMClassifier()
clf2.fit(X, y)

```

All without every having the need to convert your data, everything works out of the box.

We want the same for time series data.
So the purpose of this document is to find a standard for time series data so time series analysis becomes more easy.

# How to pick the right format

Before one can pick the right format, one needs to

1. Do the time series can have different lengths?
2. Are the time series uniformly sampled?
3. Are the time series allowed to have missing values, NaNs etc.?
4. Are multivariate time series allowed?

# Possible formats

There is a myriad of different formats which could be used. 

1. Relational
    1. Stacked matrix
    2. Flat matrix
    3. 3-dimensional matrix
2. Nested
    1. Dictionary based

