# Stochastic-Inventory-Modelling
Modeling the uncertainty in building round-the-clock product availability of short-shelf life products while minimizing disposals.

Imagine you own a grocery store and you had to stock up on bread. Every day you have the option to send out an order by the afternoon to the vendor to replenish the stock the next day. Assume a shelf life of 2 days.

3 major sources of uncertainty -

Demand today(d_0) - This will allow us to predict the opening stock of the next day.
Demand tomorrow(d_1) - This would determine the demand for tomorrow, and the number of excess units for the next day or lost opportunity of sales.
Demand day after(d_2) - To help us understand how many of the excess units we will be able to sell out. If demand for the next day is less than the number of excess units, it gets disposed of.
On some preliminary data analysis, you are able to fit your sales onto a normal distribution with a mean of 60 units and a standard deviation of 14 units.

Therefore, this is how the problem would look on simplification.

Objective Function - Minimize (Lost Opportunity+Disposal)
Uncertainty Model - d_0,d_1,d_2 ~ N(mu = 60,sd = 14)
Decision Variable - Assuming we start at a source of certainty of opening stock today of 70 units, how many units would you order for tomorrow?
Few Simplifications -

Let us assume the only values d_0,d_1,d_2 can take are - 10,20,30,40,50,60,70,80,90,100,110,120 (12 Cases in Total)
d_0,d_1,d_2 are independant of each other
The replenishment is always done at the beginning the demand cycle.
In the code below I aim to do the following - Given 12 cases of sales we would have 12 x 12 x 12 = 1728 possibilities

( Example -

Case 1 - d_0 = 10 units, d_1 = 20 units and d_2 = 110 units Output_1 - disposal_1 = n1, loss_1 = m1
Case 2 - d_0 = 100 units, d_1 = 80 units and d_2 = 60 units Output_2 - disposal_2 = n2, loss_2 = m2
......
Case 1728 - d_0 = 90 units, d_1 = 10 units and d_2 = 80 units Output_1728 - disposal_1728 = n_1728, loss_1728 = m_1728)
In each of the above cases we would observe n units of disposals, and m units of lost sales due to out of stock. These cases could happen with a certain probability.

Expected_Outcome(opening_stock_today , final_order)
= Prob(Outcome_1)*Outcome_1 + Prob(Outcome_2)*Outcome_2 +.......+ Prob(Outcome_1728)*Outcome_1728

Therefore, our expected_outcome is a function of opening_stock_today and final order. Given opening_stock_today, we will choose that final order that will optimise expected_outcome¶

# Model Validation 
![image](https://github.com/adelsakkir/Stochastic-Inventory-Modelling/assets/63802234/e12ed854-c789-4493-8edf-3f0a87a6e50b)

# Simulating Several Scenarios
![image](https://github.com/adelsakkir/Stochastic-Inventory-Modelling/assets/63802234/cfc1a76f-1ba0-4b07-8d03-f6a3401c6e9c)

# Optimal Order Quantity
![image](https://github.com/adelsakkir/Stochastic-Inventory-Modelling/assets/63802234/3bb6af79-fe2b-4a5e-bf15-b97c2cb1a1e4)


