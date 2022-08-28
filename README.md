# Credit Line Increase Model Card
Analytics Edge and Data Ethics_DNSC_6301 Project 

### Basic Information

* **Person or organization developing model**: 
   - Pranjal Shukla - Pranjalshukla98@gwmail.gwu.edu
   - Chun Yueh Liu - adelynliu8487@gwmail.gwu.edu
   - Dimple Kuldeep Modi - dimple.modi@gwmail.gwu.edu
   - Mariam Zain - mzain22@gwmail.gwu.edu
* **Model date**: August 28, 2022
* **Model version**: 1.0
* **License**: MIT
* **Model implementation code**: [DNSC_6301_Project_Group_28.ipynb](https://github.com/pranjals26/DNSC_6301_Project_Group_28/blob/main/DNSC_6301_Project_Group_28.ipynb)
  
  ### Intended Use
* **Primary intended uses**: This model is an *example* probability of default classifier, with an *example* use case for determining eligibility for a credit line increase.
* **Primary intended users**: Students in GWU DNSC 6301 bootcamp.
* **Out-of-scope use cases**: Any use beyond an educational example is out-of-scope.

### Training Data

* Data dictionary: 

| Name | Modeling Role | Measurement Level| Description|
| ---- | ------------- | ---------------- | ---------- |
|**ID**| ID | int | unique row indentifier |
| **LIMIT_BAL** | input | float | amount of previously awarded credit |
| **SEX** | demographic information | int | 1 = male; 2 = female
| **RACE** | demographic information | int | 1 = hispanic; 2 = black; 3 = white; 4 = asian |
| **EDUCATION** | demographic information | int | 1 = graduate school; 2 = university; 3 = high school; 4 = others |
| **MARRIAGE** | demographic information | int | 1 = married; 2 = single; 3 = others |
| **AGE** | demographic information | int | age in years |
| **PAY_0, PAY_2 - PAY_6** | inputs | int | history of past payment; PAY_0 = the repayment status in September, 2005; PAY_2 = the repayment status in August, 2005; ...; PAY_6 = the repayment status in April, 2005. The measurement scale for the repayment status is: -1 = pay duly; 1 = payment delay for one month; 2 = payment delay for two months; ...; 8 = payment delay for eight months; 9 = payment delay for nine months and above |
| **BILL_AMT1 - BILL_AMT6** | inputs | float | amount of bill statement; BILL_AMNT1 = amount of bill statement in September, 2005; BILL_AMT2 = amount of bill statement in August, 2005; ...; BILL_AMT6 = amount of bill statement in April, 2005 |
| **PAY_AMT1 - PAY_AMT6** | inputs | float | amount of previous payment; PAY_AMT1 = amount paid in September, 2005; PAY_AMT2 = amount paid in August, 2005; ...; PAY_AMT6 = amount paid in April, 2005 |
| **DELINQ_NEXT**| target | int | whether a customer's next payment is delinquent (late), 1 = late; 0 = on-time |

* **Source of training data**: GWU Blackboard, email `jphall@gwu.edu` for more information
* **How training data was divided into training and validation data**: 50% training, 25% validation, 25% test
* **Number of rows in training and validation data**:
  * Training rows: 15,000
  * Validation rows: 7,500
 

### Test Data
* **Source of test data**: GWU Blackboard, email `jphall@gwu.edu` for more information
* **Number of rows in test data**: 7,500 / (30000, 26)
* **State any differences in columns between training and test data**: None

### Model details
* **Columns used as inputs in the final model**: 'LIMIT_BAL',
       'PAY_0', 'PAY_2', 'PAY_3', 'PAY_4', 'PAY_5', 'PAY_6', 'BILL_AMT1',
       'BILL_AMT2', 'BILL_AMT3', 'BILL_AMT4', 'BILL_AMT5', 'BILL_AMT6',
       'PAY_AMT1', 'PAY_AMT2', 'PAY_AMT3', 'PAY_AMT4', 'PAY_AMT5', 'PAY_AMT6'
* **Column(s) used as target(s) in the final model**: 'DELINQ_NEXT'
* **Type of model**: Decision Tree 
* **Software used to implement the model**: Python, scikit-learn
* **Version of the modeling software**: 0.22.2.post1
* **Hyperparameters or other settings of your model**: 
```
DecisionTreeClassifier(ccp_alpha=0.0, class_weight=None, criterion='gini',
                       max_depth=6, max_features=None, max_leaf_nodes=None,
                       min_impurity_decrease=0.0, min_impurity_split=None,
                       min_samples_leaf=1, min_samples_split=2,
                       min_weight_fraction_leaf=0.0, presort='deprecated',
                       random_state=12345, splitter='best')`
```
### Quantitative Analysis

| Tr AUC | Val AUC | Test AUC |
| ------ | ------- | -------- |
| 0.7837 | 0.7496  | 0.7438 |



#### Correlation Heatmap
![Correlation Heatmap](Heatmap.png)

* The heat map shows how the variables are correlating with each other. It shows a high correlation between race and the payment delinquency which raises a red flag indicating bias discrimination


![Iteration Plot](https://github.com/pranjals26/DNSC_6301_Project_Group_28/blob/main/Iteration%20Plot.png)


* This graph shows the training AUC line growing very high as the tree gets deeper. However, the validation AUC line starts going down somewhere between 4-6, which indicates the model isn't performing well. It also shows a continuous decline past tree depth of 8 as it starts to memorize and overfit the data. In summary, the model is not generalizing well

![Variable importance](https://github.com/pranjals26/DNSC_6301_Project_Group_28/blob/main/Variable%20importance%20.png)

* The Variable importance helps find a good decision model at pay_0, the most recent payment bill. The graph signifies that pay_0 has more significance. It is a red flag to have more importance on only one variable; Therefore, the model is too dependent on only the pay_0 variable. 


![Final_Iteration Plot](https://github.com/pranjals26/DNSC_6301_Project_Group_28/blob/main/Tress%20depth%20and%20AUC%20Iteration%20plot.png)

* This graph shows three lines: Training AUC, Validation AUC, and Hispanic-to-white AIR. The training AUC line increases to one as the decision tree depth gets more involved. The validation AUC helps find the number of decision trees used for the model. The Hispanic-to-White AIR line was selected because it had the lowest fairness measure. It is up above 0.8 at the tree depth of 6. In terms of fairness and accuracy, the decision tree depth at 6 is a feasible model

## Ethical Considerations

### Potential Negative Impacts:

Math or software problems:
* The test AUC is approximately 70%, which indicates that there is still a 30% probability of having an error in our model. 
* Google Collaborate has privacy issues, but only users with permission to view or edit the file can access it. Hence, Google has intensely made its Open Source programming protected and private. 
* The probability of data focuses on either being misconstrued, adjusted, or missing. Many potential data lead to questions regarding yield legitimacy.

### Real-world risks: 
* Users who trust the model too much and make decisions without specific consideration may cause uncertain damage and negative consequences.

### Potential Uncertainties

Math or software problems:
* When executing the decision tree model with personal information, it is questionable if the privacy and information are well protected.

### Real-world risks: 
* With a data set that centers around demographical data, uncertainties around implicit biases arise.
* Everyone should be treated fairly. When it comes to decision-making, it is not reasonable that a person is approved or denied based on the previous actions of a similar demographic group.

### Unexpected Results

* When it comes to results about the variable importance, pay_0 shows remarkable output compared to other variables. Hence, if there is an error or missing value in pay_0, we are likely to have unexpected results that we cannot predict.






  
      
  
