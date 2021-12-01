Logistic Model
================

``` r
banking_train<- read_delim("/cloud/project/data/Banking Dataset.csv",
            delim = ";", escape_double = FALSE, trim_ws = TRUE)
```

    ## Rows: 45211 Columns: 17

    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ";"
    ## chr (10): job, marital, education, default, housing, loan, contact, month, p...
    ## dbl  (7): age, balance, day, duration, campaign, pdays, previous

    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
banking_train <- banking_train %>%
  mutate(y = factor(if_else(y == "yes", 1, 0)))
```

``` r
set.seed(45211)
######
banking_split <- initial_split(banking_train, prop = 0.8)
reduced_train_df <-training(banking_split)
banking_test <-testing(banking_split)
nrow(banking_train)
```

    ## [1] 45211

``` r
nrow(banking_test)
```

    ## [1] 9043

``` r
banking_rec<- recipe(
  y ~ .,
  data = reduced_train_df
)

banking_rec <- banking_rec %>%
  step_rm(day, pdays) %>%
  step_cut(campaign, previous, breaks = c(0, 1)) %>%
  step_cut(age, breaks = c(25,40,65)) %>%
  step_cut(balance, breaks = c(-0.1, 0.1, 1000, 10000)) %>%
  step_cut(duration, breaks = c(60, 120, 180, 240, 300, 360, 420, 480, 540, 600)) %>%
  step_dummy(all_nominal(),-all_outcomes()) %>%
  step_zv(all_predictors())
```

``` r
banking_mod <- logistic_reg() %>%
  set_engine("glm")
```

``` r
banking_wflow <-workflow() %>%
  add_model(banking_mod) %>%
  add_recipe(banking_rec)
```

``` r
 banking_fit <- banking_wflow %>%
  fit(data = reduced_train_df)
tidy(banking_fit) 
```

    ## # A tibble: 55 × 5
    ##    term              estimate std.error statistic  p.value
    ##    <chr>                <dbl>     <dbl>     <dbl>    <dbl>
    ##  1 (Intercept)        -4.72      0.409    -11.5   1.10e-30
    ##  2 age_X.25.40.       -0.621     0.105     -5.91  3.51e- 9
    ##  3 age_X.40.65.       -0.641     0.113     -5.67  1.40e- 8
    ##  4 age_X.65.95.       -0.218     0.179     -1.22  2.22e- 1
    ##  5 job_blue.collar    -0.319     0.0811    -3.94  8.24e- 5
    ##  6 job_entrepreneur   -0.266     0.138     -1.93  5.35e- 2
    ##  7 job_housemaid      -0.505     0.152     -3.32  8.93e- 4
    ##  8 job_management     -0.147     0.0834    -1.77  7.73e- 2
    ##  9 job_retired         0.0381    0.114      0.334 7.39e- 1
    ## 10 job_self.employed  -0.309     0.123     -2.50  1.24e- 2
    ## # … with 45 more rows

``` r
banking_pred <- predict(banking_fit, banking_test, type = "prob") %>%
  bind_cols(banking_test %>% select(y))
```

    ## Warning: There are new levels in a factor: NA

    ## Warning: There are new levels in a factor: NA

    ## Warning: There are new levels in a factor: NA

``` r
banking_pred %>%
  roc_curve(
    truth = y,
    .pred_1,
    event_level = "second") %>%
  autoplot()
```

![](Logistic_Model_files/figure-gfm/prediction-1.png)<!-- -->

``` r
banking_pred %>%
  roc_auc(
    truth = y,
    .pred_1,
    event_level = "second") 
```

    ## # A tibble: 1 × 3
    ##   .metric .estimator .estimate
    ##   <chr>   <chr>          <dbl>
    ## 1 roc_auc binary         0.911
