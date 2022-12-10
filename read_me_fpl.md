# Linear Programming and predictions - Fantasy Premier League

## Context
Fantasy Premier League is well-known online game where each week ~9million managers try to pick the best team from players in the English Premier League. Points are attributed to players based on their actuel performance on the pitch.
<br> Leveraging the important volume of data available on each games and players could help make educated guess on best team to pick and avoid all different types of bias and subjective decisions.

## Objectives
1. **Identify key statistics and metrics behind FPL** - validating or not assumptions, myths and beliefs
2. Compare different models *(LinearRegression, KNN, RandomForest)* performance while attempting to **predict weekly points** per players based on key features identified
3. **Pick best team** *(maximizing number of points)* per game weeks using LinearProgramming (PulP library)

## Content

### Import, explore and prepare data
* Import data from API *(4 different end-points)*
* Data cleaning
* Data exploration
  * *Players with most goals, assists or bonus points?* **Salah makes it to the podium in all three categories**
  * *Players with most dream team selection or minutes played?* **Surprisingly CR7 joins Salaha and Son on the podium**
  * *Players with best transfer delta?* **Cancelo seems to be by far the best surprise of the season with transfer delta 2x the runner-up Dennis. Cancelo's value has increased by 1.2 (only matched by Son)**
  * *Players with highest value for money?* **Matip, Bowen, Coady and Ramsdale are all joining Cancelo with 30+ points per cost. Interesting to see that assumptions that FWD and MID are better value for money is validated**
  * *On what gameweeks are chips played the most?* **With the exception of wildcard which is played the most within first 5 Gameweeks (once manager have a better understanding of teams/players form),  most chips are playes in 2nd half of the season with bench bosst peaking in the last Gameweeks as managers try to make their way back**
  * *On what gameweeks do most transfers happen?* **First 5 gameweeks as well as Boxing days are where most transfers happen**
  * *What players have been the most captained or top scorer?* **Fun fact: It only happened once that the most captained player was also the top scorer**
  * *Players with the most FPL seasons or total points?* **Long has 18 seasons on the PL, while Milner has accumulated the highest number of points (~1500)**
  * *Which games would be worth watching again?* **Based on number of bps attributed it would be ManCity's 7-0 victory. Interesting to note tha team playing at home tend to score more goals and make for bps**
  * *Which player to pick for which use cases?* **You wouldn't pick the same players if you are far behind with a couple of ronds left or if you are willing to defend your position. For example van Dijk was scoring 5+ points 60% of the time (vs.40% for Bowen), however Bowen scored 10+ points 25% of the time (vs. 10% for van Dijk). You will need to understand how much risk is worht taking**
* Linear Programming on historical data (using pulp package)
  * *Best 15 players team which could have been picked based on previous season (no chips and costs based on season start)?* **1856 points (vs. 2844 winner vs. 1990 myself with no tranfers or team changes since season start)** 
  * *Best 15 and 11 players teams which could have been picked at start of season (no chips and costs based on season start)?* **2962 points for 15 players and 2144 for 11 players; interesting to see combinations with less forwards scoring more points**
* Correlation among key features
  * *Features most correlated with "Total points"?* **bps, value, influence, ict_index, minutes, clean_sheets, bonus, thread, creativity, ..**
* Feature engineering
  * Decision taken after data exploration to leverage data of last 3 gameweeks (average or max depending on metrics) as well as meta data of upcoming game to feed ML models
* Feature encoding

### ML models
* Decision taken to **build 1 model for each position** *(Defenders, Midfielders, Forwards and Goalkeepers)* as features have different importance for each groups
* Baseline, LinearRegression *(incl. hyperparameter tuning)*, KNN Regressor, RandomForest Regressor; **LinearRegression over-performing other models altoug all with low R2 performance; KNN and RF over-fitting to train set**

### Predictions
* Use models fitted on '21/22 season to predict 1st half of '22/23 season; as previewed on validation set of '21/22 season **models seems to be struggling with predicting higher performance and tend to predict much lower values** *(which could work if ranking is still correct)*
* Linear Programming applied to select team for first 3 gameweeks based on previous season and then each gameweeks based on points predicted
  * Relatively poor performance of teams selected based on points prediction and linear programming due to bad models accuracy/performance 
 
<img src="images/airbnb_nulls_card.jpg?raw=true"/>
<img src="images/airbnb_age.jpg?raw=true"/>
<img src="images/airbnb_correlation.jpg?raw=true"/>

## Conclusion
A. Overall many interesting findings on the key statistics behind FPL, however **given the nature of football it is hard to make accurate predictions only looking at historical data**
<br>B. **Linear Programming allows to solve the complex equation trying to maximize points without going over the budegt**. Without LP calculating all different combinatinations and permutation would be almost impossible in regards to coputing power and time needed

*For more details see [GitHub ML projects - Fantasy Premier League-Moneyball project - Gregoire LAURENT]([https://github.com/Greg1806/ML_projects/blob/main/Kaggle_airbnb.ipynb](https://github.com/Greg1806/ML_projects/blob/main/Fantasy_moneyball_project.ipynb))*
