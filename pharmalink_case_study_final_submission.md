# Pharmalink – B2B Medicine Distribution Platform
## Machine Learning Case Study Submission

---

## 1. Problem Identification

The problem is a **supervised learning task** because it uses labeled historical data to predict the target variable `will_churn_next_30d`. It is a **classification problem** since the output is categorical in nature, and specifically a **binary classification task** as the target variable has two classes: churn (1) and not churn (0).

---

## 2. Mapping to the 5-Stage ML Pipeline

### Data Collection
Collect `last_order_date`, `order_frequency_60d`, and `avg_order_value` from the order management system.

### Data Preprocessing
Convert `last_order_date` to datetime format and create a new feature `days_since_last_order` to capture recency of transactions.

### Model Training
Train a Random Forest model using features like `order_frequency_60d`, `credit_utilization_ratio`, and `days_since_last_order` to predict `will_churn_next_30d`.

### Model Evaluation
Evaluate the model using Recall, Precision, and F1-score, with a focus on maximizing Recall.

### Deployment
Deploy the model to identify pharmacies likely to churn and trigger intervention actions such as outreach calls.

---

## 3. Evaluation Strategy

The company should prioritize **Recall** because missing a churn-prone pharmacy (false negative) leads to significant revenue loss, while incorrectly identifying a non-churner (false positive) only results in a minor operational cost.

This represents a trade-off where the company accepts more false positives in order to minimize the risk of losing high-value customers.

---

## 4. Advanced Thinking

Using a single global model can lead to biased predictions because it learns average behavior across all tiers, causing it to misclassify Tier-2 and Tier-3 pharmacies whose ordering patterns differ significantly from Tier-1.

I would use **interaction features** because they allow a single model to capture differences in behavior across city tiers without the complexity of maintaining multiple models. This approach is more scalable and enables the model to learn how features like `days_since_last_order` behave differently for Tier-1 versus Tier-3 pharmacies.

Interaction features like `days_since_last_order * city_tier` help the model understand how the impact of recency on churn varies across different city tiers.

---

## Conclusion

This approach ensures a scalable, business-aware machine learning solution that prioritizes minimizing revenue loss while accounting for behavioral differences across pharmacy segments.

