Fantasy Football Rookie RBs and WRs Projection Project
======================================================

In this project, I wanted to build a model that could predict which rookie running backs and wide receivers would have the most successful season. I did this by building a model tested against 2022 rookies, then seeing the results the model gave me for the 2023 rookies (this is before the 2023 season). I then dug further to see what trends I could find within the players that did succeed. In this project, I showed examples of data scraping with Beautiful Soup, data cleaning, linear regressions with Scikit-Learn, SVMs, K Means Clustering, and K Nearest Neighbors.

Summary
-------

[Here is a visualization](https://public.tableau.com/app/profile/kevin.le8759/viz/FantasyTopFinishesDashboardRB-WR2018-2022/WRDash) I put together in Tableau as a way to explore the results. There is a dash for running backs and a dash for wide receivers. On each you can hover over the circles to see the players that finished top 5 amongst rookies between 2018-2022. Clicking on their circle will filter out the upper dash to show where they stood on key metrics relative to the full data set average. I give an explanation on the right of each dash what you should be looking for with the key metrics.

This project is broken down into three parts, in which you can find the links to below for full code and project..

-   [1\. Data Scraping and Cleaning](https://github.com/kevinkietle/Fantasy-Football-Rookie-Project/blob/main/1.%20Fantasy%20Rookie%20RBs-WRs%20Data%20Scraping%20and%20Cleaning.ipynb)

-   [2\. Rookie Running Backs Analysis](https://github.com/kevinkietle/Fantasy-Football-Rookie-Project/blob/main/2.%20Fantasy%20Rookie%20RBs.ipynb)

-   [3\. Rookie Wide Receivers Analysis](https://github.com/kevinkietle/Fantasy-Football-Rookie-Project/blob/main/3.%20Fantasy%20Rookie%20WRs.ipynb)

Main takeaways:

-   The linear regression models for both running backs and wide receivers had R scores over 0.60, meaning they are relatively strong in predicting the fantasy points per game finishes of rookies (or at least the ranking).

-   For both models, the draft pick of a player is the most significant predictor of rookie year fantasy success.

-   The quality of the next best teammate at the position is also very important. 

-   For running backs, significant predictors include the number of games the teammate played the previous year and their yards per attempt. The more games the teammate played, the higher the predicted points per game of the rookie is, likely because of running back wear down and a factor of "you know what you have" in the previous guy. The lower the yards per attempt of the teammate, the higher the predicted FPPG of the rookie is because the teammate is not that good.

-   For wide receivers, significant predictors include teammate first downs and teammate yards per reception. The more first downs the teammate had the previous year, the higher the predicted FPPG of the rookie is. The lower the yards per reception of the best WR teammate is, the higher the predicted FPPG of the rookie is. The theory behind this is that the best teammate is a possession receiver and the team has a need for a big play option - it is these big play threats that actualize strong rookie WR seasons.

-   For 2023:

-   Bijan Robinson and Jahmyr Gibbs are the obvious candidates to have strong rookie RB seasons. The model suggests Devon Achane may have a strong season as well.

-   The highest projected FPPG among 2023 rookie WRs are Zay Flowers and Jayden Reed, both guys who are going very low in drafts and can be sleepers.

Data Scraping and Cleaning
--------------------------

Using Beautiful Soup, I scraped the rushing and receiving stats pages from Football Reference for the 2017-2022 seasons. I used this for the teammate stats as well as the rookie's final stats (not including 2023 rookies). I also prefilled a dataset in Excel with rookie RBs and WRs between 2017-2023 with data like height, weight, 40 time, and pick number. I used AI to fill in most of the table.

For cleaning, I consolidated extra rows for players that played on multiple teams in one year and removed asterisks by players' names. I created a few calculated columns such as fantasy points per game (FPPG) and fantasy point totals for the year. FPPG was more successful so most of the project is done with that stat. These fantasy scores are calculated based on a PPR scoring format.

Running Backs
-------------

I ran linear regression models with 2018-2021 rookies as the training set and 2022 rookies as the test set. This resulted in an R score of 0.64 for the model based on FPPG. The model correctly predicted the top 3 finishers of 2022: Dameon Pierce, Breece Hall, and Kenneth Walker.

With the model validated, I now ran another model with 2022 included in the training set and 2023 as the test set. This model predicted Bijan Robinson, Jahmyr Gibbs, and Devon Achane as the top 3 finishers in FPPG, in that order.

The model suggested looking at a player's draft capital, number of games the best RB teammate played the year before, and the teammate's previous year yards per attempt. Explanation is given in the summary section above. Check out how the top 5 running backs from each year fared in these categories [HERE](https://public.tableau.com/app/profile/kevin.le8759/viz/FantasyTopFinishesDashboardRB-WR2018-2022/RBDash)

I then ran some more models to spot trends of RBs that finish top 5 amongst rookies. I ran a SVM model with the target being top 5 within a respective season. This model was not successful, correctly predicting about 1 in 5 of top 5 finishes.

I also ran a K Means Clustering model to spot trends in players that finish top 5. A few of the clusters include quick, explosive backs with good draft capital (second rounders); bruising, run-first guys who have large carrying responsibility; and strong pass catchers.

Wide Receivers
--------------

I ran linear regression models with 2018-2021 rookies as the training set and 2022 rookies as the test set. This resulted in an R score of 0.68 for the model based on FPPG. The model correctly predicted 2 of the top 5 finishes by selecting Wan'Dale Robinson, Garrett Wilson, Treylon Burks, Jameson WIlliams, and Chris Olave in that order.

With the model validated, I now ran another model with 2022 included in the training set and 2023 as the test set. This model predicted Zay Flowers, Jayden Reed, Jaxon Smith-Njigba, Nathaniel Dell, and Jonathan Mingo as the top 5 finishers in FPPG, in that order.

The model suggested looking at a player's draft capital, number of first downs the best WR teammate played the year before, and the teammate's previous year yards per reception. Explanation is given in the summary section above. Check out how the top 5 wide receivers from each year fared in these categories [HERE](https://public.tableau.com/app/profile/kevin.le8759/viz/FantasyTopFinishesDashboardRB-WR2018-2022/WRDash)

I then ran a K Nearest Neighbors model to see if I could predict who would finish top 5 within a given year. The best results I could achieve for correctly selecting top 5 finishes was a precision percentage of 22% and a recall percentage of 40%.

I also ran a K Means Clustering model to spot trends in players that finish top 5. The clusters here were not as clear as the running back clusters but most of the players are first or second round picks with big play capability.

&nbsp;
&nbsp;
&nbsp;

Hope you enjoyed reading through this project!

Feel free to contact me with any questions or inquiries.

LinkedIn - <https://www.linkedin.com/in/kevinkietle/>

Email - <kevinkietle@gmail.com>
