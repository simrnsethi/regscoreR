# regscoreR

An R package that does model comparison between different regression models.

A project by:
- Ha Dinh
- Simran Sethi
- Ruoqi Xu

## **Overview**

### Problem

Currently, in R ecosystems, there is no single package that provides easy calculation for AIC, BIC, Mallow's C_p, and a united table summary of scores for all models that users can refer to to compare and choose the best model. This leads to manual mathematical calculation, lengthy codes or usage of several packages to obtain one task, which is inefficient.

### Solution

Acknowledging this problem, we want to build a united package which provides users instant computation for various model comparison metrics such as:

- Mean Square error
- Root mean square error
- Mean absolute error
- Mean Percentage error
- Mean absolute percentage error
- AIC
- BIC
- Mallow's C_p

In addition to all model comparison score functions, we want to have a function to output a summary table that combines scores for all models users want to compare. This table helps users avoid scrolling through lines of output or call score outputs with additional code to get all scores. This table of comparison is not recommended to be used if users want to compare models with different methods (e.g. linear regression, logistic regression)

### How solution fits to R ecosystem

[`broom`](https://www.rdocumentation.org/packages/broom/versions/0.4.2/topics/finish_glance) package has a function `finish_glance` that outputs some of regression metrics in a table:
* Log likelihoods
* AIC
* BIC
* Deviance
* Residual degrees of freedom

Although this function provides a table with some of the key metrics that we want to include in our package (AIC, BIC), it lacks of other metrics such as MSE and Mallow's C_p. Additionally, `finish_glance`'s output table only include metrics for 1 model which might not be as easy to compare metrics of all models as out intended output table of comparison. That being said, our package can solve this problem, and be a united source for all popular regression model comparison metrics. 

## **Timeline**

**Phase I**: 02/05/2018 - 03/11/2018, develop functions to compute AIC, BIC, Mallow's $C_p$ and table output that include all scores for model comparison.
- ** **Phase II**: From late March, develop other functions to finish the package.

* ** Tentative, and will be updated later

## **Function Description**

Here, we will describe functions in *Phase I*.

### AIC

#### Introduction

AIC stands for Akaike's Information Criterion. It estimates the quality of a model, relative to each of other models. The lower AIC score is, the better the model is. Therefore, a model with lowest AIC - in comparison to others, is chosen.

```
AIC = n*log(residual sum of squares/n) + 2K
```

where:
- n: number of observations
- K: number of parameters (including intercept)

#### Function

```
aic(x, y, n, k, model)
```

### BIC

#### Introduction

BIC stands for Bayesian Information Criterion. Like AIC, it also estimates the quality of a model. When fitting models, it is possible to increase model fitness by adding more parameters. Doing this may results in model overfit. Both AIC and BIC helps to resolve this problem by using a penalty term for the number of parameters in the model. This term is bigger in BIC than in AIC.

```
BIC = n*log(residual sum of squares/n) + K*log(n)
```

where:
- n: number of observations
- K: number of parameters (including intercept)

#### Function

```
```

### Mallow's $C_p$

#### Introduction


#### Function


### Table of comparison

#### Function

```
comparison_model(model1, model2,...)
```

**Input**


**Output**

A table with model names and their scores. Demo:

| Model  | AIC | BIC | Mallow's C_p |
|--------|-----|-----|--------------|
| Model1 | 123 | 145 | 156          |
| Model2 | 145 | 134 | 167          |

Mallow's C_p
