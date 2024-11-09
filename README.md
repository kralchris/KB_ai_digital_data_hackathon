# KB AI Digital Data Hackathon
<i>Unlocking digital data potential</i>

![image](https://github.com/user-attachments/assets/cf0ef487-a404-4067-8a0b-b6fe4e9142d1)

## SRE BOT (Segmentation Recommendation Engine)
Customer Segmentation and Recommendation App

## Project Overview
This project was created as part of a hackathon challenge aimed at developing a machine learning model to identify customer behavior patterns and predict product purchase likelihood. The goal is to enable **more efficient and targeted marketing campaigns** by recognizing patterns in customer interactions.

[**View the Presentation**](https://skippy8.github.io/kbaihack/ppt/)

### Objective
- Detect customer behavior patterns and predict the likelihood of product purchases to enhance the effectiveness of marketing campaigns.
- Rank clients for individual KB products by the probability of purchase, allowing marketing campaigns to focus on clients with the highest likelihood of conversion.

## Input Data

The dataset consists of several tables capturing various customer interactions and transaction details across multiple platforms and channels. Key features include:

1. **Web**: Actions on the KB.cz website (3 tables by month; each with over 5 million rows).
2. **APP**: Interactions with the KB+ Mobile Banking app (4 tables; approximately 15 million rows per table).
3. **IB**: KB+ Internet Banking usage (1 table for three months, 8 million rows).
4. **Prodeje**: Sales records (1 table for three months, 0.1 million rows).
5. **Camp**: Records from direct marketing campaigns (1 table for three months, 1.6 million rows).

Each table uses `identity_id_hash` as the key to link records across datasets, representing client IDs. Web data includes both clients and non-clients, where non-clients are identified by `user_id` (cookies).

## Approach

1. **Data Loading and Cleaning**:
   - Merged datasets on `identity_id_hash`.
   - Cleaned data by removing columns with all missing values and filling missing values appropriately.

2. **Feature Engineering**:
   - Created new features like `avg_session_duration`, `interaction_count`, and `campaign_engagement`.
   - Defined the target variable, `purchase`, based on agreement status.

3. **Model Training**:
   - Used a `RandomForestClassifier` with hyperparameter tuning via `GridSearchCV` to optimize for ROC-AUC.
   - Validated model performance using cross-validation and test set evaluation.

4. **Customer Segmentation**:
   - Segmented customers based on purchase probability:
     - **High Value Engaged**: Probability > 0.8
     - **Potential Upsell**: 0.5 < Probability ≤ 0.8
     - **Nurture and Educate**: 0.3 < Probability ≤ 0.5
     - **Low Engagement and Awareness**: Probability ≤ 0.3
   - Provided tailored recommendations for each segment to guide marketing strategies.

## Results
The final model achieved high accuracy in predicting purchase probability, allowing for effective customer segmentation and targeted recommendations. This approach supports KB's goal of directing marketing efforts towards clients most likely to engage with and purchase their products.
### Accuracy
![image](https://github.com/user-attachments/assets/8be3c94a-82e6-483b-b7b2-32208169c136)
### Model output
![image](https://github.com/user-attachments/assets/56082e3a-e3c4-497d-accb-1de1d3f10490)

## Our team: Prazska Smetanka
![IMG_0986](https://github.com/user-attachments/assets/f62d1221-d6ca-4ef2-8df2-e47e885279bd)
