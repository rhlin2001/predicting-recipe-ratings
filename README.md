# Predicting Recipe Ratings

Authors: Richard Lin, Francisco Downey





## Introduction

Cooking recipes are traditions that are as old as civilization itself, passed on from generation to generation. In modern times, there is a large and growing community of home cooks including people who like to share recipes and people who try to follow and rate them. There are many factors that go into rating recipes such as personal enjoyment, ingredients, nutrition, and easy preparation. Our goal for this project is to try to determine what types of recipes have high ratings, and to ultimately build a model that can predict ratings for recipes. If we are able to accomplish this goal, then people may use our model to understand what kind of recipes deserve specific ratings.

For our project, we will be using datasets from [Food.com](https://www.food.com/recipe) which include `recipes` (83,782 observations and 10 variables) and `interactions` (731,927 observations and 5 variables).

### Recipes:

| Column         | Description                                                    |
| -------------- | -------------------------------------------------------------- |
| 'name'         | Recipe name                                                    |
| 'id'           | Recipe ID                                                      |
| 'minutes'      | Minutes to prepare recipe                                       |
| 'contributor_id' | User ID who submitted this recipe                              |
| 'submitted'    | Date recipe was submitted                                       |
| 'tags'         | Food.com tags for recipe                                        |
| 'nutrition'    | Nutrition information in the form [calories (#), total fat (PDV), sugar (PDV), sodium (PDV), protein (PDV), saturated fat (PDV), carbohydrates (PDV)]; PDV stands for “percentage of daily value” |
| 'n_steps'      | Number of steps in recipe                                       |
| 'steps'        | Text for recipe steps, in order                                  |
| 'description'  | User-provided description                                        |

### Interactions:

| Column      | Description         |
|-------------|---------------------|
| 'user_id'   | User ID             |
| 'recipe_id' | Recipe ID           |
| 'date'      | Date of interaction |
| 'rating'    | Rating given        |
| 'review'    | Review text         |



## Data Cleaning & EDA

### Data Cleaning

| name                                 |     id |   minutes |   contributor_id | submitted           | tags                                                  | nutrition                                 |   n_steps | steps                                                 | description                                           | ingredients                                           |   n_ingredients |          user_id |   recipe_id | date                |   rating | review                                                |   avg_rating |   calories |   total_fat |   sugar |   sodium |   protein |   saturated_fat |   carbohydrates |
|:-------------------------------------|-------:|----------:|-----------------:|:--------------------|:------------------------------------------------------|:------------------------------------------|----------:|:------------------------------------------------------|:------------------------------------------------------|:------------------------------------------------------|----------------:|-----------------:|------------:|:--------------------|---------:|:------------------------------------------------------|-------------:|-----------:|------------:|--------:|---------:|----------:|----------------:|----------------:|
| 1 brownies in the world    best ever | 333281 |        40 |           985201 | 2008-10-27 00:00:00 | ['60-minutes-or-less', 'time-to-make', 'course', '... | [138.4, 10.0, 50.0, 3.0, 3.0, 19.0, 6.0]  |        10 | ['heat the oven to 350f and arrange the rack in th... | these are the most; chocolatey, moist, rich, dense... | ['bittersweet chocolate', 'unsalted butter', 'eggs... |               9 | 386585           |      333281 | 2008-11-19 00:00:00 |        4 | These were pretty good, but took forever to bake. ... |            4 |      138.4 |          10 |      50 |        3 |         3 |              19 |               6 |
| 412 broccoli casserole               | 306168 |        40 |            50969 | 2008-05-30 00:00:00 | ['60-minutes-or-less', 'time-to-make', 'course', '... | [194.8, 20.0, 6.0, 32.0, 22.0, 36.0, 3.0] |         6 | ['preheat oven to 350 degrees', 'spray a 2 quart b... | since there are already 411 recipes for broccoli c... | ['frozen broccoli cuts', 'cream of chicken soup', ... |               9 |  29782           |      306168 | 2008-12-31 00:00:00 |        5 | This was one of the best broccoli casseroles that ... |            5 |      194.8 |          20 |       6 |       32 |        22 |              36 |               3 |
| 412 broccoli casserole               | 306168 |        40 |            50969 | 2008-05-30 00:00:00 | ['60-minutes-or-less', 'time-to-make', 'course', '... | [194.8, 20.0, 6.0, 32.0, 22.0, 36.0, 3.0] |         6 | ['preheat oven to 350 degrees', 'spray a 2 quart b... | since there are already 411 recipes for broccoli c... | ['frozen broccoli cuts', 'cream of chicken soup', ... |               9 |      1.19628e+06 |      306168 | 2009-04-13 00:00:00 |        5 | I made this for my son's first birthday party this... |            5 |      194.8 |          20 |       6 |       32 |        22 |              36 |               3 |
| 412 broccoli casserole               | 306168 |        40 |            50969 | 2008-05-30 00:00:00 | ['60-minutes-or-less', 'time-to-make', 'course', '... | [194.8, 20.0, 6.0, 32.0, 22.0, 36.0, 3.0] |         6 | ['preheat oven to 350 degrees', 'spray a 2 quart b... | since there are already 411 recipes for broccoli c... | ['frozen broccoli cuts', 'cream of chicken soup', ... |               9 | 768828           |      306168 | 2013-08-02 00:00:00 |        5 | Loved this.  Be sure to completely thaw the brocco... |            5 |      194.8 |          20 |       6 |       32 |        22 |              36 |               3 |
| 412 broccoli casserole               | 306168 |        40 |            50969 | 2008-05-30 00:00:00 | ['60-minutes-or-less', 'time-to-make', 'course', '... | [194.8, 20.0, 6.0, 32.0, 22.0, 36.0, 3.0] |         6 | ['preheat oven to 350 degrees', 'spray a 2 quart b... | since there are already 411 recipes for broccoli c... | ['frozen broccoli cuts', 'cream of chicken soup', ... |               9 | 520830           |      306168 | 2017-10-17 00:00:00 |        5 | 5 stars from my husband and son, my toughest criti... |            5 |      194.8 |          20 |       6 |       32 |        22 |              36 |               3 |

### Univariate Analysis

<iframe
  src="assets/rating_hist.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

<iframe
  src="assets/hist_grid.html"
  width="950"
  height="800"
  frameborder="0"
></iframe>

### Bivariate Analysis

<iframe
  src="assets/rating_vs_ingredients.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

<iframe
  src="assets/rating_vs_calories.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

### Interesting Aggregates

|   rating |   minutes |   n_steps |   n_ingredients |   calories |   total_fat |   sugar |   sodium |   protein |   saturated_fat |   carbohydrates |
|---------:|----------:|----------:|----------------:|-----------:|------------:|--------:|---------:|----------:|----------------:|----------------:|
|        1 |   36.2803 |   9.33219 |         8.42849 |    253.136 |     18.1094 | 33.1732 |  15.1561 |   20.2205 |         23.4006 |         8.29516 |
|        2 |   37.2563 |   9.44106 |         8.73841 |    278.025 |     19.4848 | 32.5073 |  16.6205 |   24.043  |         24.5079 |         9.07483 |
|        3 |   36.085  |   9.01971 |         8.75529 |    275.179 |     19.6132 | 29.1049 |  17.0275 |   25.147  |         23.7723 |         8.46438 |
|        4 |   34.8529 |   8.83843 |         8.73365 |    279.741 |     19.8944 | 27.969  |  17.4507 |   26.1159 |         23.7849 |         8.52295 |
|        5 |   34.2342 |   8.90763 |         8.59581 |    270.349 |     20.1664 | 28.9405 |  16.916  |   23.7741 |         24.4596 |         7.97638 |



## Assessment of Missingness

### NMAR Analysis

### Missingness Dependency

<iframe
  src="assets/emp_dist_1.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

<iframe
  src="assets/emp_dist_2.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>



## Hypothesis Testing



## Framing a Prediction Problem

Recalling the main question guiding this project, the importance of a rating matters to those interested in cooking and/or eating these meals. Furthermore, it would be extremely beneficial to have the ability to know the rating even when just given a few details about the recipe. Our project aims to classify `rating`, the response variable, of a given recipe using a multiclass classification approach. The model’s features that will be used to predict the rating are available before the reviewer inputs their rating. To evaluate the model, a classification report is derived where accuracy is a key metric being used to evaluate the model’s performance. Not only is it intuitive, but it provides a measure of how correct the model is. However, due to the imbalanced distribution of classes, the F1-score is leveraged to achieve a balanced evaluation between precision and recall. For instance, when viewing the distribution of ratings, it is apparent that the majority of ratings is five. It is important that we can accurately predict other ratings. It would be terrible to prepare a recipe with a rating of one because it was believed to have a rating of five. If the project were to only use accuracy, it could be high solely due to predicting only ratings of five. By not only focusing on accuracy, we are able to measure how well the model does in the other classes as well.



## Baseline Model

Wanting an easily interpretable model for classification, we chose to use ordinal logistic regression. As an extension of the linear regression model, it is best suited for this project because of its use of a linear combination of features to output probabilities for classification. Wanting to predict the rating of a recipe, our first intuition was to use the nutritional composition of the recipe, mainly total fat, sugar, and carbohydrates. These features were all quantitative, represented as percentages of daily value for a recipe. The features were transformed by a `QuantileTransformer` object within a `ColumnTransformer`. By doing so, the distributions of these features were normalized, we reduced outliers, and we transformed the data to be more linearly separable. The `ColumnTransformer` was then passed into a `Pipeline` which added a `LogisticRegression` model. With just these transformed features implemented in the logistic regression model, a 77.29% training accuracy and a 77.02% testing accuracy was achieved. Although our baseline model achieved a reasonably high accuracy, the F1 score was zero for all ratings except for the rating of five which had an F1 score of 0.87. With only these three features, we considered our current model as insufficient since it seemed trivial to make every prediction as a rating of five while still achieving relatively high accuracy. The baseline model needs additional feature engineering to improve its predictive power for the other ratings.



## Final Model

Although the baseline model performed poorly given only three features, we think incorporating these features into our final model is beneficial for the predictive power. In addition, one feature that we believe to be crucial is the `review` column. The `review` column is text that the reviewer submitted which consists of their thoughts on the recipe and whether they liked it or not. In other words, it contains valuable sentimental information that we can use to differentiate between positive and negative reviews in order to predict ratings. To incorporate this essential feature, we use a term frequency-inverse document frequency (TF-IDF) approach. TF-IDF allows for the retrieval of the importance of a term or word in its respective document, or review in this case. The most important words such as “love”, “yummy”, and “best” can reflect positive sentiment, and likely higher ratings whereas words such as “hate”, “gross”, and “worst” can reflect negative sentiment, and likely lower ratings. To use the TF-IDF approach, we add a `TfidfVectorizer` object in the ColumnTransformer to process the `review` column. In addition to this, we also standardize `n_steps` and `minutes` using `StandardScaler` in the ColumnTransformer to try to improve the predictive capability even further. We choose these two features because we believe that these quantify the ease to follow the recipe. We reason that how easy it is to prepare a dish can severely affect the rating. For example, if two dishes have the same macronutrients, but one takes 30 minutes while the other takes two days, the ratings for the two could be very different. Furthermore, we use `GridSearchCV` with 3-fold cross validation to find the optimal hyperparameter of `max_iter` (maximum number of iterations) for model convergence which we find to be 1000. This time, we achieve an 83.83% training accuracy and an 81.15% testing accuracy. Not only did the accuracy increase, but so did the F1 scores of all ratings. The F1 scores for the ratings from 1-5 are 0.55, 0.12, 0.35, 0.40, 0.90 respectively. Although far from ideal, these scores show drastic improvement from the baseline model.



## Fairness Analysis

To ensure the final model is fair for different groups of observations, we conduct permutation testing and define our two groups by the date of the review (one for reviews before 01-01-2013 and other for reviews after 01-01-2013).

**Null:** Our model is fair. Its accuracy for reviews before 2013 and after 2013 are roughly the same, and any differences are due to random chance.
**Alternative:** Our model is unfair. Its accuracy for reviews before 2013 is lower than that of after 2013.
**Test Statistic:** Difference in Group Accuracy
**Significance Level:** 0.05

With a p-value of 0.104 and a significance level of 5%, we fail to reject the null in favor of the alternative. Thus, this suggests that our model is fair.
