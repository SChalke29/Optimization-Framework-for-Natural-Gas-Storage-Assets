## Optimization Framework for Natural Gas Storage Assets

## Motivation

- Natural gas accounts for 1/4th of the global energy demand and it is also one of the major trading commodities in the market
- Natural gas storage facilities present opportunities for companies to take advantage of fluctuating prices due to their highly seasonal demand profile. It can be achieved through the buy low, sell high strategy (storing excess gas when it is cheap and supplementing during the extremely high demand) 
- This project presents a series of optimization models to support the decision-making at the natural gas storage facilities
- The user interface is designed to interact with the models for changing operations parameters

## Methodology
 <img src="https://user-images.githubusercontent.com/56485357/147991962-772e70aa-24fd-4c34-badf-8c8414726e12.png" width="900" height="350" />

## Exploratoary Data Analysis and Preparation

Simulated natural gas price predictions were analyzed using descriptive statistics as below.

<img src="https://user-images.githubusercontent.com/56485357/148002314-25e05ab1-7b81-4ffa-81ec-6b6fb42c6c04.png" width="900"/> 

- High price variations and high average prices were observed during the winter season 
- The above observation perfectly correlates with the extremely high demand during the winter season and therefore the high prices and price fluctuations

Over 900 price scenarios were clustered using **"machine learning algorithm (K-Means Clustering)"** and optimum numbers of clusters (price scenarios) were derived using the **"Elbow Method"** 

<img src="https://user-images.githubusercontent.com/56485357/147995280-41076e34-ec5b-47de-bfb4-0baa48ccaffb.png" width="900"/> 

- Within cluster variation starts to get plateaued after 9 clusters. Therefore, K=9 is selected as an optimum number of price scenarios for analysis.

## Modeling

Series of optimization models were tested and compared to get the maximum expected profit and optimum natural gas storage decisions (amount of natural gas to be injected and/or withdrawn by month) for 12 months time horizon.

- **Linear Programming** with average monthly price
- **Stochastic Linear Programming** with K=9 price scenarios
- **Stochastic Linear Programming** with probabilistic constraint (chance constraint)
- **Robust Optimization**
- **Minimizing the Maximum Regret Model**
- **Deterministic Dynamic Programming**

## Results

![image](https://user-images.githubusercontent.com/56485357/147997354-bfcce7d0-8d94-48af-9813-7b58ee96f7fa.png)

- The key assumption of linear programming models is that the parameter values are assumed to be a known constant, such is not the case in our application where seasonality plays a very important role and hence high fluctuations in natural gas prices. This modeling approach tries to produce the most favorable solution out of all.
- The Robust optimization model is designed for dealing with a high level of price uncertainties and therefore produces the most conservative solution. 
- Minimizing the maximum regret model, however, tries to balance the extreme results produced by linear programming and robust optimization. It tries to optimize the maximum regret of going towards the best solution and therefore stays in between the both.
- Dynamic programming model produces a satisfactory result, however, two major drawbacks were observed while testing the model. Firstly the computation time was taken to yield the result was ~5 hours compared to a few seconds for other models and secondly, it only accepts the discreet set of data for analysis which limits the optimization capability when we have continuous values of natural gas storage quantity.

## Recommendation

All the models performed well under the given parameters and the results as discussed above highlights the benefits of selecting one model over the other. There is no straight answer to which model to choose given the fact that every model has its limitation to perform under different conditions and it solely depends on the risk appetite of a decision-maker. If they believe that there will not be as much price variation then the linear programming approach can be recommended. if they want to go with the safe option, then risk-aversing robust optimization would be a perfect choice. However, if they are ready to take some calculative risks, then there is an option of selecting the min-max regret model which makes the perfect tradeoff between the best and worst-case scenarios.


## GUI Demo

The user interface was designed to enable the decision-maker to change the input parameters and compare the results of different modeling outputs. Python's TKinter module was used to design the interface. The video demonstration of the GUI tool is provided below for reference purposes only.

https://user-images.githubusercontent.com/56485357/147926314-a89de21e-9245-4871-85c6-59c903d0f867.mp4


## Pictures of research seminar presented to the graduate students and faculty members of Dalhousie University in Halifax, Nova Scotia.

<img src="https://user-images.githubusercontent.com/56485357/148002612-5e1bf14f-0cf5-41b0-86ab-fd0cd17bf137.png" width="900"/> 

