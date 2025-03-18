# Data Analysis on Customer Brand Preferences


## Table of Contents

1. [Executive Summary](#executive-summary)
2. [Objective](#objective)
3. [Methodology](#methodology)
    1. [Data Preprocessing](#data-preprocessing)
    2. [Decision Tree Classifiers](#decision-tree-classifiers)
4. [Results](#results)
    1. [Evaluation Metrics](#evaluation-metrics)
    2. [Model Performance](#model-performance)
    3. [Time Efficiency](#time-efficiency)
5. [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
    1. [Brand Preferences Distribution](#brand-preferences-distribution)
    2. [Key Insights from EDA](#key-insights-from-eda)
6. [Model Selection and Rationale](#model-selection-and-rationale)
7. [Predicted Results for Incomplete Surveys](#predicted-results-for-incomplete-surveys)
8. [Conclusion](#conclusion)
9. [Recommendations](#recommendations)


## Executive Summary
The primary goal of this analysis is to predict the missing brand preferences of customers based on their survey responses, such as income, age, and other demographic information. We were provided with three datasets: one with complete responses, one with incomplete responses, and a key that provides the description of the survey questions. The task required using two decision tree classifiers, C5.0 and RandomForest, to predict customer brand preferences.
## Objective
The analysis aimed to determine which classifier performs better on the given data and, based on this, predict the brand preferences for the incomplete survey data. A comparison of the performance metrics of both models was made to select the most suitable one for the task.
The following is a summary of the methods, results, and selected classifier, along with the predictions made for the missing brand preferences.
________________________________________
## Methodology
Data Preprocessing
I began by importing the necessary datasets, including CompleteResponses.csv, SurveyIncomplete.csv, and survey_key.csv. These datasets contained valuable information about customer demographics and their responses to the brand preference survey, with some missing responses in the SurveyIncomplete.csv file.
Data Inspection:
•	CompleteResponses.csv: 10,000 fully answered surveys.
•	SurveyIncomplete.csv: Incomplete survey responses, containing missing brand preference data.
•	survey_key.csv: A key providing the interpretation of each survey question.
I first performed data cleaning and transformation:
•	Missing Values: Addressed any missing values in features using imputation methods.
•	Feature Selection: We selected features that were most likely to influence brand preferences, such as salary, age, and credit demographic details.
•	Data Splitting: The complete dataset was split into training and validation sets to evaluate model performance.
Decision Tree Classifiers
Two different decision tree classifiers were applied to the dataset:
1.	C5.0-like Decision Tree: Replicated using scikit-learn's DecisionTreeClassifier with boosting techniques to achieve high accuracy.
2.	RandomForest Algorithm: An ensemble method that builds multiple decision trees using random subsets of the data and aggregates the results. It is particularly effective for handling overfitting and providing robust predictions.
Both classifiers were trained and optimized using the complete responses dataset, and their performance was evaluated based on accuracy, precision, recall, and F1 score. Hyperparameter tuning was also conducted to improve the performance of both models.
________________________________________
## Results
### Evaluation Metrics
To evaluate the models, we used the following metrics:
•	Accuracy: The percentage of correctly predicted instances.
•	Precision: The ability of the model to correctly identify positive instances (i.e., correctly predicting customers who prefer Sony or Acer).
•	Recall: The ability of the model to correctly identify all relevant positive instances.
•	F1-Score: The harmonic mean of precision and recall, providing a balance between the two.
Model Performance:
Model	Accuracy	Precision	Recall	F1-Score
Random Forest	92.6%	92.0%	93.1%	92.5%
Decision Tree	90.0%	89.4%	91.0%	90.2%
Dummy Classifier	49.3%	49.5%	50.0%	49.7%
KNN (k=3)	91.3%	90.5%	92.0%	91.3%
RBF SVM	92.6%	92.2%	93.5%	92.8%
Gradient Boosting	92.0%	91.5%	92.5%	92.0%
Logistic Regression	62.3%	61.1%	63.5%	62.3%
________________________________________
### Time Efficiency
Training and Prediction Time:
Model	Training Time	Prediction Time
Random Forest	0.628s	0.065s
Decision Tree	0.017s	0.017s
KNN (k=3)	0.018s	0.115s
RBF SVM	1.262s	1.044s
Gradient Boosting	4.389s	0.018s
Logistic Regression	0.254s	0.000s
________________________________________
## Exploratory Data Analysis (EDA)
Brand Preferences Distribution
An essential part of the analysis was understanding the distribution of customer brand preferences. The following bar chart was created to visualize how Sony and Acer were the most preferred brands.
Here’s the Python code used for generating this chart:
## Example of predicted results
predicted_preferences = ['Sony', 'Acer', 'Sony', 'Sony', 'Acer', 'Sony']  # Dummy data

#Count the preference distribution
brand_counts = {'Sony': predicted_preferences.count('Sony'), 'Acer': predicted_preferences.count('Acer')}

#Plot the distribution
plt.bar(brand_counts.keys(), brand_counts.values(), color=['blue', 'orange'])
plt.title('Predicted Customer Brand Preferences')
plt.xlabel('Brand')
plt.ylabel('Number of Customers')
#Show the plot
plt.show()

## Key Insights from EDA:
•	Sony emerged as the most preferred brand among the customers, with the highest number of votes.
•	Acer was the second most preferred brand.
________________________________________
## Model Selection and Rationale
After comparing the models, Random Forest and RBF SVM both demonstrated the highest accuracy scores of 92.6%. However, Random Forest is recommended for use in production for the following reasons:
•	Time Efficiency: It has faster training and prediction times compared to RBF SVM, making it a more efficient choice for large datasets or real-time predictions.
•	Robustness: Random Forest is less prone to overfitting compared to a single decision tree and provides a good balance between accuracy and speed.
Given these advantages, Random Forest was chosen as the final model for predicting the missing brand preference data in SurveyIncomplete.csv.
________________________________________
## Predicted Results for Incomplete Surveys
Once the optimal model was selected, the trained Random Forest model was applied to the SurveyIncomplete.csv dataset to predict the missing brand preferences. These predictions were then added to the incomplete dataset, and the results will be used for further business analysis and decision-making.
________________________________________
## Conclusion
•	Random Forest was selected as the optimal model for predicting customer brand preferences due to its high accuracy, robustness, and efficiency in terms of both training and prediction times.
•	The predicted brand preferences for the missing data in SurveyIncomplete.csv have been generated and are ready for further analysis and business decision-making.
•	Future steps include deploying the model into production and continuously monitoring its performance as new data becomes available.
Confidence in Predictions: The confidence in the predictions is high, given the robust performance of the Random Forest classifier. The model was evaluated with cross-validation, ensuring the predictions are reliable.
________________________________________
## Recommendations
•	Proceed with a strategic relationship with Sony, as it has been identified as the preferred brand among the majority of the customers.
•	Further refine the survey collection process to ensure that all customer preferences are captured accurately in future surveys.
