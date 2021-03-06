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
banking_train%>%
  ggplot(aes(x=job,y=y))+
  geom_jitter()+
   labs(
    x = "Jobs",
    y = "Clients subscribed?",
    title = "Relationship between clients jobs 
    and whether they subsribe to term deposits",
  ) 
```

![](Preliminary-Visualizations_files/figure-gfm/17%20graph%20grid-1.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(x=age,y=y))+
  geom_jitter()+
 labs(
    x = "Age",
    y = "Clients subscribed?",
    title = "Relationship between clients age and whether they subsribe to term deposits",
  ) 
```

![](Preliminary-Visualizations_files/figure-gfm/17%20graph%20grid-2.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(x=marital,y=y))+
  geom_jitter()+
 labs(
    x = "Marital status",
    y = "Clients subscribed?",
    title = "Relationship between clients  marital status 
    and whether they subsribe to term deposits",
  ) 
```

![](Preliminary-Visualizations_files/figure-gfm/17%20graph%20grid-3.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(x=education,y=y))+
  geom_jitter()+
 labs(
    x = "Education",
    y = "Clients subscribed?",
    title = "Relationship between clients education 
    and whether they subsribe to term deposits",
  ) 
```

![](Preliminary-Visualizations_files/figure-gfm/17%20graph%20grid-4.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(x=default,y=y))+
  geom_jitter()+
 labs(
    x = "default",
    y = "Clients subscribed?",
    title = "Relationship between clients default status 
    and whether they subsribe to term deposits",
  ) 
```

![](Preliminary-Visualizations_files/figure-gfm/17%20graph%20grid-5.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(x=balance,y=y))+
  geom_jitter()+
 labs(
    x = "balance",
    y = "Clients subscribed?",
    title = "Relationship between clients balance 
    and whether they subsribe to term deposits",
  ) 
```

![](Preliminary-Visualizations_files/figure-gfm/17%20graph%20grid-6.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(x=housing,y=y))+
  geom_jitter()+
 labs(
    x = "Housing",
    y = "Clients subscribed?",
    title = "Relationship between clients housing 
    and whether they subsribe to term deposits",
  ) 
```

![](Preliminary-Visualizations_files/figure-gfm/17%20graph%20grid-7.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(x=loan,y=y))+
  geom_jitter()+
 labs(
    x = "Loan status?",
    y = "Clients subscribed?",
    title = "Relationship between clients loan status 
    and whether they subsribe to term deposits",
  ) 
```

![](Preliminary-Visualizations_files/figure-gfm/17%20graph%20grid-8.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(x=contact,y=y))+
  geom_jitter()+
 labs(
    x = "Methods of contact",
    y = "Clients subscribed?",
    title = "Relationship between clients methods contact 
    with the bank and whether they subsribe to term deposits",
  ) 
```

![](Preliminary-Visualizations_files/figure-gfm/17%20graph%20grid-9.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(x=day,y=y))+
  geom_jitter()+
 labs(
    x = "Day",
    y = "Clients subscribed?",
    title = "Relationship between the day 
    and whether they subsribe to term deposits",
  ) 
```

![](Preliminary-Visualizations_files/figure-gfm/17%20graph%20grid-10.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(x=month,y=y))+
  geom_jitter()+
 labs(
    x = "Month",
    y = "Clients subscribed?",
    title = "Relationship between the month 
    and whether they subsribe to term deposits",
  ) 
```

![](Preliminary-Visualizations_files/figure-gfm/17%20graph%20grid-11.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(x=duration,y=y))+
  geom_jitter()+
 labs(
    x = "Clients subscribed?",
    y = "Duration of last contact",
    title = "Relationship between clients duration of last contact 
    with the bank and whether they subsribe to term deposits",
  ) 
```

![](Preliminary-Visualizations_files/figure-gfm/17%20graph%20grid-12.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(x=campaign,y=y))+
  geom_jitter()+
 labs(
    x = "Contacts this campaign",
    y = "Clients subscribed?",
    title = "Relationship between the number of contacts performed 
    during this campaign and whether they subsribe to term deposits",
  ) 
```

![](Preliminary-Visualizations_files/figure-gfm/17%20graph%20grid-13.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(x=pdays,y=y))+
  geom_jitter()+
 labs(
    x = "Pdays",
    y = "Clients subscribed?",
    title = "Relationship between the number of days that passed 
    by after the client was last contacted from a previous campaign  
    and whether they subsribe to term deposits",
  ) 
```

![](Preliminary-Visualizations_files/figure-gfm/17%20graph%20grid-14.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(x=previous,y=y))+
  geom_jitter()+
 labs(
    x = "Previous contacts",
    y = "Clients subscribed?",
    title = "Relationship between the number of contacts  
    performed before this campaign and whether they subsribe to term deposits",
  ) 
```

![](Preliminary-Visualizations_files/figure-gfm/17%20graph%20grid-15.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(x=poutcome,y=y))+
  geom_jitter()+
 labs(
    x = "Clients prior marketing campaign outcome",
    y = "Clients subscribed?",
    title = "Relationship between clients prior marketing campaign outcome 
    and whether they subsribe to term deposits",
  ) 
```

![](Preliminary-Visualizations_files/figure-gfm/17%20graph%20grid-16.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(y=age,color=y))+
  geom_bar()+
 labs(
    y = "Age",
    color= "Clients subscribed?",
    title = "Relationship between clients jobs 
    and whether they subsribe to term deposits",
  ) 
```

![](Preliminary-Visualizations_files/figure-gfm/graph%20grid-1.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(y=job,color=y))+
  geom_bar()+
labs(
    y = "Job",
    color= "Clients subscribed?",
    title = "Relationship between clients age 
    and whether they subsribe to term deposits",
  ) 
```

![](Preliminary-Visualizations_files/figure-gfm/graph%20grid-2.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(y=marital,color=y))+
  geom_bar()+
  labs(
    y = "Marital",
    color= "Clients subscribed?",
    title = "Relationship between clients marital
    and whether they subsribe to term deposits",
  ) 
```

![](Preliminary-Visualizations_files/figure-gfm/graph%20grid-3.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(y=education,color=y))+
  geom_bar()+
  labs(
    y = "Education",
    color= "Clients subscribed?",
    title = "Relationship between clients education
    and whether they subsribe to term deposits",
  ) 
```

![](Preliminary-Visualizations_files/figure-gfm/graph%20grid-4.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(y=default,color=y))+
  geom_bar()+
  labs(
    y= "default",
    color= "Clients subscribed?",
    title = "Relationship between clients default status
    and whether they subsribe to term deposits",
  ) 
```

![](Preliminary-Visualizations_files/figure-gfm/graph%20grid-5.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(y=balance,color=y))+
  geom_bar()+
  labs(
    y = "Balance",
    color= "Clients subscribed?",
    title = "Relationship between clients balance
    and whether they subsribe to term deposits",
  ) 
```

![](Preliminary-Visualizations_files/figure-gfm/graph%20grid-6.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(y=housing,color=y))+
  geom_bar()+
  labs(
    y= "Housing",
    color= "Clients subscribed?",
    title = "Relationship between clients housing
    and whether they subsribe to term deposits",
  ) 
```

![](Preliminary-Visualizations_files/figure-gfm/graph%20grid-7.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(y=loan,color=y))+
  geom_bar()+
  labs(
    y = "Loan status",
    color= "Clients subscribed?",
    title = "Relationship between clients loan status
    and whether they subsribe to term deposits",
  ) 
```

![](Preliminary-Visualizations_files/figure-gfm/graph%20grid-8.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(y=contact,color=y))+
  geom_bar()+
  labs(
    y= "Methods of contact",
    color= "Clients subscribed?",
    title = "Relationship between clients methods of 
    contact and whether they subsribe to term deposits",
  ) 
```

![](Preliminary-Visualizations_files/figure-gfm/graph%20grid-9.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(y=day,color=y))+
  geom_bar()+
  labs(
    y = "Day",
    color= "Clients subscribed?",
    title = "Relationship between the day 
    and whether they subsribe to term deposits",
  ) 
```

![](Preliminary-Visualizations_files/figure-gfm/graph%20grid-10.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(y=month,color=y))+
  geom_bar()+
  labs(
    x = "Month",
    color= "Clients subscribed?",
    title = "Relationship between the Month
    and whether they subsribe to term deposits",
  ) 
```

![](Preliminary-Visualizations_files/figure-gfm/graph%20grid-11.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(y=duration,color=y))+
  geom_bar()+
  labs(
    x = "Duration of last contact",
    color= "Clients subscribed?",
    title = "Relationship between the duration of last contact
    and whether they subsribe to term deposits",
  ) 
```

![](Preliminary-Visualizations_files/figure-gfm/graph%20grid-12.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(y=campaign,color=y))+
  geom_bar()+
   labs(
    x = "Contacts this campaign",
    color = "Clients subscribed?",
    title = "Relationship between the contacts this campaign
    and whether they subsribe to term deposits",
  )
```

![](Preliminary-Visualizations_files/figure-gfm/graph%20grid-13.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(y=pdays,color=y))+
  geom_bar()+
   labs(
    x = "the number of days that passed 
    by after the client was last contacted",
    color = "Clients subscribed?",
    title = "Relationship between the number of days that passed 
    by after the client was last contacted
    and whether they subsribe to term deposits",
  )
```

![](Preliminary-Visualizations_files/figure-gfm/graph%20grid-14.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(y=previous,color=y))+
  geom_bar()+
  labs(
    x = "Previous contacts",
    color = "Clients subscribed?",
    title = "Relationship between the previous contacts last campaign
    and whether they subsribe to term deposits",
  )
```

![](Preliminary-Visualizations_files/figure-gfm/graph%20grid-15.png)<!-- -->

``` r
banking_train%>%
  ggplot(aes(y=poutcome,color=y))+
  geom_bar()+
   labs(
    x = "Clients prior marketing campaign outcome",
    color = "Clients subscribed?",
    title = "Relationship between the clients prior marketing campaign outcome
    and whether they subsribe to term deposits",
  )
```

![](Preliminary-Visualizations_files/figure-gfm/graph%20grid-16.png)<!-- -->
