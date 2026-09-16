# ML Problem-Framing Memo

## Project Title

Customer Churn Prediction Using Machine Learning

## 1. Decision

The project aims to identify customers who may be at risk of leaving a service. The prediction can be used to help a customer-support or retention team decide which customers may need human review and attention.

The model should not automatically cancel accounts, deny services, or make other significant decisions about customers.

## 2. Prediction Target

The prediction target is `churned`.

* `0` = customer did not churn
* `1` = customer churned

## 3. Unit of Observation

Each row in the dataset represents one customer.

## 4. Prediction Time / Action Window

For a real-world system, the organization should define a future prediction period, such as whether a customer will churn within the next 30 days.

The supplied dataset does not document a specific future prediction window, so this is a limitation of the current project.

## 5. Available Data

The dataset contains information including:

* Customer tenure
* Number of support tickets
* Monthly spending
* Days since last login
* Plan type
* Churn outcome

`customer_id` is an identifier and should not be used as a predictive feature.

## 6. Why Consider Machine Learning?

Machine learning may be useful because several customer characteristics can be considered together to identify patterns associated with churn.

However, the supplied dataset is very small, containing only 12 customer records. Therefore, this project demonstrates the ML workflow but cannot establish reliable real-world predictive performance.

## 7. Non-ML Baseline

Before using machine learning, a simple baseline will be created.

The baseline will predict the majority class for every customer. This provides a reference point for determining whether the ML model provides useful predictive information.

## 8. Costs of Errors

### False Positive

A customer is predicted to churn but does not actually churn.

Possible consequence: the company may spend unnecessary time or resources contacting the customer.

### False Negative

A customer is predicted not to churn but actually churns.

Possible consequence: the company may miss an opportunity to provide appropriate support.

Because false negatives can mean missed retention opportunities, recall will be considered alongside other evaluation measures.

## 9. Human Review

Model predictions should be reviewed by a human before any customer intervention.

The model should provide decision support rather than automatically making important decisions about customers.

## 10. Abstention

If the model has insufficient confidence or the available data is outside the conditions used during development, the system should avoid making an automatic recommendation and send the case for human review.

## 11. Monitoring

A real deployment should monitor:

* Prediction performance
* False positives
* False negatives
* Data quality
* Changes in customer behavior
* Performance across relevant customer groups

## 12. Rollback

If monitoring identifies serious performance or data-quality problems, the ML system should be disabled and the organization should return to the established non-ML process until the issue is investigated.

## 13. Project Limitation

The current dataset contains only 12 records. Results from such a small dataset are highly uncertain and should not be interpreted as evidence that the model is ready for production use.

A larger and more representative dataset would be required for real-world deployment.
