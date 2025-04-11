# ISTA_Exam_2
# This repository looks into creating a model to assist hospitals in understanding the relationship between patients being discharged and readmitted.
## This model utilizes the Hospital Readmissions Reduction Program dataset which is available at [https://data.cms.gov/provider-data/dataset/9n3s-kdb3#data-table]


# - Resources to help understand the topic
##[https://jamanetwork.com/journals/jama/fullarticle/1104511]##
##[https://europepmc.org/article/NBK/nbk368492]##


# - A description for all 12 variables in the dataset
#Variables, meanings, and datatypes:
##Facility Name - This is the facility where the data point took place - String

##Facility ID - This relates each individual facility to an ID number - Integer

##State - The state that the facility resides in - String

##Measure Name - The type of measurement that occurs (medical procedure) - String

##Number of Discharges - The total number of patients discharged for the measurement type - Integer

##Footnote - Additional note about the data point (only about 1/3 have a footnote) - Integer

##Excess Readmission Ratio - Measurement of ratio of the predicted readmission rate to the expected readmission rate - Float

##Predicted Readmission Rate - Predicted 30 day readmission rate for a hospital based on its previous performances for specific cases - Float

##Expected Readmission Rate - Expected 30 day readmission rate for a hospital baseed on readmission rates of similar hospitals with similar cases - Float

##Number of Readmissions - The number of readmissions during the study period - Float

##Start Date - The start date of the study - String

##End Date - The end date of the study - String

##[https://qualitynet.cms.gov/inpatient/hrrp/measures]##


## With so much data we might want to slim it down, so only look at heart attack patients in this study.


# - Question to be answered:
##How is the Excess Readmission Ratio of heart attack patients influenced by the Number of Discharges?

# - Hypothesis:
##If a hospital has a high number of discharges for heart attack patients there will be a lower excess readmission ratio.


# - Why is this Interesting
##For hospitals that see a lot of patients for heart attacks, especially if they are successful in preventing readmission (repeated health issues), we would want to perform a study on why they are successful. By evaluating if it is true that hospitals that see more heart attack patients are better at treating them, then it would make sense to then look into what these hospitals are doing that is more effective than hospitals with a high excess readmission rate. This follow up allows the health industry to better analyze how treatment of these patients is effective. However, in order to perform the follow up we first need to have evidence that it is true.


# - Model Construction
##A linear regression model was constructed utilizing ridge regression on a gradient descent. The output from the linear regression model shows that there is in fact a negative linear relationship between the Number of discharges and the Excess Readmission Ratio.

##Resource to help build a similar model
##[https://www.kaggle.com/code/ninjaac/lasso-and-ridge-regression-from-scratch?utm_source=chatgpt.com]


# - Model Validation
##The model is validated using a K-fold cross validation iterating on K values between 2 and 20. The results of this show a rather constant MSE and an R2 that decreases with an increasing number of folds. I believe this is explained by the high variance in the original dataset.
##[https://isheunesu48.medium.com/cross-validation-using-k-fold-with-scikit-learn-cfc44bf1ce6]
##[https://towardsdatascience.com/evaluation-metrics-model-selection-in-linear-regression-73c7573208be/]


# - Conclusion
Conclusion:
As hypothesized with the initial exploratory data analysis, the number of discharges is negatively correlated with the excess readmissions ratio. For hospitals that are on the upper end of number of discharges for heart attack patients should be more closely studied. These hospitals appear to be most successfully preventing readmission for heart attack related reasons. It is even more impressive considering there are already estimates for how well they should be treating the patients that they are surpassing. Moving forward a model should be created to understand how these hospitals treat heart attack patients that differs from hospitals that don't see as many discharges. This can help in developing more efficient treatment options for other hospitals that could lead to a higher number of successful discharges in the future.
