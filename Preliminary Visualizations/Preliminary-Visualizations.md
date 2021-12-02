Preliminary Visualizations
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
#variableGraphs<-function(df,name){
 # variable<- banking_test[ , name]
   #variable<- banking_test[ , name] %>%
banking_train%>%
  ggplot(aes(x=job,y=y))+
  geom_jitter()
```

![](Preliminary-Visualizations_files/figure-gfm/17%20graph%20grid-1.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(x=age,y=y))+
  geom_jitter()
```

![](Preliminary-Visualizations_files/figure-gfm/17%20graph%20grid-2.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(x=marital,y=y))+
  geom_jitter()
```

![](Preliminary-Visualizations_files/figure-gfm/17%20graph%20grid-3.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(x=education,y=y))+
  geom_jitter()
```

![](Preliminary-Visualizations_files/figure-gfm/17%20graph%20grid-4.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(x=default,y=y))+
  geom_jitter()
```

![](Preliminary-Visualizations_files/figure-gfm/17%20graph%20grid-5.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(x=balance,y=y))+
  geom_jitter()
```

![](Preliminary-Visualizations_files/figure-gfm/17%20graph%20grid-6.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(x=housing,y=y))+
  geom_jitter()
```

![](Preliminary-Visualizations_files/figure-gfm/17%20graph%20grid-7.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(x=loan,y=y))+
  geom_jitter()
```

![](Preliminary-Visualizations_files/figure-gfm/17%20graph%20grid-8.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(x=contact,y=y))+
  geom_jitter()
```

![](Preliminary-Visualizations_files/figure-gfm/17%20graph%20grid-9.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(x=day,y=y))+
  geom_jitter()
```

![](Preliminary-Visualizations_files/figure-gfm/17%20graph%20grid-10.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(x=month,y=y))+
  geom_jitter()
```

![](Preliminary-Visualizations_files/figure-gfm/17%20graph%20grid-11.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(x=duration,y=y))+
  geom_jitter()
```

![](Preliminary-Visualizations_files/figure-gfm/17%20graph%20grid-12.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(x=campaign,y=y))+
  geom_jitter()
```

![](Preliminary-Visualizations_files/figure-gfm/17%20graph%20grid-13.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(x=pdays,y=y))+
  geom_jitter()
```

![](Preliminary-Visualizations_files/figure-gfm/17%20graph%20grid-14.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(x=previous,y=y))+
  geom_jitter()
```

![](Preliminary-Visualizations_files/figure-gfm/17%20graph%20grid-15.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(x=poutcome,y=y))+
  geom_jitter()
```

![](Preliminary-Visualizations_files/figure-gfm/17%20graph%20grid-16.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(y=age,color=y))+
  geom_bar()
```

![](Preliminary-Visualizations_files/figure-gfm/graph%20grid-1.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(y=job,color=y))+
  geom_bar()
```

![](Preliminary-Visualizations_files/figure-gfm/graph%20grid-2.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(y=marital,color=y))+
  geom_bar()
```

![](Preliminary-Visualizations_files/figure-gfm/graph%20grid-3.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(y=education,color=y))+
  geom_bar()
```

![](Preliminary-Visualizations_files/figure-gfm/graph%20grid-4.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(y=default,color=y))+
  geom_bar()
```

![](Preliminary-Visualizations_files/figure-gfm/graph%20grid-5.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(y=balance,color=y))+
  geom_bar()
```

![](Preliminary-Visualizations_files/figure-gfm/graph%20grid-6.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(y=housing,color=y))+
  geom_bar()
```

![](Preliminary-Visualizations_files/figure-gfm/graph%20grid-7.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(y=loan,color=y))+
  geom_bar()
```

![](Preliminary-Visualizations_files/figure-gfm/graph%20grid-8.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(y=contact,color=y))+
  geom_bar()
```

![](Preliminary-Visualizations_files/figure-gfm/graph%20grid-9.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(y=day,color=y))+
  geom_bar()
```

![](Preliminary-Visualizations_files/figure-gfm/graph%20grid-10.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(y=month,color=y))+
  geom_bar()
```

![](Preliminary-Visualizations_files/figure-gfm/graph%20grid-11.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(y=duration,color=y))+
  geom_bar()
```

![](Preliminary-Visualizations_files/figure-gfm/graph%20grid-12.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(y=campaign,color=y))+
  geom_bar()
```

![](Preliminary-Visualizations_files/figure-gfm/graph%20grid-13.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(y=pdays,color=y))+
  geom_bar()
```

![](Preliminary-Visualizations_files/figure-gfm/graph%20grid-14.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(y=previous,color=y))+
  geom_bar()
```

![](Preliminary-Visualizations_files/figure-gfm/graph%20grid-15.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(y=poutcome,color=y))+
  geom_bar()
```

![](Preliminary-Visualizations_files/figure-gfm/graph%20grid-16.png)<!-- -->

``` r
#variableGraphs(df=banking_test, name=c("job"))
```
