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
All of the data that I used for this project came from FBRef.com, which offers free data for several top leagues. Since FBRef doesn't have an API, I have scraped all of the data. For each league, I scraped the league table, all of the fixtures (games) for that league, and all of the shots from each of those fixtures. I was then able to amend the shots dataframe (shots_df) to accomodate the shot-taker's team as well as the opposing team. The league and fixtures tables themselves have season-long and per-game xG, but it would have been impossible to know the xG and xGA while nil-nil (zero-zero) using these already existing tables. We also now have xG at the same "grain" as formations which allows us to sum the xG while accounting for formation.

The first page I scraped was the Scores & Fixtures page, which gives a general overview of every game in that season (home and away xG, final score, stadium, referee, etc.) Since all of the data is returned in HTML format, the first thing I had to do was loop through the responses and trim off the tags and other excess characters, and load it into a pandas dataframe. The next step was getting the shot data, which was a bit tricky because rather than being at the same URL, a user must click a unique game link to see all of the shots for a given game. So I scraped each unique game id that comes from each of those individual links and stored them in a list called game_ids. I then went to the 'matches' page for that league and looped through each unique game id -- appending it to the match URL.


### 3 - Use Case Scenario <a name="Use_Case_Scenario"></a>
These scripts can be used by the public not only for data collection, but also for engineered features not typically available on a soccer data website. The script compiles data into neat pandas dataframes which are ready for analysis, visualizations, and modeling.

These models can be useful for (among other things) NBA organizations when making decisions about their team's salary cap and potential players they want so sign. If considering signing a player who is currently being paid in a certain class, but who the model predicts should be making the amount of money in a class or two above, they may want to consider that the player could be in line for a pay-raise given his stats. So, that is something that they would need to be cognizant of when planning financially and allocating salaries for players.

In a similar situation, players and agents can use this model, if it shows that he is underpaid, to lobby for bigger contracts based on game statistics.
