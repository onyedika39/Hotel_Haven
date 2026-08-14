Hotel Haven: Booking Cancellation Prediction

An end-to-end machine-learning project that analyzes hotel reservations and predicts whether a booking will be cancelled. The analysis is designed to help Hotel Haven identify at-risk bookings early and take practical retention actions.

## Business problem

Booking cancellations reduce revenue certainty and make room, staffing, and inventory planning harder. This project uses historical booking information to identify the drivers of cancellation and compare classification models for flagging higher-risk reservations.

## Project highlights

- Analyzed **36,285** booking records across 17 original fields.
- Cleaned dates, removed the identifier field, and retained **36,248** usable observations.
- Engineered stay length, party size, price-per-night, and reservation-date features.
- Compared Logistic Regression, Random Forest, and XGBoost using an 80/20 train-test split.
- Best recorded test result: **Random Forest — 89.86% accuracy**.

## Key findings

- Longer lead times are associated with more cancellations.
- Higher-priced bookings show a greater tendency to cancel.
- Bookings with special requests are less likely to be cancelled.
- Cancellation behavior varies by market segment; online bookings warrant particular attention.
- Repeat customers appear less likely to cancel, making loyalty initiatives a useful retention lever.

## Results

| Model | Test accuracy |
| --- | ---: |
| Logistic Regression | 80.47% |
| Random Forest | **89.86%** |
| XGBoost | 89.12% |

Accuracy is a useful first comparison, but a production decision should also consider precision, recall, false-positive cost, and false-negative cost.

## Repository structure

```text
Hotel_Haven/
├── Bookings.ipynb                 # Analysis, visualizations, and model comparison
├── booking - booking.csv          # Source dataset
├── images/                        # Exported charts and model visuals
├── README.md                      # Project overview (this file)
├── requirements.txt               # Python dependencies
└── .gitignore                     # Files excluded from Git
```

## Getting started

1. Clone the repository.
2. Create and activate a virtual environment.
3. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Launch Jupyter Notebook:

   ```bash
   jupyter notebook
   ```

5. Open `Bookings.ipynb` and run the cells from top to bottom. Keep the CSV file in the same directory as the notebook.

## Methods

### Data preparation

- Removed `Booking_ID`, which is an identifier rather than a predictive feature.
- Parsed reservation dates and extracted month, year, and day-of-week features.
- Removed 37 rows with invalid reservation dates.
- Label-encoded categorical features for the modeling workflow.

### Feature engineering

- `total_nights` = weekend nights + week nights
- `total_guests` = adults + children
- `price_per_night` = average price / (total nights + 1)

### Models evaluated

- Logistic Regression (baseline)
- Random Forest Classifier
- XGBoost Classifier

## Business recommendations

1. Proactively confirm reservations with long lead times.
2. Test retention offers for higher-priced, high-risk bookings.
3. Encourage special requests during booking to increase customer commitment.
4. Focus outreach and cancellation-policy experiments on higher-risk market segments.
5. Use loyalty benefits to reduce cancellation risk among returning customers.

## Limitations and next steps

- Use one-hot encoding or a scikit-learn pipeline instead of ordinal label encoding for nominal categories.
- Add a stratified train-test split and cross-validation.
- Report ROC-AUC, precision, recall, F1, and a cost-sensitive threshold—not only accuracy.
- Save the chosen model and preprocessing pipeline for repeatable predictions.
- Add a data dictionary and document the dataset source/license before presenting this as production-ready work.

## Visuals

The exported PNG files are worth including in an `images/` folder. They make the repository easier to scan and allow recruiters to understand the work without running the notebook. Use only the most decision-relevant visuals in the README, such as the model comparison, feature importance, and ROC curve.

## Author

**Michael Onyedika**  
Data analytics and machine-learning portfolio project
