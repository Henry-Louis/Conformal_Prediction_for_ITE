# Split Conformal Prediction Project

## Introduction

This project aims to implement Split Conformal Prediction (CP) in Python. The primary goal is to create predictive models that are accompanied by reliable confidence intervals. The project includes the implementation of neural networks for outcome prediction and quantile regression for uncertainty quantification.

## Theory of Conformal Prediction

Conformal Prediction (CP) is a framework for constructing prediction intervals that offer a valid measure of confidence. It provides a way to use past experience to specify how likely new predictions are to be correct.

### Properties

1. **Validity**: Under the assumption that the data are exchangeable (i.e., each data point is equally likely to appear), CP gives valid confidence intervals. In other words, the error rate is controlled.

2. **Efficiency**: CP aims to produce intervals that are as tight as possible while still maintaining the specified confidence level.

3. **Distribution-Free**: CP does not make any assumptions about the distribution of the data, which makes it widely applicable.

4. **Online Learning**: CP can work in an online setting where data points arrive one at a time.

5. **Transparency**: The CP framework is transparent and allows for easy inspection of its predictions and intervals.

## Project Structure

The core of the project is the `SplitConformalPrediction` class, which has the following methods:

- `split_data()`: Splits the data into training and calibration sets.
- `train_nn_Y0_Y1()`: Trains neural network models for predicting outcomes under control and treatment.
- `train_nn_ITE()`: Trains a neural network model for predicting Individual Treatment Effects (ITE).
- `train_quantile_models()`: Trains quantile regression models for the upper and lower bounds of the prediction intervals.
- `calculate_calibrated_interval()`: Computes calibrated confidence intervals based on the trained models and calibration data.

## Usage

```python
# Initialize the class with the data and parameters
scp = SplitConformalPrediction(data, W="treatment", Y="wage_2010", X=["feature1", "feature2"])

# Calculate the calibrated confidence interval
calibrated_lower_bound, calibrated_upper_bound, calibrated_coverage_rate = scp.calculate_calibrated_interval()
```

## Reference
- Jing Lei, Max G’Sell, Alessandro Rinaldo, Ryan J. Tibshirani, Larry Wasserman. "Distribution-Free Predictive Inference for Regression." Journal of the American Statistical Association, Volume 113, Issue 523, 2018, Pages 1094-1111. [DOI](https://doi.org/10.1080/01621459.2017.1307116)
