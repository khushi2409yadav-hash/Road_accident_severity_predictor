                 ##ACCIDENT SEVERITY PREDICTION

Problem Statement:
Most existing accident severity models focus only on getting high overall accuracy. But since most accidents are minor, these models get good accuracy just by predicting "Slight" every time — while missing the rare but serious Fatal and Serious cases that matter most. This project builds a model that pays real attention to those critical cases, not just overall accuracy, using factors like weather, time of day, day of week, and driver/casualty age band.

Objective of the Project:
To develop, compare, and evaluate multiple machine learning classification models (Decision Tree, Random Forest, Logistic Regression, SVM, KNN) for predicting road accident severity, with the specific goal of improving detection of Serious and Fatal accidents through class-imbalance handling techniques , using real-world factors (weather, time, day, age band, road/junction type, etc.) and to deploy the best model as a usable app that can also help governments and traffic authorities plan better safety measures — like extra caution during certain weather, times, or high-risk age groups.

Research Gaps:

     •  Most existing models are trained on one country's data and don't generalize well elsewhere. 
		 
     •  Class imbalance (too few Fatal/Serious cases) isn't handled properly in most studies, so those cases get missed. –solved it
		 
     •  Real-time factors like live weather and traffic aren't included in most datasets. 
		 
•	Most models aren't explainable, making it hard to use them for real policy decisions.

•	There's no standard way papers report their results, making comparisons unreliable.

Dataset Name:

           Road traffic accidents-https://www.kaggle.com/datasets/saurabhshahane/road-traffic-accidents
					 
Number of Samples and Features in the dataset:

        •  12,316 accident records 
				
        •  32 columns (before selection)
				
Data Preprocessing Performed:

•  Filled missing values using the most frequent value (mode). 

•  Cleaned and grouped similar categories (e.g., vehicle types). 

•  Converted Time into four time slots: Morning, Afternoon, Evening, and Night to avoid unnecessary columns. 

•  Applied One-Hot Encoding to convert categorical features into numbers.

•  Used Label Encoding for the target variable (Slight, Serious, Fatal). 

•  Applied StandardScaler for SVM and KNN models. 

•  Split the dataset into 80% training and 20% testing. 

•  Handled class imbalance using class_weight='balanced' to improve prediction of serious and fatal accidents.


Machine Learning/Deep Learning Models Implemented:

                       Decision Tree, Random Forest, Logistic Regression, Support Vector Machine (SVM), K-Nearest Neighbors (KNN)
											 
Best Model Selected:

             Random Forest— selected for having the smallest train/test accuracy gap  and by far the best minority-class recall of all five models.
						 
Performance Metrics Achieved:

            Model                                Train Acc        Test Acc    Gap       Fatal recall           Serious recall
						
Decision Tree (balanced)                          99.0%           76.8%       huge          0.35                      0.29

Random Forest (balanced)                          83.5%           76.1%       small         0.43                      0.33

Logistic Regression                               84.8%           83.8%       tiny          0.00                      0.01

SVM (balanced, scaled)                            85.4%           70.7%       large         0.30                      0.39

KNN (scaled)                                      85.3%           83.6%       small         0.00                      0.02

Current Findings/Observations:

•  A preprocessing issue with the Time feature created too many columns and led to overfitting, which was fixed by grouping time into four intervals. 

•  Improving prediction of Serious and Fatal accidents reduced overall accuracy, showing a trade-off between accuracy and balanced performance. 

•  SVM performed better after feature scaling, while tree-based models did not require scaling. 

•  Even after handling class imbalance, predicting Serious and Fatal accidents accurately is still difficult, showing there is room for further improvement.

Challenges Faced:

•   Most records were Slight accidents, making it difficult for models to correctly predict Serious and Fatal accidents. 

•  Optimizing only for accuracy gave misleading results, so F1-score (macro) was used to improve prediction of all classes. 

•  Scaling improved the performance of SVM, but KNN still struggled to predict fatal accidents. 

•   A model with the highest accuracy was not always the best at identifying serious and fatal accidents, which are the most important for road safety.

Next Steps/Planned Improvements:

•	Improve the Streamlit UI by organizing all input features into clear sections (Driver, Vehicle, Road, Weather, Time, etc.) for a better user experience. 

•	Making the app auto-fill the Weather and Time fields using live data instead of the user manually selecting them

•	Instead of displaying only the class, show it clearly:

         Slight 
				 
         Serious 
				 
         Fatal 
				 
Also add a short explanation beneath the prediction.

•	Confidence score

•	Risk-Threshold Warning System

