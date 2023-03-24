# Prediction and Analysis of the League of Legends Professional Game

**Name(s)**: Runze Wang, Xuecheng Xu

#### Import Data

<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>gameid</th>
      <th>datacompleteness</th>
      <th>url</th>
      <th>league</th>
      <th>year</th>
      <th>split</th>
      <th>playoffs</th>
      <th>date</th>
      <th>game</th>
      <th>patch</th>
      <th>...</th>
      <th>opp_csat15</th>
      <th>golddiffat15</th>
      <th>xpdiffat15</th>
      <th>csdiffat15</th>
      <th>killsat15</th>
      <th>assistsat15</th>
      <th>deathsat15</th>
      <th>opp_killsat15</th>
      <th>opp_assistsat15</th>
      <th>opp_deathsat15</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>ESPORTSTMNT01_2690210</td>
      <td>complete</td>
      <td>NaN</td>
      <td>LCK CL</td>
      <td>2022</td>
      <td>Spring</td>
      <td>0</td>
      <td>2022-01-10 07:44:08</td>
      <td>1</td>
      <td>12.01</td>
      <td>...</td>
      <td>121.0</td>
      <td>391.0</td>
      <td>345.0</td>
      <td>14.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>ESPORTSTMNT01_2690210</td>
      <td>complete</td>
      <td>NaN</td>
      <td>LCK CL</td>
      <td>2022</td>
      <td>Spring</td>
      <td>0</td>
      <td>2022-01-10 07:44:08</td>
      <td>1</td>
      <td>12.01</td>
      <td>...</td>
      <td>100.0</td>
      <td>541.0</td>
      <td>-275.0</td>
      <td>-11.0</td>
      <td>2.0</td>
      <td>3.0</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>5.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>ESPORTSTMNT01_2690210</td>
      <td>complete</td>
      <td>NaN</td>
      <td>LCK CL</td>
      <td>2022</td>
      <td>Spring</td>
      <td>0</td>
      <td>2022-01-10 07:44:08</td>
      <td>1</td>
      <td>12.01</td>
      <td>...</td>
      <td>119.0</td>
      <td>-475.0</td>
      <td>153.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>3.0</td>
      <td>0.0</td>
      <td>3.0</td>
      <td>3.0</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>ESPORTSTMNT01_2690210</td>
      <td>complete</td>
      <td>NaN</td>
      <td>LCK CL</td>
      <td>2022</td>
      <td>Spring</td>
      <td>0</td>
      <td>2022-01-10 07:44:08</td>
      <td>1</td>
      <td>12.01</td>
      <td>...</td>
      <td>149.0</td>
      <td>-793.0</td>
      <td>-1343.0</td>
      <td>-34.0</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>3.0</td>
      <td>3.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>ESPORTSTMNT01_2690210</td>
      <td>complete</td>
      <td>NaN</td>
      <td>LCK CL</td>
      <td>2022</td>
      <td>Spring</td>
      <td>0</td>
      <td>2022-01-10 07:44:08</td>
      <td>1</td>
      <td>12.01</td>
      <td>...</td>
      <td>21.0</td>
      <td>443.0</td>
      <td>-497.0</td>
      <td>7.0</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>6.0</td>
      <td>2.0</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 123 columns</p>
</div>



### Framing the Problem

#### Goal of Prediction Model (Prediction Problem):

Predict whether a team will win in the end based on the data performance of a certain team in the early stages of the game in 2022 professional League of legend competition.

#### Explanation:

LoL (League of legend) is a multiplayer online arena (MOBA) video game with 27 million players per day. In LoL, a standard game consists of two opposing teams consisting of five players. Each "summoner" (player) controls a "champion" (character) with unique abilities. The goal is to destroy a structure of the opposing team, It is located in the center of a base protected by a defensive structure called a "turret.". Each match is discrete and the champion is initially quite weak, but through accumulating projects and experience on the court, his strength continues to strengthen as a part of the game.

In a competition, a champion can be killed by other champions and then resurrected. The murderer will receive a homicide score. If the other champion deals damage to the victim before the champion kills the victim, they will receive an auxiliary score. This lethal scoring system is very similar to real games such as basketball. However, the significant difference between LoL and basketball is that even if a team lags far behind in the early stages, it can still win as long as it destroys the crystal. That is to say, the advantage in the early stage does not represent the final victory. Therefore, the purpose of this experiment is to predict whether the team will win the competition in the end based on the data performance of the previous team.


#### Data Cleanning:

Before data analysis, we need to clean up the data to reduce the possibility of model problems, which is the "garbage in garbage out" mentioned in the prediction model. Our data contains a column called **datacompleteness**, which provides us with information on whether the data is complete. In order to obtain a more convinced and accurate prediction model, we filter out incomplete data:



<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>gameid</th>
      <th>datacompleteness</th>
      <th>url</th>
      <th>league</th>
      <th>year</th>
      <th>split</th>
      <th>playoffs</th>
      <th>date</th>
      <th>game</th>
      <th>patch</th>
      <th>...</th>
      <th>opp_csat15</th>
      <th>golddiffat15</th>
      <th>xpdiffat15</th>
      <th>csdiffat15</th>
      <th>killsat15</th>
      <th>assistsat15</th>
      <th>deathsat15</th>
      <th>opp_killsat15</th>
      <th>opp_assistsat15</th>
      <th>opp_deathsat15</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>ESPORTSTMNT01_2690210</td>
      <td>complete</td>
      <td>NaN</td>
      <td>LCK CL</td>
      <td>2022</td>
      <td>Spring</td>
      <td>0</td>
      <td>2022-01-10 07:44:08</td>
      <td>1</td>
      <td>12.01</td>
      <td>...</td>
      <td>121.0</td>
      <td>391.0</td>
      <td>345.0</td>
      <td>14.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>ESPORTSTMNT01_2690210</td>
      <td>complete</td>
      <td>NaN</td>
      <td>LCK CL</td>
      <td>2022</td>
      <td>Spring</td>
      <td>0</td>
      <td>2022-01-10 07:44:08</td>
      <td>1</td>
      <td>12.01</td>
      <td>...</td>
      <td>100.0</td>
      <td>541.0</td>
      <td>-275.0</td>
      <td>-11.0</td>
      <td>2.0</td>
      <td>3.0</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>5.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>ESPORTSTMNT01_2690210</td>
      <td>complete</td>
      <td>NaN</td>
      <td>LCK CL</td>
      <td>2022</td>
      <td>Spring</td>
      <td>0</td>
      <td>2022-01-10 07:44:08</td>
      <td>1</td>
      <td>12.01</td>
      <td>...</td>
      <td>119.0</td>
      <td>-475.0</td>
      <td>153.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>3.0</td>
      <td>0.0</td>
      <td>3.0</td>
      <td>3.0</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>ESPORTSTMNT01_2690210</td>
      <td>complete</td>
      <td>NaN</td>
      <td>LCK CL</td>
      <td>2022</td>
      <td>Spring</td>
      <td>0</td>
      <td>2022-01-10 07:44:08</td>
      <td>1</td>
      <td>12.01</td>
      <td>...</td>
      <td>149.0</td>
      <td>-793.0</td>
      <td>-1343.0</td>
      <td>-34.0</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>3.0</td>
      <td>3.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>ESPORTSTMNT01_2690210</td>
      <td>complete</td>
      <td>NaN</td>
      <td>LCK CL</td>
      <td>2022</td>
      <td>Spring</td>
      <td>0</td>
      <td>2022-01-10 07:44:08</td>
      <td>1</td>
      <td>12.01</td>
      <td>...</td>
      <td>21.0</td>
      <td>443.0</td>
      <td>-497.0</td>
      <td>7.0</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>6.0</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>ESPORTSTMNT01_2690210</td>
      <td>complete</td>
      <td>NaN</td>
      <td>LCK CL</td>
      <td>2022</td>
      <td>Spring</td>
      <td>0</td>
      <td>2022-01-10 07:44:08</td>
      <td>1</td>
      <td>12.01</td>
      <td>...</td>
      <td>135.0</td>
      <td>-391.0</td>
      <td>-345.0</td>
      <td>-14.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>ESPORTSTMNT01_2690210</td>
      <td>complete</td>
      <td>NaN</td>
      <td>LCK CL</td>
      <td>2022</td>
      <td>Spring</td>
      <td>0</td>
      <td>2022-01-10 07:44:08</td>
      <td>1</td>
      <td>12.01</td>
      <td>...</td>
      <td>89.0</td>
      <td>-541.0</td>
      <td>275.0</td>
      <td>11.0</td>
      <td>0.0</td>
      <td>5.0</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>3.0</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>ESPORTSTMNT01_2690210</td>
      <td>complete</td>
      <td>NaN</td>
      <td>LCK CL</td>
      <td>2022</td>
      <td>Spring</td>
      <td>0</td>
      <td>2022-01-10 07:44:08</td>
      <td>1</td>
      <td>12.01</td>
      <td>...</td>
      <td>120.0</td>
      <td>475.0</td>
      <td>-153.0</td>
      <td>-1.0</td>
      <td>3.0</td>
      <td>3.0</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>3.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>ESPORTSTMNT01_2690210</td>
      <td>complete</td>
      <td>NaN</td>
      <td>LCK CL</td>
      <td>2022</td>
      <td>Spring</td>
      <td>0</td>
      <td>2022-01-10 07:44:08</td>
      <td>1</td>
      <td>12.01</td>
      <td>...</td>
      <td>115.0</td>
      <td>793.0</td>
      <td>1343.0</td>
      <td>34.0</td>
      <td>3.0</td>
      <td>3.0</td>
      <td>0.0</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>9</th>
      <td>ESPORTSTMNT01_2690210</td>
      <td>complete</td>
      <td>NaN</td>
      <td>LCK CL</td>
      <td>2022</td>
      <td>Spring</td>
      <td>0</td>
      <td>2022-01-10 07:44:08</td>
      <td>1</td>
      <td>12.01</td>
      <td>...</td>
      <td>28.0</td>
      <td>-443.0</td>
      <td>497.0</td>
      <td>-7.0</td>
      <td>0.0</td>
      <td>6.0</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>10</th>
      <td>ESPORTSTMNT01_2690210</td>
      <td>complete</td>
      <td>NaN</td>
      <td>LCK CL</td>
      <td>2022</td>
      <td>Spring</td>
      <td>0</td>
      <td>2022-01-10 07:44:08</td>
      <td>1</td>
      <td>12.01</td>
      <td>...</td>
      <td>510.0</td>
      <td>107.0</td>
      <td>-1617.0</td>
      <td>-23.0</td>
      <td>5.0</td>
      <td>10.0</td>
      <td>6.0</td>
      <td>6.0</td>
      <td>18.0</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>11</th>
      <td>ESPORTSTMNT01_2690210</td>
      <td>complete</td>
      <td>NaN</td>
      <td>LCK CL</td>
      <td>2022</td>
      <td>Spring</td>
      <td>0</td>
      <td>2022-01-10 07:44:08</td>
      <td>1</td>
      <td>12.01</td>
      <td>...</td>
      <td>487.0</td>
      <td>-107.0</td>
      <td>1617.0</td>
      <td>23.0</td>
      <td>6.0</td>
      <td>18.0</td>
      <td>5.0</td>
      <td>5.0</td>
      <td>10.0</td>
      <td>6.0</td>
    </tr>
    <tr>
      <th>12</th>
      <td>ESPORTSTMNT01_2690219</td>
      <td>complete</td>
      <td>NaN</td>
      <td>LCK CL</td>
      <td>2022</td>
      <td>Spring</td>
      <td>0</td>
      <td>2022-01-10 08:38:24</td>
      <td>1</td>
      <td>12.01</td>
      <td>...</td>
      <td>140.0</td>
      <td>-1484.0</td>
      <td>-652.0</td>
      <td>-30.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>1.0</td>
    </tr>
  </tbody>
</table>
<p>13 rows × 123 columns</p>
</div>



The data of a game contained in the data we use occupies 12 rows, which means that every 12 rows represent the data of a game. Among them, the data of each game, 12 rows, including the personal data of 10 players and the data of 2 teams. The data of the team is the accumulation of the data of the players in each team. You can observe this from the dataframe above.(The dataframe above showcase the first 13 rows in the data frame. The 13th row are the game data in the another game.) All the data are sorted according to certain rules: the bottom two rows of every 12 rows are the overall data of the two teams; the first 10 rows are the data of the 10 players of the two teams. 

You can see that the **position** column contains 6 variables in different positions.They are: **top**, **jng**, **mid**, **bot**, **sup**, and **team**. Among them, **team** represents the overall data of a team in a game.

Our goal is to be able to describe whether the team can win through the performance of a team in the early game. Therefore, our target observation is the aggregate data for each team. We will choose the row whose position is **team** for the upcoming analysis:


<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>gameid</th>
      <th>datacompleteness</th>
      <th>url</th>
      <th>league</th>
      <th>year</th>
      <th>split</th>
      <th>playoffs</th>
      <th>date</th>
      <th>game</th>
      <th>patch</th>
      <th>...</th>
      <th>opp_csat15</th>
      <th>golddiffat15</th>
      <th>xpdiffat15</th>
      <th>csdiffat15</th>
      <th>killsat15</th>
      <th>assistsat15</th>
      <th>deathsat15</th>
      <th>opp_killsat15</th>
      <th>opp_assistsat15</th>
      <th>opp_deathsat15</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>10</th>
      <td>ESPORTSTMNT01_2690210</td>
      <td>complete</td>
      <td>NaN</td>
      <td>LCK CL</td>
      <td>2022</td>
      <td>Spring</td>
      <td>0</td>
      <td>2022-01-10 07:44:08</td>
      <td>1</td>
      <td>12.01</td>
      <td>...</td>
      <td>510.0</td>
      <td>107.0</td>
      <td>-1617.0</td>
      <td>-23.0</td>
      <td>5.0</td>
      <td>10.0</td>
      <td>6.0</td>
      <td>6.0</td>
      <td>18.0</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>11</th>
      <td>ESPORTSTMNT01_2690210</td>
      <td>complete</td>
      <td>NaN</td>
      <td>LCK CL</td>
      <td>2022</td>
      <td>Spring</td>
      <td>0</td>
      <td>2022-01-10 07:44:08</td>
      <td>1</td>
      <td>12.01</td>
      <td>...</td>
      <td>487.0</td>
      <td>-107.0</td>
      <td>1617.0</td>
      <td>23.0</td>
      <td>6.0</td>
      <td>18.0</td>
      <td>5.0</td>
      <td>5.0</td>
      <td>10.0</td>
      <td>6.0</td>
    </tr>
    <tr>
      <th>22</th>
      <td>ESPORTSTMNT01_2690219</td>
      <td>complete</td>
      <td>NaN</td>
      <td>LCK CL</td>
      <td>2022</td>
      <td>Spring</td>
      <td>0</td>
      <td>2022-01-10 08:38:24</td>
      <td>1</td>
      <td>12.01</td>
      <td>...</td>
      <td>555.0</td>
      <td>-1763.0</td>
      <td>-906.0</td>
      <td>-22.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>3.0</td>
      <td>3.0</td>
      <td>3.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>23</th>
      <td>ESPORTSTMNT01_2690219</td>
      <td>complete</td>
      <td>NaN</td>
      <td>LCK CL</td>
      <td>2022</td>
      <td>Spring</td>
      <td>0</td>
      <td>2022-01-10 08:38:24</td>
      <td>1</td>
      <td>12.01</td>
      <td>...</td>
      <td>533.0</td>
      <td>1763.0</td>
      <td>906.0</td>
      <td>22.0</td>
      <td>3.0</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>46</th>
      <td>ESPORTSTMNT01_2690227</td>
      <td>complete</td>
      <td>NaN</td>
      <td>LCK CL</td>
      <td>2022</td>
      <td>Spring</td>
      <td>0</td>
      <td>2022-01-10 09:51:16</td>
      <td>1</td>
      <td>12.01</td>
      <td>...</td>
      <td>545.0</td>
      <td>1191.0</td>
      <td>2298.0</td>
      <td>15.0</td>
      <td>3.0</td>
      <td>8.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>149111</th>
      <td>ESPORTSTMNT01_3268686</td>
      <td>complete</td>
      <td>NaN</td>
      <td>NEXO</td>
      <td>2023</td>
      <td>Split 1</td>
      <td>0</td>
      <td>2022-12-21 17:16:50</td>
      <td>2</td>
      <td>12.23</td>
      <td>...</td>
      <td>459.0</td>
      <td>-853.0</td>
      <td>2092.0</td>
      <td>-33.0</td>
      <td>6.0</td>
      <td>12.0</td>
      <td>4.0</td>
      <td>4.0</td>
      <td>5.0</td>
      <td>6.0</td>
    </tr>
    <tr>
      <th>149122</th>
      <td>ESPORTSTMNT01_3269631</td>
      <td>complete</td>
      <td>NaN</td>
      <td>NEXO</td>
      <td>2023</td>
      <td>Split 1</td>
      <td>0</td>
      <td>2022-12-21 18:21:45</td>
      <td>3</td>
      <td>12.23</td>
      <td>...</td>
      <td>466.0</td>
      <td>2063.0</td>
      <td>-1049.0</td>
      <td>-28.0</td>
      <td>8.0</td>
      <td>11.0</td>
      <td>5.0</td>
      <td>5.0</td>
      <td>5.0</td>
      <td>8.0</td>
    </tr>
    <tr>
      <th>149123</th>
      <td>ESPORTSTMNT01_3269631</td>
      <td>complete</td>
      <td>NaN</td>
      <td>NEXO</td>
      <td>2023</td>
      <td>Split 1</td>
      <td>0</td>
      <td>2022-12-21 18:21:45</td>
      <td>3</td>
      <td>12.23</td>
      <td>...</td>
      <td>438.0</td>
      <td>-2063.0</td>
      <td>1049.0</td>
      <td>28.0</td>
      <td>5.0</td>
      <td>5.0</td>
      <td>8.0</td>
      <td>8.0</td>
      <td>11.0</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>149134</th>
      <td>ESPORTSTMNT01_3268705</td>
      <td>complete</td>
      <td>NaN</td>
      <td>NEXO</td>
      <td>2023</td>
      <td>Split 1</td>
      <td>0</td>
      <td>2022-12-21 19:22:53</td>
      <td>4</td>
      <td>12.23</td>
      <td>...</td>
      <td>439.0</td>
      <td>2213.0</td>
      <td>516.0</td>
      <td>18.0</td>
      <td>6.0</td>
      <td>7.0</td>
      <td>5.0</td>
      <td>5.0</td>
      <td>10.0</td>
      <td>6.0</td>
    </tr>
    <tr>
      <th>149135</th>
      <td>ESPORTSTMNT01_3268705</td>
      <td>complete</td>
      <td>NaN</td>
      <td>NEXO</td>
      <td>2023</td>
      <td>Split 1</td>
      <td>0</td>
      <td>2022-12-21 19:22:53</td>
      <td>4</td>
      <td>12.23</td>
      <td>...</td>
      <td>457.0</td>
      <td>-2213.0</td>
      <td>-516.0</td>
      <td>-18.0</td>
      <td>5.0</td>
      <td>10.0</td>
      <td>6.0</td>
      <td>6.0</td>
      <td>7.0</td>
      <td>5.0</td>
    </tr>
  </tbody>
</table>
<p>21174 rows × 123 columns</p>
</div>


In the game League of Legends, teams can choose to surrender at 15 minutes, when a team believes that they are really far behind the opponent. Therefore, we chose to use the first 15 minutes of game data as a variable for a team's early game performance. In the game, different sides (red side and blue side) will be in different game terrains. The difference between the terrain of the red side and the blue side is often considered to be one of the factors that affect a team's decision-making, which may also become a variable that affects whether to win or not. Additionally, first blood and destroying the first tower in the game both grant bonus gold, which gives a team a bigger early-game advantage. Likewise, first dragon and first baron in the game show that the team has more leads than the enemy in the early game The following columns are included in the dataframe about the game data of the first 15 minutes and the early game performance:

**firstblood**: whether a team get the first blood in the game.\
**firstdragon**: whether a team get the first dragon in the game.\
**firsttower**: whether a team get the first tower in the game.\
**firstbaron**: whether a team get the first baron in the game.\
**result**: whether a team win the game.\
(The above columns all use 0 or 1 to represent True or False.)

**side**: the side that a team are in a game. (Blue side/Red side)\

**golddiffat15**: The difference between the sum of team gold and the enemy at 15 minutes (can be positive or negative).\
**csdiffat15**: Average creep score difference at 15 minutes (can be positive or negative).\
**xpdiffat15**: Average experience difference at 15 minutes (can be positive or negative).

<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>side</th>
      <th>firstblood</th>
      <th>firstdragon</th>
      <th>firsttower</th>
      <th>firstbaron</th>
      <th>result</th>
      <th>golddiffat15</th>
      <th>csdiffat15</th>
      <th>xpdiffat15</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>10</th>
      <td>Blue</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0</td>
      <td>107.0</td>
      <td>-23.0</td>
      <td>-1617.0</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Red</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1</td>
      <td>-107.0</td>
      <td>23.0</td>
      <td>1617.0</td>
    </tr>
    <tr>
      <th>22</th>
      <td>Blue</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0</td>
      <td>-1763.0</td>
      <td>-22.0</td>
      <td>-906.0</td>
    </tr>
    <tr>
      <th>23</th>
      <td>Red</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>1</td>
      <td>1763.0</td>
      <td>22.0</td>
      <td>906.0</td>
    </tr>
    <tr>
      <th>46</th>
      <td>Blue</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>1</td>
      <td>1191.0</td>
      <td>15.0</td>
      <td>2298.0</td>
    </tr>
  </tbody>
</table>
</div>

### Prediction Type:

Our purpose is to predict whether a team will win in the end based on the data performance of a certain team in the early stages of the game. While the parameters that can represent the early stages of the game include not only numerical data, but also categorical data. Therefore, in order to obtain a better prediction model, we choose to include both in our scope, that is to say, our prediction type is both classification and regression.

The model may most useful to our dataset are decision trees and forest. The datatype in the dataframe above shows that the the data in first 6 columns are typically used as labels for binary classification; while the data in the last 3 columns are used as regression.

The dataframe contains a column called **result**, which indicates whether a team win or loss a game. The 0 in the row represent loss, while the 1 in the row represent win. The **result** is the response variable in our model. It shows the game result, win or lose, directly by 1 and 0, which is the variable we try to predict and explain. 

About the metric to evaluate the model, accuracy is particularly useful when the classes in the dataset are balanced, meaning that the number of instances in each class is roughly equal. In this case, accuracy can give a good indication of how well the model is performing across all classes. According to the dataframe above, most of the data in each columns are close to each other since the professional game in League of Legends are competitive, the gap between two teams are small, which provide a roughly equal game data. While F1 score is a commonly used metric to evaluate the performance of a binary classification model, and it combines precision and recall into a single value, which may not a good metric to evaluate the incoming model we may used. Moreover, precision is a useful metric to use in situations where the cost of a false positive. It is good to use when the data is inbalanced and cost of a false positive is high, which may not a good metric for our model.



#### Exploratory data analysis:


    

    



    

    



    

    



    

    



    

    



    

    



    

    



    

    



    

    


Let's see the Correlation coefficient distribution on the matrix:

    

    

From the correlation coefficient matrix, we can see the strength of the correlation between various variables. Generally, the stronger the correlation, the greater the contribution of variables to the prediction of target variables. We can find that the correlation between most variables is relatively weak. So we need to re integrate the data and construct the target variables and characteristic variables we need.

### Baseline Model

There are many models in machine learning, and different models have their own characteristics. They often play different roles for different data characteristics. Therefore, we have selected multiple commonly used machine learning models for testing, and selected the one with higher accuracy as the base model.

In this question, we have 8 features in the selected columns. 7 of them are quantitatives, and 1 of them is nominal(i.e Blue side or Red side). 

For the base model, I firstly use the one hot encoder model in order to deal with categorical input, that is Side in this case. As I mentioned above, there are many mmachine learning models and decided to perform the pipeline with different models and comparing for the best models. As the table shown below, among the 7 models, Random Forest Classifier performs the best in the pipeline I built. Therefore, for the baseline, we choose Random Forest Classifier.

To report the performance, all the accuracy score is shown below with different models, and we choose Random Forest Classifiers because it has the highest accuracy score (0.839131). We believe that it is a good base line model because the features we used has quantitative and categorical features,so one hot encoder is necessary. Furthermore, Random Forest Classifier has less sensitive to the outliers, like a crushing game. Random Forest Classifier gives the highest accuracy score. 


                             method  accuracy score
    0           Logistic Regression        0.835511
    1      Decision Tree Classifier        0.809696
    2                KNN Classifier        0.815520
    3      Random Forest Classifier        0.839131
    4                     LinearSVC        0.794585
    5           AdaBoost Classifier        0.834252
    6  Gradient Boosting Classifier        0.835039
    

According to the score summary above, although the **accuracy score** in each model are almost the same, we can see that the **Random Forest Classifier** shows a better predicted performance compare with rest of the Classifier. Therefore, we choose the **Random Forest Classifier** as our base model.

### Final Model

To optimize, we add two more scaler into the pipeline (MaxAbsScaler and Normalizer). We tried different scaler such as MinMaxScaler but the input is sparse so we choose MaxAbsScaler. MaxAbsScaler and Normalizer are good for our model because MaxAbsScaler scales the data while preserving the sign of the value. In our data, the quantitative values like gold difference has sign for prediction. Normalizer could scale the data so that each data has the same impact on the prediction we are making. Combining this two features, our random forest classifier could perform better.

Adjusting parameters can achieve better performance of the model. Here, we conduct parameter tuning for random forests that perform well in the base model test. We use gridsearchcv to perform, n_ Estimators and max_ Depth is two important parameters for random forests, which have a significant impact on performance. Here, the default parameter in base line is **n_estimators** = 200, **max_Depth** = 120, here we select a parameter range to adjust based on this range and find **max_depth** = 20, When **n_estimators**=250, the test accuracy of the model is the highest, indicating that the model has improved to a certain extent.

Although the final model has less accuracy score, the Random Forest Classifier is prone to overfit. The final model with the best hyperameter we chose has the optimal time and space complexity. We find a great balance between the accuracy and time and space complexity.



The adjusted process result is shown below:\
(The accuracy of the adjusted Random Forest is 0.8335467544201014)



    0.8335467544201014
    Pipeline(steps=[('transformer',
                     ColumnTransformer(remainder='passthrough',
                                       transformers=[('one hot',
                                                      OneHotEncoder(handle_unknown='ignore'),
                                                      ['side', 'firstblood',
                                                       'firstdragon', 'firsttower',
                                                       'firstbaron', 'golddiffat15',
                                                       'csdiffat15',
                                                       'xpdiffat15'])])),
                    ('MaxAbsScale', MaxAbsScaler()), ('Normalize', Normalizer()),
                    ('model',
                     RandomForestClassifier(max_depth=20, n_estimators=250,
                                            random_state=True))])
    

### Fairness Analysis

#### Additional model evaluation:

Using the final model to predict test set data, we can find that the prediction accuracy is approximately 84%

    0.8386589013064694
                  precision    recall  f1-score   support
    
               0       0.84      0.84      0.84      3177
               1       0.84      0.84      0.84      3176
    
        accuracy                           0.84      6353
       macro avg       0.84      0.84      0.84      6353
    weighted avg       0.84      0.84      0.84      6353
    
    

#### Permutation test for Fairness Analysis:

The discriminant variable (Group X and Group Y) we choose is the red side versus the blue side. We shuffle the sides to calculate the accuracy of the red side and the blue side under the Random Forest Classifier. By simulating the permutation multiple times and comparing the obtained empirical difference with the observed difference.

**Null Hypothesis**: The classifier's accuracy is the same for both blue side and red side, and any differences are due to chance.\
**Alternative Hypothesis**: The classifier's accuracy is higher for red side.\
**Test statistic**: Difference in accuracy (blue side accuracy minus red sude accuracy).\
**Significance**: α = 0.01

**observed accuracy difference** = -0.010684470979782312

**p_value** = 0.171

According to the p-value and distribution graph of the empirical difference of accuracy between blue side and red side above, the p-value is close to 0.2. Since the p-value is much higher than our significance level, α = 0.01,  we reject the null hypothesis, which state that the classifier's accuracy is the same for both blue side and red side, and any differences are due to chance. Hence, difference in accuracy between blue side and red side is significant, around 10% chance. Therefore, the Random Forest Classifier seems does not achieve accuracy parity perfectly.

#### Conclusion:

According to the additional model evaluation above and the accuracy of our , the prediction precision, recall, and f1-score is approximately 84%. And the accuracy of our adjusted Random Forest Classifier are able to provide a prediction with around 83.4% accuracy. As we state above, the independent variable we manipuate is the varible which represent the early stage performance of one team, and the response variable is the **result**, which indicate the result of game is win or loss. It shows that our Random Forest Classifier perform a relatively good prediction. In other words, the early stage performance of a team will have an effect on whether the team will win or loss the game at the end. The better performance a team does on the early stage of the game, the higher probability that one game could win the game at the end.

However, according to the Fairness Analysis, the model we used, adjusted Random Forest Classifier, are unable to provide a almost fair prediction when the observation are divided into 2 part according to the variable **side**. Hence, we can say that the model we generate seems unable to achieve accuracy parity.
