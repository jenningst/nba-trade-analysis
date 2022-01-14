# NBA Player Trade Analysis

![](https://github.com/jenningst/nba-trade-analysis/blob/main/images/markus-spiske-BfphcCvhl6E-unsplash)
<p align='center'>Photo by <a href="https://unsplash.com/@markusspiske?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Markus Spiske</a> on <a href="https://unsplash.com/wallpapers/sports/basketball?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a></p>

In this project, we attempt to answer the following questions: what comparisons can we make between clusters through a K-Means algorithm vs. a DBSCAN algorithm, and are these methods suitable for comparing player similarity in the NBA (National Basketball Association) based on individual player in-game statistics? The dataset for this project will include individual per-game player statistics from the National Basketball Association (NBA).

## Motivation

Fantasy sports leagues enable fans (“commissioners”) to put together a virtual team of real-life players, to compete against other virtual teams in a variety of formats, based on the players’ actual game statistics. In fantasy sports, the objective is to assemble a team of NBA players through a mock draft. These teams accumulate fantasy points across categories over the course of a season, determining the virtual team’s rank in each category. The final standings of the fantasy teams at the end of the season determine the league winner. Players’ statistics and other metrics will be evaluated in this project including the following: player position, minutes played, points, three-points made, field goals made, free throws made, offensive/defensive rebounds, assists, steals, blocks, turnovers, and date played on. The idea throughout this project will be to evaluate players statistics through clustering.

## Assumptions

To keep the project less complex, we have to make some basic assumptions:
- trade analysis is only completed on players of the same position
- clustering methods yeild similar results across disparate player position types (e.g., Guard, Forward, Center)

## Method and Results 

To tackle the research question, we aim to classify players into an optimal number of clusters (K-Means) or based on optimal epsilon (DBSCAN), plot the most optimal clusters, and evaluate the created clusters across desired statistics to determine if we can evaluate a player trade while comparing the different created clusters. By utilizing both a hierarchical- and density-based clustering methods, we can attempt to uncover similarity amongst players using methods with differing modeling characteristics.

After predicting cluster assignments for each player in a filtered dataset, we plot each player statistic feature across clusters for both KMeans and DBSCAN.

![Screenshot](https://github.com/jenningst/nba-trade-analysis/blob/main/images/barplot-cluster-distribution.png)

What we immediately see in both plots above is that both algorithms objectively group players into distinct clusters, assuming we consider the outliers from DBSCAN as its own cluster. What these plots do not explain is the distributions within clusters for both algorithms. We can analyze the clusters further with bar charts shown below.

![Screenshot](https://github.com/jenningst/nba-trade-analysis/blob/main/images/boxplot-min-played.png)

From the bar charts, we see that DBSCAN is clustering almost all players into a single cluster. Upon further inspection, we found that there were only a couple of players in each of the clusters 0 and 2 and the –1 outlier group. What this indicated to us was that DBSCAN does not work well on this dataset and, further, that it doesn’t capture the inherent variance in the dataset. From this we would conclude that the KMeans algorithm is suitable for comparing player similarity in the NBA based on individual player in-game statistics, whereas DBSCAN is not. Using the KMeans model, we could then make an evaluation of a trade by comparing the mean statistics of the cluster to which the trade player belongs and to which the proposed player belongs. From this, if the proposed player is in the same cluster as the trade player or a cluster with higher mean statistics, then the trade would be considered “fair” or even in your best interest. Conversely, if the proposed player is in a cluster with lower mean statistics, then the trade would be considered “not worth it”.

## Future Work
- Allow for trade analysis across position types
- Rolling cluster assignments as more games are played
- Indication of trade fariness

## Project Members

- Carl Ausmees
- Troy Jennings (https://github.com/jenningst)
