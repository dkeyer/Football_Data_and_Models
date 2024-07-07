# NBA Salary Predictions

## Table of Contents
1. [Problem Statement and Objective](#Problem_Statement_and_Objective)
2. [Background](#Background)
3. [Data Choices, Extraction, Cleaning, and Analysis](#Data_Choices)
4. [Modeling](#Modeling)
5. [Executive Summary](#Executive_Summary)
6. [Use Case Scenario](#Use_Case_Scenario)

### 1 - Problem Statement and Objective <a name="Problem_Statement_and_Objective"></a>
Is it possible to correctly classify a National Basketball Association (NBA) player in his salary class based on his game statistics from the previous five years?

The goal of this project is to build a classification model of high accuracy, and that offers real-world applicability in the context of the NBA.

### 2 - Background <a name="Background"></a>
Players with sustained, multi-year careers in the NBA earn lucrative contracts, oftentimes in the eight-figure range in dollars earned per year. For example, the average salary of a player in the 2016-2017 season that had been in the NBA the previous five years was almost $10 million. 

Moreover, NBA contracts and salary cap (total amount teams are allowed to pay their players) are oftentimes susceptible to rapid growth, as witnessed with the new TV deal the league signed prior to the 2016-2017 season. The massive deal brought a large amount of money to the league, and in turn increased salary cap space, and eventually players' overall salary. This project examines recent years and salaries since the TV deal, and recognizes trends in classification and predictive power, year-by-year as player salaries continue to grow.

### 3 -  Data Choices, Extraction, Cleaning, and Analysis<a name="Data_Choices"></a>
The first thing I needed to do was choose the data I would work with for this project. I knew that I wanted to use NBA player statistics in order to predict player salary class, but I needed to specifically decide the time frame on which I’d focus for my predictions. I settled on using five years previous stats of a player to predict his yearly salary. For example, to predict a player’s salary in 2020, I used stats from 2016, 2017, 2018, 2019, 2020. I made this decision so as to minimize/exclude the data that would take predictive power away from my model, and for practicality in the sense that, in the future, we can use multiple years of data from the past to predict current/future salary.

I began this project with the idea of making it a regression problem, but soon after starting, realized that using classification methods would be more effective and useful. Given the small amount of data for each season, and that some "superstar" players make a yearly salary sometimes five times as large as the average, the error in prediction was very difficult to minimize. By switching to classification, the model could better deal with outliers, while still maintaining predictive power.

### 4 - Modeling <a name="Modeling"></a>
The main method used for this project was logistic regression, and the guiding metric of success was accuracy score. Several other model types were used including: k-Nearest Neighbors, Decision Tree Classifier, Extra Trees Classifiers; all of which suffered from either severe overfitting, low/insignificant accuracy scores on testing data, or both. Some kNN models approached scores of the better logistic regression models, but were never able to predict quite as accurately.

When setting up classes for classification, I initially set them manually in accordance with the quartiles of the salary data from each dataset. For example, players with salaries from 0 percentile to the 20th percentile were assigned a one. Players with salaries from the 20th percentile to the 40th percentile were assigned a 2, and so on until 5. I then trained and fit my models using these classes, and made predictions on the test data. While using this manual assignment, the logistic regression models performed the best.

I also wanted to assign the classes in a different way, and see what kind of models I could get. To do so, I used an unsupervised learning technique: kMeans Clustering. I grouped the salaries in clusters, assigned numbers to each class according to the clusters, and then scored them using the models to see what type of accuracy results I could get. The classes were mildly unbalanced when using clusters to assign classes, and the results of the models with the new classes were marginally lower than when I assigned classes manually.

Baseline models were set using all game metrics (points, rebounds, etc.) available from each dataframe. In each dataframe, the models improved significantly from the baseline. The highest accuracy score out of any of the models was over 60%, using logistic regression in the 16-20 stats dataset, more than 10% improvement from baseline.

### 5 - Executive Summary <a name="Executive_Summary"></a>
The purpose of our models is to be able to take in the statistics of any given NBA player that has been in the league for five straight seasons, and, based on his statistics over that timespan, correctly classify his salary in one of the five classes created. In manipulating the models through feature selection, feature engineering, and hyperparameter optimization, our model can be useful in classifying which players are in theory being underpaid or overpaid, and predicting whether a player will be above or below it in the future.

Building models for this project was a long process, and one that involved experimenting with different hyperparameters and features. Gridsearching was deployed throughout the modeling process, on all of the datasets. Although used with many different combinations to see if different combinations would be effective in raising predictive power and accuracy score, gridsearching was largely ineffective, and default parameters for the models typically produced the best results.

I attempted to engineer several new features so as to help raise the accuracy score and predictive power of the model. I engineered these features using SKlearn's PolynomialFeatures function. The new features were variants of the features that were significant in earlier models (A feature squared, one feature multiplied with another, etc.) There were 350 total, new engineered features. Despite having engineered so many new features, checking for correlation, and trying several different combinations of those features, the results were largely the same (even a bit lower accuracy) than the logistic regression model with the highest accuracy score. As a result, I decided not to use any results from the models including polynomial features because they did not offer enhanced performance, and they are not as interpretable in the context of basketball (an example of one of the features is 'Points per Game' times 'Games Started' -- not as interpretable as a statistic like 'Points per Game'.)

When running models with the original features, several were helpful, but a few were absolutely vital to maintaining a respectably high accuracy score. Features such as 'Games Started', 'Points per Game', 'Age', and 'Minutes Played' were vital to the model, and the accuracy score very noticeably suffered when those features were removed from the model.

### 6 - Use Case Scenario <a name="Use_Case_Scenario"></a>
These models can be used to know more in the future about, given a player’s statistics, whether he should be making more or less money based on his statistics, and how accurately we can make these predictions.

These models can be useful for (among other things) NBA organizations when making decisions about their team's salary cap and potential players they want so sign. If considering signing a player who is currently being paid in a certain class, but who the model predicts should be making the amount of money in a class or two above, they may want to consider that the player could be in line for a pay-raise given his stats. So, that is something that they would need to be cognizant of when planning financially and allocating salaries for players.

In a similar situation, players and agents can use this model, if it shows that he is underpaid, to lobby for bigger contracts based on game statistics.
