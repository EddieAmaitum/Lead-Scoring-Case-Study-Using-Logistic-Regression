## **Lead Scoring Case Study**

### **Summary of Problem Statement**
X Education sells online courses to professionals through their website and marketing efforts. However, they struggle with low lead conversion rates, with only around 30% of acquired leads becoming paying customers. 

To address this issue, X Education wants to identify "Hot Leads" with a higher likelihood of conversion. They need a lead scoring model to assign scores based on conversion potential. The CEO's target is to increase the conversion rate to around 80%. By focusing their sales efforts on the most promising leads, X Education aims to improve efficiency and boost overall conversion rates. The model should help prioritize communication and engagement with potential customers who are more likely to convert.

### **Objectives of this case study**
* Build a logistic regression model to assign a lead score between 0 and 100 to each of the leads which can be used by the company to target  potential leads. A higher score would mean that the lead is hot, i.e. is most likely to convert whereas a lower score would mean that the lead is cold and will mostly not get converted.

* There are some more problems presented by the company which our model should be able to adjust to if the company's requirement changes in the future so we will need to handle these as well. These problems are provided in a separate doc file. It will be filled based on the logistic regression model we get. Also, will make sure to include this in the final PPT where we will make recommendations.

### **Data** 
* We have been provided with a leads dataset from the past with around 9000 data points. 
* This dataset consists of various attributes such as Lead Source, Total Time Spent on Website, Total Visits, Last Activity, etc.
* The target variable, in this case, is the column ‘Converted’ which tells whether a past lead was converted or not wherein 1 means it was converted and 0 means it wasn’t converted.
* We have also been provided with a  data dictionary
  
### **Approach**
* Importing Libraries

* Loading the dataset

* Inspecting and understanding the data

* Data Cleaning and some EDA, some steps taken include:
    * Handling the 'Select' level that is present in some categorical variables
    * Dropping columns with high percentage of missing values and/or redundant columns
    * Checking the number of unique categories in categorical columns
    * Imputation of missing values in cloumns with less percentage of missing values
    * Some feature manupulation
    * Dropping extremely skewed features
    * Handling of outliers

* Exploratory Data Analysis
    * Categorical variable analysis
    * Numerical variable analysis

* Data Preparation
    * Converting some binary variables (Yes/No) to 0/1
    * Creating dummies for other categorical variables
    * Performing train - test split (I used train - 70%, test - 30%)
    * Feature Scaling

* Model Building
    * Built multiple models iteratively
    * Using Recursive Feature Elimination (RFE) to eliminate some less signicant features
    * Using p - value to retain only significant features
    * Using Variance Inflation Factor (VIF), to limit multicollinearity 

* Model Evaluation, this included: 
    * Using accuracy
    * Using Receiver Operating Charateristic (ROC) Curve
    * Using Sensitivity and Specificity
    * Using Precision and Recall

* Making predictions on the test set
    * Comparing model performance versus the train data to ensure the model generalized well on test data

* Calculating Lead Score

* Determining Feature Importance

* Conclusion
  

### **Key Observations and Insights**

* The original dataset has 9240 enteries and 37 columns
* The original dataset has 9240 enteries and 37 columns
* There were no duplicate values in the dataset
* The dataset had missing values, we handled these through various techniques icluding removing / imputation
* The dataset had some redundant columns e.g Lead columns so we dropped some redundat and/insignicant features
* We Converted the level 'Select' to NaN as Select means the customer did not select an option. Columns with 'Select' where: ['Specialization',  'How did you hear about X Education',  'Lead Profile',  'City']
* We encoded categorical variables for easier understanding by the model
* We created dummy variables for some categorical features with multiple levels
* Some features like Search, Magazine were extremely skewed thus not important for our analysis, we dropped them
* We had a conversion rate of 38.02%, this is a relatively good representation of both classes
* Numeric features TotalVisits and Page Views Per Visit had some outliers that we dealt with

### **Insights on our recommended model**
* Having explored several models, our best model had the following characteristics
    * All p-values were less than 0.05 implying that our features were significant
    * All VIFs were under 5 implying there was very low multicolliniarity
    * The model genralized very well on the test data set with test accuracy within less than 5% of the train accuracy
  
### **Business Recommendations**
* When looking at the feature Lead Source
    * The majority of generated leads come from Google and Direct traffic, while the least number of leads originate from Others
    * The Welingak website exhibits a very high conversion rate, hence, it  is advisable to maximize leads from this website
    * Prioritizing Olark chat, Organic search, Direct traffic, and Google leads may result in increased lead conversion
  
* Management specialization is important as manager seem to be likely to convert favourably
* From EDA, most of the successfully converted leads come from the Unemployed, special attention should be given to this group
* The are good chances of a working professional to sign up for a course
* It appears that the categories of "Housewives," "Businessman," "Student," and "Other" are not easily converted to enroll in the course
* When looking at the feature Last Activity,SMS Sent has the highest success conversion rate followed by Email Opened

* The probability of lead conversion tends to increase as the values of the following features increase:
    * Lead Source_Welingak Website
    * Lead Origin_Lead Add Form
    * Lead Origin_Landing Page Submission
    * What is your current occupation_Working professional
    * Lead Source_Olark Chat
    * Lead Quality_High in Relevance
    * Total Time Spent on Website

* The probability of lead conversion tends to decrease as the values of the following features decrease:
    * Lead Quality_Worst
    * Lead Quality_Not Sure
    * Last Notable Activity_Email Link Clicked
    * Last Notable Activity_Modified
    * Last Notable Activity_Page Visited on Website
    * Last Notable Activity_Olark Chat Conversation
    * Last Notable Activity_Email Opened
    * Last Activity_Email Bounced
    * Do Not Email

* It is important to note that, based on the business requirements, we have the flexibility to adjust the probability threshold value. Modifying this threshold value allows us to control the trade-off between sensitivity and specificity in the model. Increasing the threshold will decrease sensitivity but increase specificity, while decreasing the threshold will have the opposite effect, increasing sensitivity but decreasing specificity. This adjustment allows us to tailor the model's behavior to align with specific business needs and priorities.

* A high sensitivity value ensures that most leads who are likely to convert are correctly predicted as such. On the other hand, a high specificity value ensures that leads with borderline conversion probabilities are not falsely selected. In other words, high sensitivity focuses on minimizing false negatives (leads who should have been identified as likely to convert but were missed), while high specificity aims to minimize false positives (leads who are incorrectly identified as likely to convert). Balancing these two measures is crucial to achieve an optimal prediction outcome for lead conversion.
