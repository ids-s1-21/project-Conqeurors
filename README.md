Client Behavior Prediction Model (For term-deposit subscriptions in
banking)
================
by Conquerors

## Summary

Our team decided to make a presentation on the data of a bank’s
marketing campaign about whether clients would subscribe to a term
deposit based on their characteristics. The question we asked ourselves
was ‘Which variables (or combinations of these) are the most important
indicators when determining whether an individual will subscribe to a
term deposit?’. We built a logistic regression model to answer which
variables are the most important indicators. Firstly, we made some
preliminary data analysis and visualizations to get a general gist of
our data. We then used advanced statistical and modelling techniques to
create an adequate model and finally tested it in a separate set of data
it had never seen before to properly assess its performance.

The first thing we did with the data was a preliminary visualization,
which we used to compare the outcome variable with the variables
themselves, and these with one another. This helped us understand what
variables were more important in determining whether someone would
subscribe to a term deposit. When looking at the visualization that
generally describes the number of clients who subscribed to a term
deposit, we can see that the number of clients who did not subscribe to
a term deposit far outweighs the number of clients who did subscribe.
This is important to keep in mind and allows us to assess the scenario
from a general scope. Firstly, looking at the visualization of whether
clients subscribed or not faceted by Jobs, allows us to see that an
individual’s job does correlate with whether he/she will subscribe or
not. For instance, students seemingly have a much higher proportion of
subscriptions than the other jobs. Also, the month of contact is highly
relevant in determining subscription success, as there are months that
the bank places a lot more focus on. Looking at the next graphic of
methods of contact versus subscription status, suggests that methods of
contact correlates highly with whether clients subscribed or not. When
clients were contacted through cellular devices there was a much higher
proportion of subscriptions. The last visualization between number of
days since a client was contacted and whether they subscribed, is an
example of a variable that has little to no impact on the outcome.
variables like these can be removed from our logistic regression model.
Finally, we used a correlation matrix to compare all the numerical
variables and to observe if there was any correlation between these. We
don’t want a strong correlation between our explanatory variables as
this can lead to collinearity. With all of these visualizations and
preliminary analysis, we were ready to create our logistic regression
model.

To create our model we first downloaded train and test data sets. We
first split our train data set randomly into sub-train (80% of the size
of the original) and sub-test sets (20% of the size of the original). We
also changed the outcome variable from a character to a factor as this
is necessary when dealing with a logistic model. After this, we began
working on our recipe. Our recipe steps are as follows: Remove the pdays
variable because it had minimal correlation with our outcome, cut the
campaign variable in breaks of 0 and 1(whether the client was contacted
before or not), create relevant age groups, create times of the month
from the day variable, classify calls by their duration in minutes
rather than seconds, create dummy variables and removed zero variance
variables. We then created a workflow from this recipe and fit it to our
model and data.

At this moment, we were able to conduct our first test. This test was
quite a success with an area under the ROC of .908. Nonetheless, this
success could potentially be meaningless due to possible over fitting.
To make sure that was not the case, we decided to carry out cross
validation using ten folds. This number is logical based on the large
size of our data set (+40,000 observations). The result from this test
was that our model had an average accuracy of 0.898. With this, we were
ready to run our test on the official and untouched test data set.

The results of our final test were surprisingly positive. Our model had
achieved an accuracy of 0.9011344. Our Research Question was answered:
call duration, month of the year and past campaign outcome were the most
relevant predictors to our outcome variable. In addition, we managed to
build a model which predicted with 90% certainty whether or not a client
would subscribe to a term deposit. In fact, our model was much better at
predicting whether a client would not subscribe.

The ethics aspect of our project must also be analyzed. Logistic
regression models are used by countless financial institutions and even
though these are effective, if misused, can result in discrimination and
other unethical outcomes.

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

*Correlation matrix : A quick start guide to analyze, format and
visualize a correlation matrix using R software* Statistical tools for
high-throughput data analysis,
<http://www.sthda.com/english/wiki/correlation-matrix-a-quick-start-guide-to-analyze-format-and-visualize-a-correlation-matrix-using-r-software>
