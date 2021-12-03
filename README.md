Client Behavior Prediction Model (For term-deposit subscriptions in
banking)
================
by Conquerors

## Summary

Our team decided to make a presentation on the data of a bank’s
marketing campaign about if clients will subscribe to their term
deposit. The question we asked ourselves was ‘Which variables (or
combinations of these) are the most important indicators when
determining whether an individual will subscribe to a term deposit?’.

We built a logistic regression model to answer which variables are the
most important indicators when determining whether an individual will
subscribe to a term deposit. Firstly, we made some preliminary data
analysis and visualizations to get a general gist of our data. We then
used advanced statistical and modelling techniques to create an adequate
model and finally tested it in a separate set of data it had never seen
before to properly assess its performance.

The original data collection comes from the 2008-2013 records of a
Portuguese Banking Institution and their success in convincing clients
to subscribe to term deposits. It is called “Banking Dataset - Marketing
Targets” by Prakhar Rathi and contains data derived from *S. Moro, P.
Cortez and P. Rita.-A Data-Driven Approach to Predict the Success of
Bank Telemarketing*.

The first thing we did with the data was a preliminary visualization,
which we used to compare the outcome variable with the variables
themselves. This helped us understand what variables were more important
in determining whether someone would subscribe to a term deposit. When
looking at the visualization that generally describes the number of
clients who subscribed to their term deposit, we can see that the number
of clients who did not subscribe to their term deposit far outweighs the
number of clients who did subscribe. This is important to keep in mind
when looking at how the variables correlate with getting a term deposit
in the graphs.Firstly looking at the visualization of whether clients
subscribed or not faceted, we can see that the variable jobs does
correlate with whether clients subscribe or not, for example the
students seemingly have a much higher proportion of clients who
subscribed, then the other observations for jobs.Looking at the next
graphic of methods of contact versus subscription status, it also
suggests that methods of contact correlates with whether clients
subscribed or not. As when clients were contacted through cellular
devices there was much higher proportion of subscriptions,then when they
were not.The last model looking at the correlation between number of
days since they were contacted and whether they subscribed, there is a
clear correlation.As when the number days increases the proportion of
clients who subscribed drastically falls, showing there is a clear
correlation between number of days since a client was contacted and
whether the client subscribes.

We then used a correlation matrix to compare all the numerical variables
and to observe if there are any correlation between variables. From this
we the had enough information to create the logistic regression model

The downloaded 2 data sets- test and train- the test data set is 10% of
the train data set.

We made a recipe for the model by removing pdays variable because it had
minimal correlation with our outcome, cutting the campaign variable in
breaks of 0 and 1, creating relevant age groups, creating times of the
month from the day variable, classifying calls by their duration in
minutes rather than seconds and creating dummy variables and removed
zero variance variables.

The model we used was 90% effective in determining whether an individual
will subscribe to a term deposit or not so therefore they are used often
in banking and other areas however there are many ethical implications
from this as it is segregating or discriminating racial, age, or job
groups- the conditions may not be fair.

## Presentation

Our presentation can be found [here](presentation/presentation.html).

## Data

Moro, S, Cortez, P and Rita, P, June 2014, *A Data-Driven Approach to
Predict the Success of Bank Telemarketing.* Decision Support Systems,
Elsevier, 62:22-31, viewed
\<<https://www.kaggle.com/prakharrathi25/banking-dataset-marketing-targets>\>

## References

Moro, S, Cortez, P and Rita, P, June 2014, *A Data-Driven Approach to
Predict the Success of Bank Telemarketing.* Decision Support Systems,
Elsevier, 62:22-31, viewed
\<<https://www.kaggle.com/prakharrathi25/banking-dataset-marketing-targets>\>
