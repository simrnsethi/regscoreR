# regscoreR

[![Build Status](https://travis-ci.org/UBC-MDS/regscoreR.svg?branch=master)](https://travis-ci.org/UBC-MDS/regscoreR) [![codecov](https://codecov.io/gh/simrnsethi/regscoreR/branch/master/graphs/badge.svg)](https://codecov.io/gh/simrnsethi/regscoreR) [![Coverage Status](https://coveralls.io/repos/github/simrnsethi/regscoreR/badge.svg)](https://coveralls.io/github/simrnsethi/regscoreR)


An R package that does model comparison between different regression models.


## Installation

You can install regscoreR from github with:


``` r
# install.packages("devtools")
devtools::install_github("UBC-MDS/regscoreR")
```



## **Function Description**


### AIC

AIC stands for Akaike’s Information Criterion. It estimates the quality of a model, relative to each of other models. The lower AIC score is, the better the model is. Therefore, a model with lowest AIC - in comparison to others, is chosen.

```
AIC = n*log(residual sum of squares/n) + 2K
```

where:

- n: number of observations
- K: number of parameters (including intercept)

#### Function

```
aic(y, y_pred, p)
```

**Parameters:**

* **y**: array-like of shape = (n_samples) or (n_samples, n_outputs)
  * True target variable(s)

* **y_pred**: array-like of shape = (n_samples) or (n_samples, n_outputs)
  * Fitted target variable(s) obtained from your regression model

* **p**: int
  * Number of predictive variable(s) used in the model

**Return:**
* aic_score: int
  * AIC score of the model


### BIC

BIC stands for Bayesian Information Criterion. Like AIC, it also estimates the quality of a model. When fitting models, it is possible to increase model fitness by adding more parameters. Doing this may results in model overfit. Both AIC and BIC helps to resolve this problem by using a penalty term for the number of parameters in the model. This term is bigger in BIC than in AIC.

```
BIC = n*log(residual sum of squares/n) + K*log(n)
```

where:

- n: number of observations
- K: number of parameters (including intercept)

#### Function

```
bic(y, y_pred, p)
```
**Parameters:**
* **y**: array-like of shape = (n_samples) or (n_samples, n_outputs)
  * True target variable(s)

* **y_pred**: array-like of shape = (n_samples) or (n_samples, n_outputs)
  * Fitted target variable(s) obtained from your regression model

* **p**: int
  * Number of predictive variable(s) used in the model

**Return:**
* bic_score: int
  * BIC score of the model

  
  


### Mallow's C_p

Mallow's C_p is named for Colin Lingwood Mallows. It is used to assess the fit of regression model, finding the best model involving a subset of predictive variables available for predicting some outcome.

```
C_p = (SSE_p/MSE) - (n - 2p)
```

where:

- SSE_k: residual sum of squares for the subset model containing `p` explanatory
variables counting the intercept.
- MSE: mean squared error for the full model (model containing all `k` explanatory variables of interest)
- n: number of observations
- p: number of subset explanatory variables

#### Function

```
mallow(y, y_pred, y_sub, k, p)
```

**Parameters:**


* **y**: array-like of shape = (n_samples) or (n_samples, n_outputs)
  * True target variable(s)

* **y_pred**: array-like of shape = (n_samples) or (n_samples, n_outputs)
  * Fitted target variable(s) obtained from your regression model

* **y_sub**: array-like of shape = (n_samples) or (n_samples, n_outputs)
  * Fitted target variable(s) obtained from your subset regression model

* **k**: int
  * Number of predictive variable(s) used in the model

* **p**: int
  * Number of predictive variable(s) used in the subset model

**Return:**

* mallow_score: int
  * Mallow's C_p score of the subset model



## Usage

```
> library(regscoreR)
> y <-  c(1,2,3,4)
> y_pred <- c(5,6,7,8)
> p <- 3
>
> aic(y, y_pred, p)
[1] 17.09035
>
>
> bic(y, y_pred, p)
[1] 15.24924
>
>
> y_sub <- c(1,2,3,5)
> k <- 3L
> p <-2L
> mallow(y, y_pred, y_sub, k, p) 
[1] 0.015625
```


## License
[MIT](LICENSE)

## Contributing
This is an open source project. Please follow the guidelines below for contribution.
  - Open an issue for any feedback and suggestions.
  - For contributing to the project, please refer to [Contributing](CONTRIBUTING.md) for details.
