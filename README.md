# NFL Advanced Analytics on 4th down 

Time and time again we hear about coaches punting or kicking a field goal on 4th down just to hear later that they should have gone for it. So when should they really go for it? Using the combination of Exploratory Data Analysis and Machine Learning, I aim to build a model that takes into account the field position, the drive, the quarter, and anything else you can think of to predict whether or not a team is going to Punt, Kick a Field Goal, or Go for it on 4th down. 

### Table of Contents

1. [Overview](#overview)
2. [Goals](#goals)
3. [Data](#data)
4. [Analysis](#ana)
5. [Models](#model)
6. [Conclusion](#conclusion)

<a name="overview"></a>
## 1. Overview

Need a quick refresher? Check out this [video...](https://www.youtube.com/watch?v=3t6hM5tRlfA).

4th downs are considered a very important part of football. You can either add to your score or give the ball away to the other team at a worse field position. Coaches tend to be very, very conservative when it comes to "Going for it" on 4th down. Even sometimes when statistically Going for it is in their favor. I want to educate fans and coaches about their options on 4th down and what the best decision is. 


<a name="goals"></a>
## 2. Goals

**Using Exploratory Data Analysis and Machine Learning, this study predicts deicion making on 4th down and provides insight into what the outcomes could be if coaching tatics were adjusted.**

My long term goals: 
I want to use the research and analyses I have done to revolutionalize sports using Big Data. As a woman and a data scientist, I love bringing my skills and my passions to this male dominanted industry. So much more needs to be done and we will never know the advances we can make unless we do work similar to this study. 

<a name="data"></a>
## 3. Data

Thanks to Maksim Horowitz, Ron Yurko, and Sam Ventura, this data is publicly available on [Kaggle](https://www.kaggle.com/maxhorowitz/nflplaybyplay2009to2016). 
From the 2009 to the 2018 regular season, this dataset contains 449,371 rows (individual plays) and 255 columns (features). 

|Entire Dataset |                
|-----------------------------|             
|449371 individual plays|          
|255 features|                     
|2009 - 2018 regular seasons|     
|2,526 games|                          
|37,769 4th down plays|                       


**Pipeline**
The process for reading in the data for EDA purposes 
- CSV read in using pandas specifying low memory due to the size of the file. 
                  
`pd.read_csv('NFL_playbyplay.csv', low_memory=False)` 

- In order to do EDA on 4th down plays a lot of cleaning was involved:
  1. Specified all 4th down plays
  2. Got rid of plays that had penalties
  3. Changed data type of date features and created new feature engineered columns like year and month 
  4. Got rid of plays that were the last of the quarter

<a name="ana"></a>
## 4. Analysis
The best part about this project was the EDA. Finding what influences 4th down and the analyzing the discrepencies about which plays happen when was fascinating. We will take a look at some of those findings here.  
<p align="center">
<img src="graphics/pct_plays3.png" width="400" height="350">
</p>

Its no secret that Punting is far more common than Kicking a Field Goal or Going for it, but I had no idea that it was going to be this big of a gap between the three. After seeing this class imbalance the first thought was that any model would not be able to predict these classes very well if at all. 

But I decided to jump into some of the features to figure out what really makes a difference on 4th down. One previous notion was that the `yardline_100` feature, or Field Position would make a huge difference.

<p align="center">
<img src="graphics/field_pos3.png" width="550" height="400">
</p>

In this visual, along the xaxis we have the field position, 0 representing the opponents endzone and 100 representing a teams own endzone. If you know anything about football you know that A kicker cannot kick a Field Goal much further than the opponents own 40 yard line, and we can clearly see that from the Field Goal's distribution. Similarly we can see that Punting tends to be centered around a teams own 30 yard line or so. The most important thing to take away from this decomposition about subsequent play types is that all of their distributions are drastically different, we can see that although Going for it spans a larger area of the field, their distributions all vary. 

<p align="center">
<img src="graphics/qtr3.png" width="550" height="400">
</p>

<a name="model"></a>
## 5. Models

<a name="conclusion"></a>
## 6. Conclusion
