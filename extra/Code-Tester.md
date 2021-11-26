Code Tester
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
set.seed(1115)
######
banking_split <- initial_split(banking_train, prop = 0.8)
reduced_train_df <-training(banking_split)
banking_test <-testing(banking_split)
glimpse(reduced_train_df)
```

    ## Rows: 36,168
    ## Columns: 17
    ## $ age       <dbl> 38, 33, 52, 29, 38, 40, 31, 53, 42, 33, 27, 37, 47, 32, 39, …
    ## $ job       <chr> "management", "blue-collar", "services", "admin.", "student"…
    ## $ marital   <chr> "married", "married", "divorced", "single", "single", "divor…
    ## $ education <chr> "tertiary", "secondary", "secondary", "secondary", "tertiary…
    ## $ default   <chr> "no", "no", "no", "no", "no", "no", "no", "no", "no", "no", …
    ## $ balance   <dbl> -469, 3605, 238, 265, 1523, -1, 533, 1093, 105, 146, 116, 63…
    ## $ housing   <chr> "yes", "yes", "yes", "yes", "yes", "no", "no", "yes", "no", …
    ## $ loan      <chr> "no", "no", "no", "no", "no", "no", "no", "yes", "no", "no",…
    ## $ contact   <chr> "unknown", "cellular", "cellular", "cellular", "unknown", "u…
    ## $ day       <dbl> 16, 20, 6, 25, 5, 9, 12, 16, 27, 22, 30, 5, 11, 13, 4, 18, 1…
    ## $ month     <chr> "jun", "nov", "may", "nov", "jun", "jun", "may", "jun", "aug…
    ## $ duration  <dbl> 209, 308, 101, 414, 17, 24, 372, 244, 85, 380, 46, 338, 853,…
    ## $ campaign  <dbl> 12, 1, 1, 1, 16, 1, 1, 3, 4, 1, 1, 2, 2, 2, 2, 3, 1, 5, 3, 1…
    ## $ pdays     <dbl> -1, -1, 362, 184, -1, -1, 90, -1, -1, 91, -1, -1, -1, -1, -1…
    ## $ previous  <dbl> 0, 0, 5, 1, 0, 0, 10, 0, 0, 3, 0, 0, 0, 0, 0, 0, 0, 17, 0, 0…
    ## $ poutcome  <chr> "unknown", "unknown", "other", "failure", "unknown", "unknow…
    ## $ y         <fct> 0, 0, 0, 1, 0, 0, 1, 0, 0, 1, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, …

``` r
glimpse(banking_test)
```

    ## Rows: 9,043
    ## Columns: 17
    ## $ age       <dbl> 35, 57, 36, 57, 54, 36, 58, 42, 32, 57, 33, 51, 60, 59, 53, …
    ## $ job       <chr> "management", "blue-collar", "technician", "technician", "re…
    ## $ marital   <chr> "married", "married", "single", "divorced", "married", "sing…
    ## $ education <chr> "tertiary", "primary", "secondary", "secondary", "secondary"…
    ## $ default   <chr> "no", "no", "no", "no", "no", "no", "no", "no", "no", "no", …
    ## $ balance   <dbl> 231, 52, 265, 63, 529, -171, -364, -76, 0, 249, 790, 6530, 1…
    ## $ housing   <chr> "yes", "yes", "yes", "yes", "yes", "yes", "yes", "yes", "yes…
    ## $ loan      <chr> "no", "no", "yes", "no", "no", "no", "no", "no", "no", "no",…
    ## $ contact   <chr> "unknown", "unknown", "unknown", "unknown", "unknown", "unkn…
    ## $ day       <dbl> 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, …
    ## $ month     <chr> "may", "may", "may", "may", "may", "may", "may", "may", "may…
    ## $ duration  <dbl> 139, 38, 348, 242, 1492, 242, 355, 787, 138, 164, 391, 91, 5…
    ## $ campaign  <dbl> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, …
    ## $ pdays     <dbl> -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, …
    ## $ previous  <dbl> 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, …
    ## $ poutcome  <chr> "unknown", "unknown", "unknown", "unknown", "unknown", "unkn…
    ## $ y         <fct> 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, …

``` r
trial_fit <- logistic_reg() %>%
  set_engine("glm") %>%
  fit(y ~ ., data = reduced_train_df, family = "binomial")
trial_fit
```

    ## parsnip model object
    ## 
    ## Fit time:  1.2s 
    ## 
    ## Call:  stats::glm(formula = y ~ ., family = stats::binomial, data = data)
    ## 
    ## Coefficients:
    ##        (Intercept)                 age      jobblue-collar     jobentrepreneur  
    ##         -2.653e+00           2.030e-04          -2.533e-01          -4.094e-01  
    ##       jobhousemaid       jobmanagement          jobretired    jobself-employed  
    ##         -4.240e-01          -1.218e-01           3.873e-01          -2.270e-01  
    ##        jobservices          jobstudent       jobtechnician       jobunemployed  
    ##         -1.973e-01           5.071e-01          -1.669e-01          -1.105e-01  
    ##         jobunknown      maritalmarried       maritalsingle  educationsecondary  
    ##         -3.252e-01          -1.944e-01           8.204e-02           2.339e-01  
    ##  educationtertiary    educationunknown          defaultyes             balance  
    ##          4.278e-01           3.140e-01          -1.024e-01           1.070e-05  
    ##         housingyes             loanyes    contacttelephone      contactunknown  
    ##         -6.794e-01          -4.405e-01          -1.008e-01          -1.638e+00  
    ##                day            monthaug            monthdec            monthfeb  
    ##          1.150e-02          -7.214e-01           5.685e-01          -2.404e-01  
    ##           monthjan            monthjul            monthjun            monthmar  
    ##         -1.284e+00          -8.702e-01           4.004e-01           1.533e+00  
    ##           monthmay            monthnov            monthoct            monthsep  
    ##         -4.452e-01          -9.431e-01           8.819e-01           8.217e-01  
    ##           duration            campaign               pdays            previous  
    ##          4.179e-03          -9.687e-02           5.061e-05           9.583e-03  
    ##      poutcomeother     poutcomesuccess     poutcomeunknown  
    ##          2.558e-01           2.384e+00          -4.598e-03  
    ## 
    ## Degrees of Freedom: 36167 Total (i.e. Null);  36125 Residual
    ## Null Deviance:       26070 
    ## Residual Deviance: 17170     AIC: 17250
