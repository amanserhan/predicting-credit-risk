# predicting-credit-risk
This project involves building a machine learning model to predict the risk for credit card applicants. The primary challenge addressed in this project is the significant class imbalance, where instances of the positive class are much less frequent than instances of the negative class. The goal is to develop a model that can accurately identify high-risk customers despite this imbalance.

## Data

### Features

The dataset used in this project contains 20 features, including:

- **Gender**: The gender of the customer.
- **Has a car**: Whether the customer owns a car.
- **Has a property**: Whether the customer owns a property.
- **Children count**: The number of children the customer has.
- **Income**: The customer's annual income.
- **Employment status**: The customer's current employment status.
- **Education level**: The customer's highest level of education.
- **Marital status**: The customer's marital status.
- **Dwelling**: The type of dwelling the customer lives in.
- **Age**: The customer's age, calculated in years.
- **Employment length**: The length of the customer's current employment, adjusted to years.
- **Account age**: The age of the customer's account, also converted to years.
- **Is high risk**: The target column indicating whether the customer is classified as high-risk (binary).

### Class Imbalance

The dataset has a pronounced class imbalance, with high-risk cases being significantly underrepresented. Out of approximately 36,000 records, only around 600 are labeled as high-risk. This imbalance creates challenges for the model, as it tends to predict the majority class more accurately at the expense of the minority class.

## Methods

### Data Preprocessing

The dataset required extensive preprocessing, including:

- **Feature Selection:** Dropping irrelevant or redundant columns such as "Job title" and "Dwelling."
- **Encoding**: Encoding categorical variables (e.g., gender, car ownership) into numeric form.
- **Handling Time Data:** Converting time-related columns from days to years.

### Model Development

1. **Baseline Model**: A Random Forest Classifier was initially trained without addressing class imbalance. This model showed high overall accuracy but poor performance on the minority class (high-risk).
2. **Class Weight Adjustment**: The Random Forest Classifier was retrained with balanced class weights to give more importance to the minority class. This improved recall significantly but resulted in a trade-off with precision.
3. **Resampling Techniques**: The ADASYN (Adaptive Synthetic Sampling) method was used to oversample the minority class, leading to better recall but further reduction in precision.
4. **Balancing subsamples**: The Random Forest Classifier was retrained with balanced subsamples to ensure that each bootstrap sample was balanced. This resulted in a slight improvement from the second model, which balanced the class weights before splitting the samples.
5. **Balanced Random Forest**: A final model using the Balanced Random Forest Classifier was implemented, which attempts to balance the class distribution by adjusting weights in each bootstrap sample.

### Model Evaluation

- **Precision**: The final model achieved a precision of **0.04** after resampling, indicating that  only 4% of the instances classified as high-risk were actually high-risk.
- **Recall**: The recall improved significantly to **0.6**, meaning 60% of the actual high-risk cases were correctly identified by the model.
- **F1-Score**: The F1-score was **0.08**, reflecting the balance between precision and recall.
- **Accuracy**: The overall accuracy of the model was **0.74**, which is still not indicative of true performance due to the class imbalance.

## Results

- **Class Imbalance Impact**: The significant class imbalance in the data led to initial models being biased towards predicting low-risk cases. The use of class weight adjustment and resampling techniques improved the model's ability to identify high-risk cases, though at the cost of precision.
- **Final Model Performance**: The Balanced Random Forest Classifier provided the highest recall, but witnessed a blow to precision. The third model, with an f1 score of 0.25 had the best balance between recall and precision, highlighting the importance of addressing class imbalance in predictive modeling.

## Conclusion

This project demonstrates the challenges of predicting credit card risk in the presence of severe class imbalance. By applying techniques such as class weight adjustment and resampling, the final model was able to improve its ability to identify high-risk customers, though precision remains a challenge. This work underscores the importance of carefully handling class imbalance to avoid misleadingly high accuracy scores and to ensure that the minority class is effectively captured.
