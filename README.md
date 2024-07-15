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
All of the data that I used for this project came from FBRef.com, which offers free data for several top leagues. Since FBRef doesn't have an API, I have scraped all of the data.

**Cleaning notes here

### 3 - Use Case Scenario <a name="Use_Case_Scenario"></a>
These models can be used to know more in the future about, given a player’s statistics, whether he should be making more or less money based on his statistics, and how accurately we can make these predictions.

These models can be useful for (among other things) NBA organizations when making decisions about their team's salary cap and potential players they want so sign. If considering signing a player who is currently being paid in a certain class, but who the model predicts should be making the amount of money in a class or two above, they may want to consider that the player could be in line for a pay-raise given his stats. So, that is something that they would need to be cognizant of when planning financially and allocating salaries for players.

In a similar situation, players and agents can use this model, if it shows that he is underpaid, to lobby for bigger contracts based on game statistics.
