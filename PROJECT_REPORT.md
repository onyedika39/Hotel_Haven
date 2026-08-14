# Hotel Haven Booking Cancellation Prediction: Project Report

## Executive summary

This project evaluates whether historical hotel-booking data can be used to identify reservations at risk of cancellation. After cleaning 36,285 records and engineering reservation-level features, three classification models were compared on a held-out test set. Random Forest produced the highest recorded accuracy at 89.86%.

The analysis indicates that lead time, average price, special requests, market segment, and repeat-customer behavior are meaningful signals for cancellation risk. These findings can support earlier confirmation outreach, targeted retention offers, and more dependable operational planning.

## Objective

Predict a booking's cancellation status and identify the factors that operational teams can use to reduce cancellations.

## Data and preparation

The source data contains 36,285 hotel reservations and 17 fields. The workflow removed the booking identifier, transformed reservation dates into calendar features, removed 37 records with invalid dates, and produced a modeling dataset of 36,248 rows.

Engineered features include total nights, total guests, price per night, reservation month, reservation year, and reservation day of week.

## Modeling approach

An 80/20 train-test split was used. Logistic Regression served as the baseline, while Random Forest and XGBoost were evaluated as nonlinear ensemble approaches.

| Model | Test accuracy |
| --- | ---: |
| Logistic Regression | 80.47% |
| Random Forest | **89.86%** |
| XGBoost | 89.12% |

The recorded results favor Random Forest on accuracy. The notebook should be updated before claiming XGBoost as the selected model, because its measured accuracy is lower in the saved output.

## Insights and recommendations

- Long lead-time reservations should receive early confirmation messages or carefully tested commitment incentives.
- Higher-priced reservations may benefit from targeted value reinforcement or flexible retention offers.
- Encourage special requests at checkout; the analysis indicates they are associated with lower cancellation rates.
- Prioritize high-risk market segments for proactive outreach.
- Strengthen loyalty programs, since repeat-booking behavior is associated with lower cancellation risk.

## Professional next steps

1. Replace label encoding of nominal fields with one-hot encoding inside a reproducible pipeline.
2. Add stratified cross-validation and compare ROC-AUC, precision, recall, F1, and calibration.
3. Select a prediction threshold using the business cost of empty rooms versus unnecessary outreach.
4. Save the trained pipeline and document how new booking records are scored.
5. Add data provenance, a data dictionary, and a short reproducibility note.
