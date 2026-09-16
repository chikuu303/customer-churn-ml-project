# ML Problem-Framing Memo

## Project: Customer Churn Prediction

### 1. Decision

The purpose of this project is to predict which customers may be likely to leave a service.

The prediction can help a customer-support team identify customers who may need attention. The ML model will only provide a prediction. A human should review the prediction before taking any action.

The model should not automatically cancel accounts, deny services, or make important decisions about customers.

### 2. Prediction Target

The target that the model will predict is the `churned` column.

* `0` = customer did not churn
* `1` = customer churned

The other customer information will be used as input features to help the model make this prediction.

### 3. Unit of Observation

Each row in the dataset represents one customer.

The dataset contains information such as:

* `tenure_months`
* `support_tickets`
* `monthly_spend_inr`
* `last_login_days`
* `plan_type`

The `customer_id` is only an identifier, so it will not be used as a feature for training the model.

### 4. Action Window

The prediction should ideally be made before the customer leaves the service.

For a real-world system, a specific time period would need to be defined, such as predicting whether a customer will churn within the next 30 days.

The supplied dataset does not provide enough information to define an actual prediction period, so the action window will need to be confirmed before real-world use.

### 5. Non-ML Baseline

Before training a machine learning model, a simple baseline will be created.

The baseline will predict the majority class for every customer. This gives us a simple result to compare against the ML model.

If the ML model cannot perform better than this simple approach, then there may not be enough evidence that using ML is useful for this task.

### 6. Why Machine Learning May Be Useful

Customer churn may depend on several factors at the same time.

For example, a customer's length of membership, support tickets, spending, login activity, and plan type may contain useful information about churn.

Machine learning can combine these features and look for patterns in the existing data.

However, the current dataset is very small, so the model should be considered an educational experiment rather than a production-ready system.

### 7. False Positives and False Negatives

The model can make two important types of mistakes.

**False Positive:**
The model predicts that a customer will churn, but the customer does not actually churn.

This could result in unnecessary customer-retention efforts.

**False Negative:**
The model predicts that a customer will not churn, but the customer actually churns.

This could cause the company to miss an opportunity to provide appropriate support.

Because these errors have different consequences, the model will not be evaluated using accuracy alone.

### 8. Human Review

The model should be used as a decision-support tool rather than an automatic decision-maker.

When a customer is predicted to be at risk, a human should review the prediction and the available customer information before taking any action.

### 9. Abstention

The system should be able to avoid making a recommendation when there is not enough reliable information or when the model is not sufficiently confident.

Such cases can be sent for human review instead.

### 10. Monitoring

If the model were used in a real situation, its performance should be monitored regularly.

The following should be checked:

* Accuracy
* Precision
* Recall
* False positives
* False negatives
* Data quality
* Changes in customer behavior
* Performance across relevant groups

### 11. Rollback

If the model starts producing unreliable predictions or if there are serious problems with the data, the ML system should be stopped.

The organization can temporarily return to the non-ML baseline while the problem is investigated.

### 12. Main Limitation

The current dataset contains only 12 customer records.

This is a major limitation because such a small dataset cannot reliably represent a large customer population.

Therefore, any model results from this project should be treated as a demonstration of the machine learning process and not as proof that the model is ready for real-world use.

A larger and properly documented dataset would be needed for a real deployment.

## Summary

The goal of this project is to explore whether customer information can be used to predict churn.

I will first create a simple non-ML baseline, then train and evaluate a machine learning model. Along with model performance, I will also consider possible errors, risks, human review, monitoring, and rollback.

This approach allows the project to consider not only whether the model can make predictions, but also whether those predictions can be used responsibly.
aset contains only 12 records. Results from such a small dataset are highly uncertain and should not be interpreted as evidence that the model is ready for production use.

A larger and more representative dataset would be required for real-world deployment.
