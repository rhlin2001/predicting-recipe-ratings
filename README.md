# Predicting Recipe Ratings





## Introduction



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



## Baseline Model



## Final Model



## Fairness Analysis
