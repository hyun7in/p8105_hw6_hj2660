# p8105_hw6_hj2660
Problem 2
For this problem, we’ll use the Central Park weather data similar to data we’ve seen elsewhere. The code chunk below (adapted from the course website) will download these data.

weather_df = 
  rnoaa::meteo_pull_monitors(
    c("USW00094728"),
    var = c("PRCP", "TMIN", "TMAX"), 
    date_min = "2022-01-01",
    date_max = "2022-12-31") |>
  mutate(
    name = recode(id, USW00094728 = "CentralPark_NY"),
    tmin = tmin / 10,
    tmax = tmax / 10) |>
  select(name, id, everything())
The boostrap is helpful when you’d like to perform inference for a parameter / value / summary that doesn’t have an easy-to-write-down distribution in the usual repeated sampling framework. We’ll focus on a simple linear regression with tmax as the response with tmin and prcp as the predictors, and are interested in the distribution of two quantities estimated from these data:

r̂ 2
log(β̂ 1∗β̂ 2)
Use 5000 bootstrap samples and, for each bootstrap sample, produce estimates of these two quantities. Plot the distribution of your estimates, and describe these in words. Using the 5000 bootstrap estimates, identify the 2.5% and 97.5% quantiles to provide a 95% confidence interval for r̂ 2
 and log(β̂ 0∗β̂ 1)
. Note: broom::glance() is helpful for extracting r̂ 2
 from a fitted regression, and broom::tidy() (with some additional wrangling) should help in computing log(β̂ 1∗β̂ 2)
.

Problem 3
In this problem, you will analyze data gathered to understand the effects of several variables on a child’s birthweight. This dataset, available here, consists of roughly 4000 children and includes the following variables:

babysex: baby’s sex (male = 1, female = 2)
bhead: baby’s head circumference at birth (centimeters)
blength: baby’s length at birth (centimeteres)
bwt: baby’s birth weight (grams)
delwt: mother’s weight at delivery (pounds)
fincome: family monthly income (in hundreds, rounded)
frace: father’s race (1 = White, 2 = Black, 3 = Asian, 4 = Puerto Rican, 8 = Other, 9 = Unknown)
gaweeks: gestational age in weeks
malform: presence of malformations that could affect weight (0 = absent, 1 = present)
menarche: mother’s age at menarche (years)
mheigth: mother’s height (inches)
momage: mother’s age at delivery (years)
mrace: mother’s race (1 = White, 2 = Black, 3 = Asian, 4 = Puerto Rican, 8 = Other)
parity: number of live births prior to this pregnancy
pnumlbw: previous number of low birth weight babies
pnumgsa: number of prior small for gestational age babies
ppbmi: mother’s pre-pregnancy BMI
ppwt: mother’s pre-pregnancy weight (pounds)
smoken: average number of cigarettes smoked per day during pregnancy
wtgain: mother’s weight gain during pregnancy (pounds)
Load and clean the data for regression analysis (i.e. convert numeric to factor where appropriate, check for missing data, etc.).

Propose a regression model for birthweight. This model may be based on a hypothesized structure for the factors that underly birthweight, on a data-driven model-building process, or a combination of the two. Describe your modeling process and show a plot of model residuals against fitted values – use add_predictions and add_residuals in making this plot.

Compare your model to two others:

One using length at birth and gestational age as predictors (main effects only)
One using head circumference, length, sex, and all interactions (including the three-way interaction) between these
Make this comparison in terms of the cross-validated prediction error; use crossv_mc and functions in purrr as appropriate.

Note that although we expect your model to be reasonable, model building itself is not a main idea of the course and we don’t necessarily expect your model to be “optimal”.

