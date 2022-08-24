# Credit Line Increase Model Card
Analytics Edge and Data Ethics_DNSC_6301 Project (Credit line Increase)

<h3>Basic Information</h3>
<ul>
  <li><b>Group no 28:</b> <br>Pranjal Shukla - Pranjalshukla98@gwmail.gwu.edu</br>Chun yueh Liu - adelynliu8487@gwu.edu<br>Dimple Kuldeep Modi - dimple.modi@gwmail.gwu.edu</br> Mariam Zain - mzain22@gwmail.gwu.ed</li>
  <li><b>Model date</b> : August 2022</li>
  <li><b>Model version:1.0<br>Python version: 3.7.13</br>sklearn version: 1.0.2</li>
  <li>License :MIT</li>
  <li>Model Implemetation code: https://github.com/pranjals26/DNSC_6301_Project_Group_28/blob/main/DNSC_6301_Project_Group_28.ipynb</l1>
  
  <h3>Intented Use</h3>
  <ul>
  <li><b>Primary Intended uses:</b> This model is an example probability of default classifier, with an example use case for determining eligibility for a credit line increase.</li>
  <li><b>Primary intended users:</b> GWU DNSC 6301 bootcamp students.</li>
  <li>Out-of-scope use cases: Any use beyond an educational example is out-of-scope.</li>
  
  <h3>Training Data</h3>
  <li>Data Dictionary:</li>
  <table>
  <tr>
    <th>Name</th>
    <th>Modeling Role</th>
    <th>Measurement Level</th>
    <th>Description<//th>
  </tr>
  <tr>
    <td>ID</td>
    <td>ID</td>
    <td>int</td>
    <td>unique row indentifier</td>
  </tr>
  <tr>
    <td>LIMIT_BAL</td>
    <td>input</td>
    <td>float</td>
    <td>amount of previously awarded credit</td>
  </tr>
  <tr>
    <td>SEX</td>
    <td>demographic information</td>
    <td>int</td>
    <td>1 = male; 2 = female</td>
  </tr>
   <tr>
    <td>RACE</td>
    <td>demographic information</td>
    <td>int</td>
    <td>1 = hispanic; 2 = black; 3 = white; 4 = asian</td>
  </tr>
  <tr>
    <td>EDUCATION</td>
    <td>demographic information</td>
    <td>int</td>
    <td>1 = graduate school; 2 = university; 3 = high school; 4 = others</td>
  </tr>
  <tr>
    <td>EDUCATION</td>
    <td>demographic information</td>
    <td>int</td>
    <td>1 = graduate school; 2 = university; 3 = high school; 4 = others</td>
  </tr>
  <tr>
    <td>MARRIAGE</td>
    <td>demographic information</td>
    <td>int</td>
    <td>1 = married; 2 = single; 3 = others</td>
  </tr>
  <tr>
    <td>AGE</td>
    <td>demographic information</td>
    <td>int</td>
    <td>Age in years</td>
  </tr>
   <tr>
    <td>PAY_0, PAY_2 - PAY_6</td>
    <td>inputs</td>
    <td>int</td>
    <td>history of past payment; PAY_0 = the repayment status in September, 2005; PAY_2 = the repayment status in August, 2005; ...; PAY_6 = the repayment status in April, 2005. The measurement scale for the repayment status is: -1 = pay duly; 1 = payment delay for one month; 2 = payment delay for two months; ...; 8 = payment delay for eight months; 9 = payment delay for nine months and above</td>
  </tr>
  <tr>
    <td>BILL_AMT1 - BILL_AMT6</td>
    <td>inputs</td>
    <td>float</td>
    <td>amount of bill statement; BILL_AMNT1 = amount of bill statement in September, 2005; BILL_AMT2 = amount of bill statement in August, 2005; ...; BILL_AMT6 = amount of bill statement in April, 2005
</td>
  </tr>
    <tr>
    <td>PAY_AMT1 - PAY_AMT6</td>
    <td>inputs</td>
    <td>float</td>
    <td>aamount of previous payment; PAY_AMT1 = amount paid in September, 2005; PAY_AMT2 = amount paid in August, 2005; ...; PAY_AMT6 = amount paid in April, 2005
</td>
  </tr>
    <tr>
    <td>DELINQ_NEXT</td>
    <td>target</td>
    <td>int</td>
    <td>whether a customer's next payment is delinquent (late), 1 = late; 0 = on-time
</td>
  </tr>  
</table>
  

  
  
      
  
