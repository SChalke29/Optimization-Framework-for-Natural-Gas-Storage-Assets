## Optimization Framework for Natural Gas Storage Assets

## Motivation

- Natural gas accounts for 1/4th of the global energy demand and it is also one of the major trading commodities in the market. 
- Natural gas storage facilities present opportunities for companies to take advantage of fluctuating demand and prices by storing excess gas or supplementing extremely high demand. 
- This project present series of optimization models to support the decision making at the natural gas storage facilities.
- The user interface is designed to interact with the models for changing operations' parameters.

## Methodology
 <img src="https://user-images.githubusercontent.com/56485357/147991962-772e70aa-24fd-4c34-badf-8c8414726e12.png" width="900" height="350" />

## Exploratoary Data Analysis and Preparation

Simulated natural gas price predictions were analysed using discriptive statistics as below.
<p float="left">
  <img src="https://user-images.githubusercontent.com/56485357/147994484-b7f1cfd9-7c07-4505-a539-c5c4697a0f72.png" width="420" height="300" />
  <img src="https://user-images.githubusercontent.com/56485357/147994488-8ec99296-f4ab-4afb-b485-eb2169d729c0.png" width="420" height="300" /> 
</p>


- High price variations and high average prices were observed during the winter season. 
- The above observation perefectly correlates with the extremely high demand during the winter season and therefore the high prices and price fluctuations. 

Over 900 price scenarios were clustred using **"machine learning algorithm (K-Means Clustering)"** and optimum numbers of clusters (price scenarios) were derived using **"Elbow Method"** 

<img src="https://user-images.githubusercontent.com/56485357/147995280-41076e34-ec5b-47de-bfb4-0baa48ccaffb.png" width="910"/> 

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

- The key assumption of linear programming models is that the parameter values are assumed to be a known constant, such is not the case in our application where seasonality plays a very important role and hence high flucuations in natural gas prices. This modeling approach tries to produce the most favourable solution out of all.
- Robust optimization model is designed for dealing the high level of uncertainities and therefore produces the most conservative solution. 
- Minimizing the maximum regret model however tries to balance the extreme results produced by linear programming and robust optimization. It tries to optimize the maximum regret of going towards the best solution and therefore stays in between the both.
- Dynamic programming model produces satisfactory result, however two major drawbacks were observed while testing the model. Firstly the computation time taken to yeid the result was ~5 hours compare to few seconds for other models and secondly, it only accepts the discreet set of data for analysis which limits the optimization capability when we have continuous values of natural gas storage quantity.

## Recommendation

All the models performed well under givin parameters and the results as discussed above highlights the benefits of selecting one model over the other. There is no straight answer to which model to choose given the fact that every model has its own limitation to perform under different conditions and it solely depends on the risk apetite of a decision maker. If they believe that there will not be as much price variation then the linear programming approach can be recommended. if they want to go with the safe option (risk-aversing), then robust optimizartion would be the perfect choice. However, if they are ready to take some calculative risks, then there is an option of selecting the min-max regret model which makes the perfect tradeoff between the best and worst case scenarios.


## GUI Demo

User interface was designed to enable the decision maker to change the input parameters and compare the resuts of different modeling output. Python's TKinter module was used to design the interface. The video demonstration of GUI tool is provided below for reference purpose only.

https://user-images.githubusercontent.com/56485357/147926314-a89de21e-9245-4871-85c6-59c903d0f867.mp4


## Pictures of research seminar presented to the graduate students and faculty members of Dalhousie University in Halifax, Nova Scotia.
<p float="left">
  <img src="https://user-images.githubusercontent.com/56485357/147918397-cc6e13d7-79d4-4f2b-946f-47dee580bd52.png" width="400" height="400" hspace="20" />
  <img src="https://user-images.githubusercontent.com/56485357/147918469-e64c6511-17b6-409b-a21f-4cdcde0b3ca3.png" width="400" height="400" /> 
</p>



