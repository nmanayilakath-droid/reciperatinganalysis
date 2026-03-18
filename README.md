# Recipe Rating Analysis  

Data science analysis project for DSC 80 at UCSD analyzing recipe ratings.

### By Nidhi Manayilakath

This project explores whether the nutritional content of recipes, particularly calorie levels, affects their average ratings. Using a dataset of recipes with nutritional information, I analyze patterns in ratings and build predictive models to better understand what drives recipe popularity.

---

## Introduction

The goal of this analysis is to determine whether higher-calorie recipes receive different ratings compared to lower-calorie recipes. Understanding this relationship can provide insight into whether health-related factors influence user preferences.

---

## Data Cleaning and Exploratory Data Analysis

The dataset contains recipes along with nutritional information such as calories, fat, sugar, sodium, and protein, as well as user ratings.

Below is the distribution of average ratings:

<iframe src="assets/ratings_hist.html" width="800" height="600" frameborder="0"></iframe>

Most recipes are rated between 3.5 and 5, indicating generally positive reviews.

The relationship between calories and average rating is shown below:

<iframe src="assets/calories_scatter.html" width="800" height="600" frameborder="0"></iframe>

There is no strong visible relationship between calorie content and ratings.

---

## Assessment of Missingness

Missingness was analyzed to determine whether it depended on other variables. A permutation test showed that missingness in the dataset does not depend on calories, suggesting that it is likely Missing Completely At Random (MCAR).

---

## Hypothesis Testing

To test whether calorie level affects ratings, a hypothesis test was conducted comparing high-calorie and low-calorie recipes.

Permutation test distribution for rating difference:

<iframe src="assets/permdisterbutionofrating.html" width="800" height="600" frameborder="0"></iframe>

The p-value (~0.0695) is slightly above 0.05, so we fail to reject the null hypothesis. This indicates that there is not sufficient evidence to conclude that calorie level significantly impacts average recipe ratings.

---

## Framing a Prediction Problem

The prediction task is to predict average recipe ratings using nutritional features. This is a regression problem since the target variable is continuous.

---

## Baseline Model

A linear regression model was used as a baseline. The model achieved an RMSE of approximately 0.636, meaning predictions are typically about 0.64 rating points away from the true rating.

---

## Final Model

A Random Forest model was used as an improved model with additional features such as fat, sugar, sodium, and protein.

The final model achieved an RMSE of approximately 0.635, representing only a very small improvement over the baseline. This suggests that nutritional features alone are not strong predictors of average recipe ratings.

Feature importance analysis shows that no single feature dominates, reinforcing that nutritional information has limited predictive power.

A key limitation of this model is that it does not incorporate textual or contextual features such as ingredients or user reviews, which may better explain variation in ratings.

---

## Fairness Analysis

Model performance was compared across high-calorie and low-calorie recipes.

The model performs slightly worse on high-calorie recipes (RMSE ≈ 0.640) compared to low-calorie recipes (RMSE ≈ 0.630). However, the difference is small (≈ 0.01), suggesting that there is no substantial disparity in model performance across these groups.

Thus, there is no strong evidence of meaningful unfairness, though minor variation in predictive accuracy exists.
