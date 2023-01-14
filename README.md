# Credit-Risk-Model
Data mining project using RapidMiner

The project uses a decision tree model to predict the credit rating of customers (Bad or Good) based on various attributes to help bank managers decide about loan applicants. The data was analyzed using historical information on customers who have taken out loans from a bank, including whether or not they repaid the loans or defaulted. 

## Part 1: Business Understanding (Problem):
Problem: We are trying to minimize the number of false negatives because higher false negatives will lead to higher risk.  

Description: The bank maintains a historical database of information on customers who have taken out loans from the bank. It is the bank’s job to predict the likelihood that loan applicants will default on their loans. A good credit rating means that the loan applicant will not default. A bad credit rating means that the loan applicant will default. 

Risk: We want to predict “default” or a bad credit rating because if the bank can minimize this risk, they will improve the chances of having less false predictions. 

## Part 2: Data Understanding

The dataset includes information on 2,464 credit ratings. There are 6 variables in the dataset. Age is the only continuous variable in this dataset with a range from about 20 to just over 63 and an average of 33.8 (SD = 8.539). Table 1 shows the binomial statistics for credit rating. Tables 2-5 show the descriptive statistics for various polynomial variables. The highest number of customers have a medium income and the lowest number of customers have a low income (Table - 2). 32% of customers have less than 5 credit cards, while the rest have 5 or more credit cards  (Table - 3). Half of the customers have a high school degree while the other half also has a college degree (Table - 4). 36% of customers have one or no car loans, while 64% of customers have more than 2 (Table - 5).



## Part 3: Decision Tree Model

There are 15 nodes in the decision tree model. There are 9 terminal nodes, the maximum depth is 3, and the target variables are Good and Bad. The features, in the order of significance, where the sample split are: “Less than 5” and “5 or more”; “Low”, “Medium”, and “High”; “None or 1” and “More than 2”; “≤ 34.290” and “≥34.290”; “≤ 41.124” and “≥41.124”.

## Part 4: Recommendations

We are trying to minimize False Negatives because a higher false negative will lead to higher business risk. In minimizing FN, the customers will be less likely to be falsely predicted as “not default.” The positive class here is “default” or bad credit rating because we want to predict it, and by the bank minimizing this risk, they are improving the chances of having less loans being defaulted. To do this, the bank can increase the requirements to take out a loan by increasing the precision of the predictive model. This will decrease FN but may also increase FP. This will also lead to a smaller amount of loans that are accepted. The bank will face a small amount of revenue loss as part of misclassification cost, but the business risk will be minimized.
Suggestions to improve the models based hyperparameters:

●	We can use a maximum depth of 10 to achieve better accuracy but if we change it to 3 the data becomes really hard to predict accurately as we would have only two variables to decide from, in this case, it is credit cards and income. 
●	The appropriate minimal size for leaf would be 50 but if we change it to 5 the data becomes more accurate but also more prone to overfitting. And the minimal size for the split would be 100 but if we change it to 10 the data tends to have a similar effect of becoming more accurate as well as more prone to overfitting.

