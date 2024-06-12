# Predicting Recipe Ratings





## Introduction



## Data Cleaning & EDA

### Data Cleaning

| name                                 |     id |   minutes |   contributor_id | submitted           | tags                                                                                                    | nutrition                                 |   n_steps | steps                                                                                                   | description                                                                                             | ingredients                                                                                             |   n_ingredients |          user_id |   recipe_id | date                |   rating | review                                                                                                  |   avg_rating |   calories |   total_fat |   sugar |   sodium |   protein |   saturated_fat |   carbohydrates |
|:-------------------------------------|-------:|----------:|-----------------:|:--------------------|:--------------------------------------------------------------------------------------------------------|:------------------------------------------|----------:|:--------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------|----------------:|-----------------:|------------:|:--------------------|---------:|:--------------------------------------------------------------------------------------------------------|-------------:|-----------:|------------:|--------:|---------:|----------:|----------------:|----------------:|
| 1 brownies in the world    best ever | 333281 |        40 |           985201 | 2008-10-27 00:00:00 | ['60-minutes-or-less', 'time-to-make', 'course', 'main-ingredient', 'preparation', 'for-large-groups... | [138.4, 10.0, 50.0, 3.0, 3.0, 19.0, 6.0]  |        10 | ['heat the oven to 350f and arrange the rack in the middle', 'line an 8-by-8-inch glass baking dish ... | these are the most; chocolatey, moist, rich, dense, fudgy, delicious brownies that you'll ever make.... | ['bittersweet chocolate', 'unsalted butter', 'eggs', 'granulated sugar', 'unsweetened cocoa powder',... |               9 | 386585           |      333281 | 2008-11-19 00:00:00 |        4 | These were pretty good, but took forever to bake.  I would send it ended up being almost an hour!  E... |            4 |      138.4 |          10 |      50 |        3 |         3 |              19 |               6 |
| 412 broccoli casserole               | 306168 |        40 |            50969 | 2008-05-30 00:00:00 | ['60-minutes-or-less', 'time-to-make', 'course', 'main-ingredient', 'preparation', 'side-dishes', 'v... | [194.8, 20.0, 6.0, 32.0, 22.0, 36.0, 3.0] |         6 | ['preheat oven to 350 degrees', 'spray a 2 quart baking dish with cooking spray , set aside', 'in a ... | since there are already 411 recipes for broccoli casserole posted to "zaar" ,i decided to call this ... | ['frozen broccoli cuts', 'cream of chicken soup', 'sharp cheddar cheese', 'garlic powder', 'ground b... |               9 |  29782           |      306168 | 2008-12-31 00:00:00 |        5 | This was one of the best broccoli casseroles that I have ever made.  I made my own chicken soup for ... |            5 |      194.8 |          20 |       6 |       32 |        22 |              36 |               3 |
| 412 broccoli casserole               | 306168 |        40 |            50969 | 2008-05-30 00:00:00 | ['60-minutes-or-less', 'time-to-make', 'course', 'main-ingredient', 'preparation', 'side-dishes', 'v... | [194.8, 20.0, 6.0, 32.0, 22.0, 36.0, 3.0] |         6 | ['preheat oven to 350 degrees', 'spray a 2 quart baking dish with cooking spray , set aside', 'in a ... | since there are already 411 recipes for broccoli casserole posted to "zaar" ,i decided to call this ... | ['frozen broccoli cuts', 'cream of chicken soup', 'sharp cheddar cheese', 'garlic powder', 'ground b... |               9 |      1.19628e+06 |      306168 | 2009-04-13 00:00:00 |        5 | I made this for my son's first birthday party this weekend. Our guests INHALED it! Everyone kept say... |            5 |      194.8 |          20 |       6 |       32 |        22 |              36 |               3 |
| 412 broccoli casserole               | 306168 |        40 |            50969 | 2008-05-30 00:00:00 | ['60-minutes-or-less', 'time-to-make', 'course', 'main-ingredient', 'preparation', 'side-dishes', 'v... | [194.8, 20.0, 6.0, 32.0, 22.0, 36.0, 3.0] |         6 | ['preheat oven to 350 degrees', 'spray a 2 quart baking dish with cooking spray , set aside', 'in a ... | since there are already 411 recipes for broccoli casserole posted to "zaar" ,i decided to call this ... | ['frozen broccoli cuts', 'cream of chicken soup', 'sharp cheddar cheese', 'garlic powder', 'ground b... |               9 | 768828           |      306168 | 2013-08-02 00:00:00 |        5 | Loved this.  Be sure to completely thaw the broccoli.  I didn&#039;t and it didn&#039;t get done in ... |            5 |      194.8 |          20 |       6 |       32 |        22 |              36 |               3 |
| 412 broccoli casserole               | 306168 |        40 |            50969 | 2008-05-30 00:00:00 | ['60-minutes-or-less', 'time-to-make', 'course', 'main-ingredient', 'preparation', 'side-dishes', 'v... | [194.8, 20.0, 6.0, 32.0, 22.0, 36.0, 3.0] |         6 | ['preheat oven to 350 degrees', 'spray a 2 quart baking dish with cooking spray , set aside', 'in a ... | since there are already 411 recipes for broccoli casserole posted to "zaar" ,i decided to call this ... | ['frozen broccoli cuts', 'cream of chicken soup', 'sharp cheddar cheese', 'garlic powder', 'ground b... |               9 | 520830           |      306168 | 2017-10-17 00:00:00 |        5 | 5 stars from my husband and son, my toughest critics. I used a 10-oz bag of chopped broccoli and a 1... |            5 |      194.8 |          20 |       6 |       32 |        22 |              36 |               3 |

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



## Assessment of Missingness



## Hypothesis Testing



## Framing a Prediction Problem



## Baseline Model



## Final Model



## Fairness Analysis
