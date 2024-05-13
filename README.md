# Showcasing the power of XGBoost in credit default prediction

## Project overview & Introduction:

In a [**previous project**](https://github.com/evgeni-g-georgiev/Bayesian-Credit-Card-Default-Model) we had employed a Bayesian Logistic Regression to predict whether credit card users are going to default or not. 

In **this project**, I build a simple XGBoost model to tackle the same problem (on the same dataset) to showcase the potential for superiority of decision tree based models in credit default prediction.

In its most simple form, a credit default model can be thought of as a dual optimisation problem:
1. **risk-mitigation:** you want to be sure that a small number of "accepted" credit card clients end up defaulting.
2. **profit-maximisation:** you want as many clients as possible to collect payments from.

**What we will show in this project is that even very simple decision tree models can out-perform fairly complex linear Bayesian models. In particular, our XGBoost model will do a much better job at the "profit-maximisation" aspect of our problem, while maintaining performance in "risk-mitigation".**

<u>We build an incredibly simple (yet powerful) XGBoost model that:</u>

1. has the same (90%) precision on y=0 (non-default) predictions as our [**Bayesian Model**](https://github.com/evgeni-g-georgiev/Bayesian-Credit-Card-Default-Model)
2. does a far greater better job at **profit-maximisation**. This model accepts 53% of candidates in our test set (vs just 4.5% previously!)

## Table of Contents
- [**0. Project Overview & Introduction**](#0.-Project-Overview-&-Introduction)
    - [0.1 A discussion of credit default model objectives](#0.1-A-discussion-of-credit-default-model-objectives)
    - [0.2 Brief introction to this project](#0.2-Brief-introction-to-this-project)
    - [0.3 Importing all relevant modules](#0.3-Importing-all-relevant-modules)
    - [0.4 Setting up the data](#0.4-Setting-up-the-data)
- [**1. Building and training our XGBoost default prediction model**](#1.-Building-and-training-our-XGBoost-default-prediction-model)
    - [1.1 Training the model](#1.1-Training-the-model)
    - [1.2 Intepretting the preliminary results](#1.2-Intepretting-the-preliminary-results)
    - [1.3 Adjusting the threshold to tilt our model defensively](#1.3-Adjusting-the-threshold-to-tilt-our-model-defensively)
    - [1.4 A brief conclusion...](#1.4-A-brief-conclusion...)
-  [**2. Acknowledgements**](#2.-Acknowledgements) 

## Acknowledgements

Dataset taken from Kaggle: https://www.kaggle.com/datasets/uciml/default-of-credit-card-clients-dataset

**As per Kaggle acknowledgements, they reference the following:**

- Lichman, M. (2013). UCI Machine Learning Repository [http://archive.ics.uci.edu/ml]. Irvine, CA: University of California, School of Information and Computer Science.

- The original dataset can be found here at the UCI Machine Learning Repository: https://archive.ics.uci.edu/dataset/350/default+of+credit+card+clients
