# Using python to work with time series data

The python ecosystem contains different packages that can be used to process time series.

The following list is by no means exhaustive, feel free to edit the list (will propose a file change via PR) if you miss anything.

# Machine learning, statistics, analytics

## Libraries

| Project Name | Description |
| ------- | ------ |
| [Arrow](https://github.com/crsmithdev/arrow) | A sensible, human-friendly approach to creating, manipulating, formatting and converting dates, times, and timestamps |
| [cesium](https://github.com/cesium-ml/cesium) | Time series platform with feature extraction aiming for non uniformly sampled signals |
| [GENDIS](https://github.com/IBCNServices/GENDIS) | Shapelet discovery by genetic algorithms | 
| [glm-sklearn](https://github.com/jcrudy/glm-sklearn) | scikit-learn compatible wrapper around the GLM module in [statsmodels](https://github.com/statsmodels/statsmodels) |
| [Featuretools](https://github.com/Featuretools/featuretools) | Time series feature extraction, with possible conditionality on other variables with a pandas compatible relational-database-like data container |
| [fecon235](https://github.com/rsvp/fecon235) |  Computational tools for financial economics |
| [ffn](https://github.com/pmorissette/ffn) | financial function library |
| [flint](https://github.com/twosigma/flint) | A Time Series Library for Apache Spark |
| [hctsa](https://github.com/benfulcher/hctsa) | Matlab based feature extraction which can be controlled from python |
| [HMMLearn](https://github.com/hmmlearn/hmmlearn) | Hidden Markov Models with scikit-learn compatible API |
| [khiva-python](https://github.com/shapelets/khiva-python) | A Time Series library with accelerated analytics on GPUS, it provides feature extraction and motif discovery among other functionalities.|
| [Nitime](https://github.com/nipy/nitime) |  Timeseries analysis for neuroscience data |
| [Pastas](https://github.com/pastas/pastas) | Timeseries analysis for hydrological data |
| [prophet](https://github.com/facebook/prophet) |  Time series forecasting for time series data that has multiple seasonality with linear or non-linear growth |
| [pyDSE](https://github.com/blue-yonder/pydse) |  ARMA models for Dynamic System Estimation |
| [PyFlux](https://github.com/RJT1990/pyflux) | Classical time series forecasting models |
| [pysf](https://github.com/alan-turing-institute/pysf) | A scikit-learn compatible machine learning library for supervised/panel forecasting |
| [pyramid](https://github.com/tgsmith61591/pyramid) | port of R's auto.arima method to Python |
| [pyts](https://github.com/johannfaouzi/pyts) | Contains time series preprocessing, transformation as well as classification techniques |
| [seglearn](https://github.com/dmbee/seglearn) | Extends the scikit-learn pipeline concept to sequence data |
| [sktime](https://github.com/alan-turing-institute/sktime) | A scikit-learn compatible library for learning with time series/panel data including time series classification/regression and (supervised/panel) forecasting |
| [statsmodels](https://github.com/statsmodels/statsmodels) | Contains a submodule for classical time series models and hypothesis tests |
| [stumpy](https://github.com/TDAmeritrade/stumpy) | Calculates matrix profile for time series subsequence all-pairs-similarity-search |
| [TensorFlow-Time-Series-Examples](https://github.com/hzy46/TensorFlow-Time-Series-Examples) | Time Series Prediction with tf.contrib.timeseries |
| [tensorflow_probability.sts](https://github.com/tensorflow/probability/tree/master/tensorflow_probability/python/sts) | Bayesian Structural Time Series model in Tensorflow Probability |
| [Traces](https://github.com/datascopeanalytics/traces) | A library for unevenly-spaced time series analysis |
| [ta-lib](https://github.com/mrjbq7/ta-lib) | Calculate technical indicators for financial time series (python wrapper around TA-Lib) |
| [ta](https://github.com/bukosabino/ta) | Calculate technical indicators for financial time series |
| [tsfresh](https://github.com/blue-yonder/tsfresh) | Extracts and filters features from time series, allowing supervised classificators and regressor to be applied to time series data |
| [tslearn](https://github.com/rtavenar/tslearn) | Direct time series classifiers and regressors |
| [tspreprocess](https://github.com/MaxBenChrist/tspreprocess) | Preprocess time series (resampling, denoising etc.), still WIP |

## Examples or singular models

| Project Name | Description |
| ------- | ------ |
| [ES-RNN forecasting algorithm](https://github.com/damitkwr/ESRNN-GPU) | Python implementation of the winning forecasting method of the M4 competition combining exponential smoothing with a recurrent neural network using PyTorch |
| [Deep learning methods for time series classification](https://github.com/hfawaz/dl-4-tsc) | A collection of common deep learning architectures for time series classification |
| [LSTM-Neural-Network-for-Time-Series-Prediction](https://github.com/jaungiers/LSTM-Neural-Network-for-Time-Series-Prediction) |  LSTM based forecasting model |  
| [LSTM_tsc](https://github.com/RobRomijnders/LSTM_tsc) | An LSTM based time-series classification neural network|
| [shapelets-python](https://github.com/mohaseeb/shaplets-python) |  Shapelet Classifier based on a multi layer neural network |
| [M4 competition](https://github.com/M4Competition) | Collection of statistical and machine learning forecasting methods |
| [UCR_Time_Series_Classification_Deep_Learning_Baseline](https://github.com/cauchyturing/UCR_Time_Series_Classification_Deep_Learning_Baseline) |  Fully Convolutional Neural Networks for state-of-the-art time series classification |
| [WTTE-RNN](https://github.com/ragulpr/wtte-rnn/) | Time to Event forecast by RNN based Weibull density estimation |


# Time series data container

| Project name | Description |
| ------- | ------ |
| [Featuretools](https://github.com/Featuretools/featuretools) | Time series feature extraction, with possible conditionality on other variables with a pandas compatible relational-database-like data container |
| [pysf](https://github.com/alan-turing-institute/pysf) | A scikit-learn compatible library for supervised forecasting |
| [xarray](https://github.com/pydata/xarray) | Labelled, multi-dimensional data structures as long as they have a shared time index |
| [xpandas](https://github.com/alan-turing-institute/xpandas) | Labelled 1D and 2D data container for storing type-heterogeneous tabular data of any type, including time series, and encapsulates feature extraction and transformation modelling in an sklearn-compatible transformer interface, work in progress. |

# Data sets
| Project Name | Description |
| ------- | ------ |
| [awesome-public-datasets](https://github.com/awesomedata/awesome-public-datasets#time-series) | This huge list of public datasets also has a section on time series datasets|
| [ecmwf_models](https://github.com/TUW-GEO/ecmwf_models) | Readers and converters for climate reanalysis data |
| [M4 competition](https://github.com/M4Competition) | Forecasting competition on 100,000 time series |
| [pandas-datareader](https://github.com/pydata/pandas-datareader) | Pulls financial data from different sources (e.g. yahoo, google, Quandl) |
| [Timeseriesclassification.com](https://timeseriesclassification.com) | An extensive repository for time series classification datasets |


# Databases, frameworks
| Project Name | Description |
| ------- | ------ |
| [artic](https://github.com/manahl/arctic) | High performance datastore for time series and tick data |
| [automl_service](https://github.com/crawles/automl_service) | Fully automated time series classification pipeline, deployed as a web service |
| [cesium](https://github.com/cesium-ml/cesium) | Time series platform with feature extraction aming for non uniformly sampled signals |
| [thunder](https://github.com/thunder-project/thunder) | scalable analysis of image and time series data in python based on spark |
| [whisper](https://github.com/graphite-project/whisper) | File-based time-series database format |

# Free courses

| Project Name | Description |
| ------- | ------ |
| [Time Series Sorecasting](https://www.udacity.com/course/time-series-forecasting--ud980) | Udacity free course to learn about how to build and apply time series analysis/forecasting in business contexts |

----

# Discussion

We would like to trigger a homogenization of the formats which are used in the python time series community, please see the [concept page](https://github.com/MaxBenChrist/awesome_time_series_in_python/blob/master/standardize_time_series_formats.md)
