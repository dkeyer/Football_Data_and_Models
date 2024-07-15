# European Football Data Collection, Visualizations, and Models

## Table of Contents
1. [Background](#Background)
2. [Data Choices, Extraction, Cleaning, and Analysis](#Data_Choices)
3. [Use Case Scenario](#Use_Case_Scenario)
4. [Other Notes](#Other_Notes)


### 1 - Background <a name="Background"></a>
Expected goals (xG) and Expected Goals Allowed (xGA) have become a ubiquitous stat in world football (soccer). Although overall xG and xGA tell us viewers a lot about a team and its success, I'm interested in taking the analysis a bit further by looking at the xG difference of a team while the score is 0-0. Oftentimes when either team scores a goal, strategies change and xG and xGA become more lopsided, so I'm interested in learning more about teams' xG difference before the first goal sets those many changes into motion.

I also will do some analysis on xG difference dependent on the formations of different teams. More specifically, I'm interested in seeing the average total xG in games where both teams play with three center backs, only one team plays with three center backs but the other plays with two, etc. I'm also interested in seeing the total xG and goals scored per major league in Europe.

### 2 -  Data Choices, Extraction, Cleaning, and Analysis<a name="Data_Choices"></a>
The first thing I needed to do was choose the data I would work with for this project. I knew that I wanted to use NBA player statistics in order to predict player salary class, but I needed to specifically decide the time frame on which I’d focus for my predictions. I settled on using five years previous stats of a player to predict his yearly salary. For example, to predict a player’s salary in 2020, I used stats from 2016, 2017, 2018, 2019, 2020. I made this decision so as to minimize/exclude the data that would take predictive power away from my model, and for practicality in the sense that, in the future, we can use multiple years of data from the past to predict current/future salary.

I began this project with the idea of making it a regression problem, but soon after starting, realized that using classification methods would be more effective and useful. Given the small amount of data for each season, and that some "superstar" players make a yearly salary sometimes five times as large as the average, the error in prediction was very difficult to minimize. By switching to classification, the model could better deal with outliers, while still maintaining predictive power.

### 3 - Use Case Scenario <a name="Use_Case_Scenario"></a>
These models can be used to know more in the future about, given a player’s statistics, whether he should be making more or less money based on his statistics, and how accurately we can make these predictions.

These models can be useful for (among other things) NBA organizations when making decisions about their team's salary cap and potential players they want so sign. If considering signing a player who is currently being paid in a certain class, but who the model predicts should be making the amount of money in a class or two above, they may want to consider that the player could be in line for a pay-raise given his stats. So, that is something that they would need to be cognizant of when planning financially and allocating salaries for players.

In a similar situation, players and agents can use this model, if it shows that he is underpaid, to lobby for bigger contracts based on game statistics.
