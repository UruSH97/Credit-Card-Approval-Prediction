## Forecasting Credit Card Application Outcomes using Logistic Regression

<p>Financial institutions often receive <em>numerous</em> credit card applications. A significant number of these applications face rejection due to various reasons such as high outstanding loans, low income, or excessive credit report inquiries. Manual scrutiny of these applications is tedious, error-prone, and time-intensive, which can impact the bank's efficiency and profitability. Fortunately, this task can be streamlined using machine learning, a method increasingly adopted by most commercial banks. In this notebook, I've developed an automated credit card approval prediction system using machine learning techniques, mirroring the practices of real-world banks.</p>

<p>The dataset employed in this analysis is sourced from the <a href="http://archive.ics.uci.edu/ml/datasets/credit+approval">Credit Card Approval dataset</a> available at the UCI Machine Learning Repository. The structure of this notebook unfolds as follows:</p>
<ul>
<li>Initially, I loaded and inspected the dataset.</li>
<li>The dataset encompasses both numerical and categorical features, with values spanning diverse ranges and some missing entries.</li>
<li>Subsequently, I preprocessed the dataset to enhance the predictive accuracy of the chosen machine learning model.</li>
<li>Once the data was appropriately prepared, I conducted exploratory data analysis to derive insights.</li>
<li>Finally, I constructed a machine learning model capable of determining whether an individual's credit card application will be approved or declined.</li>
</ul>

## Sequential Steps for Credit Card Approval Prediction:
* I began by loading and examining the dataset. Notably, due to data confidentiality, the feature names have been anonymized.
* I then identified the pivotal features for credit card application assessment. Although the dataset features are anonymized for privacy reasons, <a href="http://rstudio-pubs-static.s3.amazonaws.com/73039_9946de135c0a49daa7a0a9eda4a67a72.html">this blog</a> provides valuable insights into potential features. Common features in credit card applications encompass <code>Gender</code>, <code>Age</code>, <code>Debt</code>, <code>Married</code>, <code>BankCustomer</code>, <code>EducationLevel</code>, <code>Ethnicity</code>, <code>YearsEmployed</code>, <code>PriorDefault</code>, <code>Employed</code>, <code>CreditScore</code>, <code>DriversLicense</code>, <code>Citizen</code>, <code>ZipCode</code>, <code>Income</code>, and <code>ApprovalStatus</code>. This information serves as a valuable starting point, enabling us to map these features to the respective output columns.
* A preliminary examination of the data reveals a mix of numerical and non-numerical features, necessitating preprocessing.
* Subsequent steps involved addressing missing values in both numerical and categorical columns.
* Further preprocessing was categorized into three primary tasks:
<ol>
<li>Conversion of non-numeric data to numeric format.</li>
<li>Division of the data into training and testing sets.</li>
<li>Normalization of feature values to achieve uniformity.</li>
</ol>
<p>Initially, I converted all non-numeric data into numeric format. This conversion not only enhances computational efficiency but is also essential for many machine learning models, including XGBoost and those developed using scikit-learn, which typically require strictly numeric data. This conversion was accomplished using a technique known as <a href="http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.LabelEncoder.html">label encoding</a>.</p>

* With all non-numeric values successfully converted to numeric format, the data was split into training and testing sets to facilitate distinct phases of machine learning modeling without compromising data integrity.
<p>Features like <code>DriversLicense</code> and <code>ZipCode</code> were deemed less crucial for predicting credit card approvals and were consequently excluded. This process, known as <em>feature selection</em> in Data Science parlance, allows us to optimize our machine learning model by focusing on the most influential features. </p>

* The dataset was then bifurcated into two distinct sets - training and testing.

* <p>Predicting credit card application outcomes essentially constitutes a <a href="https://en.wikipedia.org/wiki/Statistical_classification">classification</a> task. As per <a href="http://archive.ics.uci.edu/ml/machine-learning-databases/credit-screening/crx.names">UCI guidelines</a>, the dataset predominantly comprises instances corresponding to "Denied" status compared to "Approved" status. Specifically, out of 690 instances, 383 (55.5%) applications were denied, while 307 (44.5%) were approved.</p>
<p>This statistical distribution serves as a benchmark. An effective machine learning model should accurately predict application statuses based on these proportions.</p>
<p>Choosing an appropriate model is pivotal. A critical consideration is whether the features influencing credit card approval decisions are correlated. While correlation measurement is beyond the scope of this notebook, we will operate under the assumption of feature correlation. Consequently, we will leverage the superior performance of generalized linear models, starting with a Logistic Regression model.</p>

* <p>The model's performance will be evaluated using the test set in terms of <a href="https://developers.google.com/machine-learning/crash-course/classification/accuracy">classification accuracy</a>. Additionally, the <a href="http://www.dataschool.io/simple-guide-to-confusion-matrix-terminology/">confusion matrix</a> will be examined. In the context of credit card application prediction, it is imperative to ascertain whether the model accurately identifies applications that should be approved or denied. The confusion matrix provides insights into the model's performance from this perspective.</p>

## Results:
<p><img src="/screenshot.png"></p><br>
<b>Accuracy of logistic regression classifier:</b>  0.8377192982456141</h3>
<b>Confusion matrix:</b>
 [[93 10]
 [27 98]]
