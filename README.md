# Credit-Risk-Model
Data mining project using RapidMiner

The project uses a decision tree model to predict the credit rating of customers (Bad or Good) based on various attributes to help bank managers decide about loan applicants. The data was analyzed using historical information on customers who have taken out loans from a bank, including whether or not they repaid the loans or defaulted. 

## Part 1: Business Understanding
Problem: Finding the best way to make decision about loan applications based on a data-driven model.

Description: The bank maintains a historical database of information on customers who have taken out loans from the bank. It is the bank’s job to predict the likelihood that loan applicants will default on their loans. A good credit rating means that the loan applicant will not default. A bad credit rating means that the loan applicant will default. 

Risk: We want to correctly predict “default” or a bad credit rating to  minimize the bank's financial risk so the focus is to reduce false negative.

## Part 2: Data Understanding

The dataset includes information on 2,464 credit ratings. There are 6 variables in the dataset. Age is the only continuous variable in this dataset with a range from about 20 to just over 63 and an average of 33.8 (SD = 8.539). Table 1 shows the binomial statistics for credit rating. Tables 2-5 show the descriptive statistics for various polynomial variables.

<br>

<p align="center">Table 1 - Descriptive Statistics for Credit Rating</p>

Category	| Frequency	| Percentage	| Cumulative Percentage
| :---: | :---: | :---: | :---: |
Bad	| 1020	| 41%	| 41%
Good	| 1444	| 59%	| 100%

<br>

The highest number of customers have a medium income and the lowest number of customers have a low income.

<p align="center">Table 2 - Descriptive Statistics for Income</p>

Category	| Frequency	| Percentage	| Cumulative Percentage
| :---: | :---: | :---: | :---: |
High	| 777	| 32%	| 32%
Low	| 553	| 22%	| 54%
Medium	| 1134	| 46%	| 100%

<br>

Only 32% of customers have less than 5 credit cards, while the rest have 5 or more credit cards. It appears the majority of the applicants have large credit lines, which can indicate two things:
(1) good credit score so they are accepted for multiple credit cards, or
(2) possible problematic spending behaviors.

<p align="center">Table 3 - Descriptive Statistics for Credit Cards</p>

Category	| Frequency	| Percentage	| Cumulative Percentage
| :---: | :---: | :---: | :---: |
5 or more	| 1666	| 68%	| 68%
Less than 5	| 798	| 32%	| 100%

<br>

Half of the customers have a high school degree while the other half also has a college degree. This may be inteterpreted that half of the applicants have steady income from high-skilled employments.

<p align="center">Table 4 - Descriptive Statistics for Education</p>

Category	| Frequency	| Percentage	| Cumulative Percentage
| :---: | :---: | :---: | :---: |
College	| 1234	| 50%	| 50%
High School	| 1230	| 50%	| 100%

<br>

Only 36% of customers have one or no car loans, while 64% of customers have more than 2 loans. Similar to credit cards, it appears the majority of the applicants have large credit lines, which can indicate two things:
(1) good credit score so they are accepted for multiple loans, or
(2) possible problematic spending behaviors.

<p align="center">Table 5 - Descriptive Statistics for Car Loans</p>

Category	| Frequency	| Percentage	| Cumulative Percentage
| :---: | :---: | :---: | :---: |
More than 2	| 1571	| 64%	| 64%
None or 1	| 893	| 36%	| 100%

<br>

## Part 3: Decision Tree Model Results and Evaluations

There are 15 nodes in the decision tree model. There are 9 terminal nodes, the maximum depth is 3, and the target variables are Good and Bad. The features, in the order of significance, where the sample split are: 

* “Less than 5” and “5 or more”; 
* “Low”, “Medium”, and “High”; 
* “None or 1” and “More than 2”; 
* “≤ 34.290” and “≥34.290”; 
* “≤ 41.124” and “≥41.124”.

<img src="images/Loan Decision Tree.png"/>

**Confusion matrix based on the “Performance Test”**

Predictive Model for Credit Rating	| Actual | Actual 
| :---: | :---: | :---: |
.	| Bad	| Good
Predicted - Bad	| 229	| 98
Predicted - Good	| 57	| 355


**Table of positive class: Bad**

Performance	| Accuracy	| Recall	| Precision
| :---: | :---: | :---: | :---: |
Cross Validation	| 77.39% +/- 2.81% (micro average: 77.39%)	| 81.85% +/- 4.30% (micro average: 81.74%)	| 70.19% +/- 3.38% (micro average: 70.09%) 
Test	| 79.03%	| 80.07%	| 70.03%


**Two groups of bad credit individuals and two groups of good credit Individuals based on the features in this model**

Group	| Describe
| :---: | :---: |
Group 1 (bad credit)	| Individuals with more than 5 or more credit cards and medium-income, and more than 2 car loans
Group 2 (bad credit)	| Individuals with more than 5 or more credit cards and low-income
Group 1 (good credit	| 	Individuals with less than 5 credit cards and medium income
Group 2 (good credit)	| Individuals with more than 5 or more credit cards and high income and older than 41



## Part 4: Examples based on Results

<p align="center">Predictions of bad and good credit individuals<\p>

Profile	| Prediction
| :---: | :---: |
Sara with High income	| Good
John, with more than 5 credit cards and more than 2 car loans	| Bad
Mike, with less than 5 credit cards and medium income	| Good

Loan: $20,000
Net revenue for each loan: $8,000
Risk of default: $14,000

1 The percentage of loan approval:	412/739 = 55.75%

2 The risk in percentage (out of all customers):	57/739 = 7.71%

3 Revenue loss in percentage (out of all customers):	98/739 = 13.36%

4 Revenue in $:	55.75% x 739 x $8,000 = $3,296,000

5 Risk in $:	7.71% x 739 x $14,000 = $798,000

6 Revenue loss in $:	13.36% x 739 x $8,000 = $784,000


## Part 5: Business Recommendations

We are trying to minimize False Negatives (FN) because a higher false negative will lead to higher business risk. In minimizing FN, the customers will be less likely to be falsely predicted as “not default.” 

The positive class here is “default” or bad credit rating because we want to predict it, and by the bank minimizing this risk, they are improving the chances of having less loans being defaulted. To do this, the bank can increase the requirements to take out a loan by increasing the precision of the predictive model. This will decrease FN but may also increase FP. This will also lead to a smaller amount of loans that are accepted. The bank will face a small amount of revenue loss as part of misclassification cost, but the business risk will be minimized.

Suggestions to improve the models based hyperparameters:

* We can use a maximum depth of 10 to achieve better accuracy but if we change it to 3 the data becomes really hard to predict accurately as we would have only two variables to decide from, in this case, it is credit cards and income. 

* The appropriate minimal size for leaf would be 50 but if we change it to 5 the data becomes more accurate but also more prone to overfitting. And the minimal size for the split would be 100 but if we change it to 10 the data tends to have a similar effect of becoming more accurate as well as more prone to overfitting.

