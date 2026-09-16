# Responsible Data Card

## Project: Customer Churn Prediction

## 1. Dataset Purpose

The purpose of this dataset is to explore whether customer information can be used to predict customer churn.

In this project, churn means that a customer has left or stopped using the service.

The dataset can support an ML model that identifies customers who may be at risk of churn. The prediction should be treated as information for a human to review rather than as an automatic decision.

The model should not be used to automatically cancel an account, deny a service, increase a customer's price, or make other important decisions about a customer.

---

## 2. Provenance and Permission

The dataset was provided as the training dataset for this project.

The CSV itself does not contain information about the original data collection process, the identity of the original data collector, customer consent, or licensing restrictions.

Because this information is not available in the supplied dataset, I cannot confirm these details.

For a real-world application, the source, permission to use the data, privacy requirements, and licensing conditions would need to be checked before using the data.

---

## 3. Population and Representation

The dataset contains 12 customer records.

The current data includes:

* 7 customers who did not churn
* 5 customers who churned

While checking the dataset, I noticed that the number of records is very small.

This is an important limitation. Twelve customers are not enough to represent a large real-world customer population.

The dataset also does not provide enough documented information about different customer groups to determine whether all groups are properly represented.

Because of this, the results of the ML model should be treated as an educational demonstration and not as evidence of real-world performance.

---

## 4. Features and Target

The dataset contains the following columns:

| Feature             | Meaning                                                  | Planned use             |
| ------------------- | -------------------------------------------------------- | ----------------------- |
| `customer_id`       | Identifier for the customer                              | Not used for prediction |
| `tenure_months`     | Number of months the customer has been using the service | Model feature           |
| `support_tickets`   | Number of support tickets raised by the customer         | Model feature           |
| `monthly_spend_inr` | Customer's monthly spending                              | Model feature           |
| `last_login_days`   | Number of days since the customer's last login           | Model feature           |
| `plan_type`         | Customer's service plan                                  | Model feature           |
| `churned`           | Whether the customer churned                             | Target                  |

### Target

The target variable is `churned`.

* `0` means the customer did not churn.
* `1` means the customer churned.

### Identifier Check

I decided not to use `customer_id` as a model feature.

An ID identifies a customer but does not describe useful customer behavior. Including it could allow the model to learn meaningless patterns from the identifier.

### Leakage Risk

One possible problem is **data leakage**.

Data leakage happens when information that would not have been available at prediction time is accidentally given to the model.

For example, if information created after a customer had already left the service was used to predict churn, the model could appear more accurate than it really is.

For a real system, only information available before the prediction should be used.

---

## 5. Quality Checks

Before building the model, I checked the basic structure of the dataset.

### Current observations

* Total records: 12
* Total columns: 7
* Missing values: None identified
* Duplicate customer records: None identified
* Churned customers: 5
* Non-churned customers: 7

### Checks to perform in the notebook

The notebook will also check:

* Data types
* Missing values
* Duplicate records
* Unusual values or outliers
* Class balance
* Train/test separation
* Possible data leakage

### Small Dataset Observation

One of the first things I noticed about the dataset was its very small size.

This means that even a small change in the data could have a large effect on the model's results.

Because of this, model performance will need to be interpreted carefully.

---

## 6. Possible Data Risks

### Privacy Risk

Customer information could be exposed or used for a purpose that was not intended.

**Safeguard:** Only use the information needed for the project and avoid exposing unnecessary customer identifiers.

### Representation Risk

The dataset contains only 12 records, so it may not represent the wider customer population.

**Safeguard:** A real system would require a much larger and more representative dataset.

### Data Leakage Risk

Information from after the prediction point could accidentally be used.

**Safeguard:** Check that every feature would have been available when the prediction was made.

### Misuse Risk

Someone could treat the model's prediction as a fact instead of a prediction.

**Safeguard:** Use the model as decision support and require human review.

---

## 7. False-Positive Risk

A false positive occurs when the model predicts that a customer will churn but the customer does not actually churn.

For example:

> Prediction: Customer will churn
> Actual result: Customer stays

The company could spend unnecessary time or resources trying to retain that customer.

The model should therefore not automatically trigger an action.

---

## 8. False-Negative Risk

A false negative occurs when the model predicts that a customer will not churn but the customer actually churns.

For example:

> Prediction: Customer will not churn
> Actual result: Customer leaves

This could mean that the company misses an opportunity to understand or support the customer.

For this reason, recall will be considered during model evaluation.

---

## 9. Human Review

The ML model should not be the final decision-maker.

If the model identifies a customer as potentially at risk, a human should review the prediction before deciding whether any action is appropriate.

This is particularly important for this project because the dataset is very small.

---

## 10. Abstention

The model should have a way to avoid making a recommendation when the available information is unreliable or when the prediction is not sufficiently confident.

Instead of forcing a prediction in every situation, the case can be sent for human review.

---

## 11. Intended Evaluation

Before deciding whether the ML model is useful, it will be compared with a simple non-ML baseline.

### Baseline

The baseline will predict the majority class for every customer.

This gives us a simple reference point.

### Model Metrics

The ML model will be evaluated using:

* Accuracy
* Precision
* Recall
* F1-score
* Confusion matrix

Accuracy will not be considered by itself because false positives and false negatives have different consequences.

### Error Analysis

After testing the model, incorrect predictions will be examined.

The purpose is to understand where the model makes mistakes rather than only looking at one final score.

### Calibration

If the model produces probability estimates, those probabilities should be checked for calibration before being used to support real decisions.

### Fairness

The current dataset does not provide enough documented information about demographic or other relevant groups to perform a meaningful fairness analysis.

If appropriate group information were available in a properly permitted real-world dataset, model performance could be compared across groups.

---

## 12. Monitoring

If the model were used in a real application, it should be monitored over time.

The monitoring process could include:

* Model performance
* False positives
* False negatives
* Data quality
* Changes in customer behavior
* Performance across relevant groups

If the data or customer behavior changes significantly, the model may need to be reviewed or retrained.

---

## 13. Rollback

There should be a way to stop using the ML model if serious problems are discovered.

For example, if the model starts producing unreliable predictions or the input data becomes incorrect, the ML system could be disabled.

The organization could then return to the non-ML baseline while the problem is investigated.

---

## 14. Current Limitations

The biggest limitation of this project is the size of the dataset.

There are only 12 customer records.

Because of this, the model's results may be unstable and should not be treated as reliable evidence for real-world deployment.

The dataset also does not provide detailed information about its original collection process, consent, or representation of different customer populations.

A real-world system would require more data, proper documentation, appropriate permissions, and further testing.

---

## 15. What I Will Check During the Project

As I continue building the project, I will document useful observations instead of only recording the final result.

For example:

* What I found during data inspection
* Whether the first baseline performs well
* Whether the ML model improves on the baseline
* Which predictions are incorrect
* Whether changing the model changes the results
* Any problems I encounter while preparing the data
* What I changed to solve those problems

This will help show the actual development process of the project.

---

## Conclusion

The dataset can be used to demonstrate the process of building a customer churn prediction model.

However, the current dataset is very small, so the project should be treated as an educational ML exercise.

The goal is not only to train a model but also to understand the data, compare the model with a simple baseline, identify possible errors and risks, and make sure that human review and safety measures are considered.
