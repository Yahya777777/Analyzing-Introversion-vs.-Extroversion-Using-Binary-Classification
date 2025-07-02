Analyzing Introversion vs. Extroversion Using Binary Classification
Yahya Chebab

1. Motivation
I used machine learning to predict whether someone is an introvert or extrovert based on their behavioral patterns. This approach avoids long personality tests and can help personalize user experiences in apps or research settings.

2. Summary
I analyzed a dataset of 2,900 individuals (1,491 introverts and 1,409 extroverts) using four supervised machine learning algorithms: Logistic Regression, Support Vector Machine (SVM), K-Nearest Neighbors (KNN), and Linear Discriminant Analysis (LDA). My goal was to classify each person as either an introvert (1) or extrovert (0) based on their daily habits and social behaviors.

3. Dataset
The dataset includes features such as:

Time_spent_Alone: Average hours spent alone each day

Stage_fear: Whether they have stage fright (Yes = 1, No = 0)

Social_event_attendance: Frequency of attending events (0–10 scale)

Going_outside: How often they go out (0–10 scale)

Drained_after_socializing: Do they feel drained after socializing? (Yes = 1, No = 0)

Friends_circle_size: Number of close friends

Post_frequency: Social media posting frequency (0–10 scale)

Personality: Target label (Introvert = 1, Extrovert = 0)

Dataset source: [Extrovert vs Introvert Behavior Data on Kaggle](https://www.kaggle.com/datasets/rakeshkapilavai/extrovert-vs-introvert-behavior-data)

4. Data Preprocessing
I handled missing numerical values (like Time_spent_Alone and Friends_circle_size) by filling them with the median. For categorical features like Stage_fear and Drained_after_socializing, I dropped rows with missing values (since they were under 5%). I encoded categorical variables numerically and used StandardScaler to normalize the data. The dataset was split 80% for training and 20% for testing.

5. Machine Learning Algorithms
Logistic Regression
I used a sigmoid function to estimate probabilities. I tested different thresholds (0.1, 0.45, 0.5, and 0.55) to analyze how sensitivity and specificity shifted.

Support Vector Machine (SVM)
SVM finds the best boundary between introverts and extroverts by maximizing the margin. It performed really well, especially with overlapping data distributions.

K-Nearest Neighbors (KNN)
I tested KNN with k-values of 3, 5, and 21. Performance improved as k increased. At k = 21, KNN achieved results comparable to Logistic Regression and SVM.

Linear Discriminant Analysis (LDA)
LDA assumes normally distributed data and separates the classes using a linear combination of features. It performed just as well as the other models.

6. Results and Evaluation
I evaluated the models using accuracy, precision, recall, F1-score, and confusion matrices. Introverts (label 1) were treated as the positive class.

Logistic Regression: At thresholds of 0.45, 0.5, and 0.55, performance was identical with high accuracy (~93.34%) and balanced precision and recall. Lowering the threshold to 0.1 increased precision but lowered recall significantly.

SVM: Matched Logistic Regression in every metric, showing strong, stable performance.

KNN: At k = 3, performance was decent but slightly weaker. At k = 5, it improved noticeably. At k = 21, results matched the top-performing models.

LDA: Achieved the same results as Logistic Regression, SVM, and KNN with k = 21, indicating that the data was linearly separable.

7. Conclusion
All four models performed well in classifying introverts and extroverts.

Logistic Regression and LDA were simple, interpretable, and accurate.

SVM handled overlapping traits effectively.

KNN required tuning but matched the best models at higher k.

This project shows that machine learning can accurately predict personality traits from everyday behaviors, potentially replacing traditional surveys in many use cases.