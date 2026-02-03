# Hotel Booking Cancellation Prediction


## Overview
This project predicts hotel booking cancellations for Resort and City hotels in Portugal (2015–2017).  
The workflow includes:

- Data cleaning and preprocessing  
- Exploratory Data Analysis (EDA)  
- Feature engineering  
- Training a Decision Tree / Random Forest model to predict cancellations  

The main goal is to identify key factors influencing cancellations and achieve a predictive accuracy of **>70%**.

---

## Dataset
- **Source:** `hotel_bookings.csv`  
- **Features include:** hotel type, lead time, deposit type, customer type, market segment, number of guests, booking agent, meal type, room type, and more.  
- **Target variable:** `is_canceled` (0 = not cancelled, 1 = cancelled)

---

## Data Preprocessing
- Dropped irrelevant or leaky columns (e.g., `company`, `reservation_status_date`)  
- Handled missing values (`children` → 0, `country` → 'Unknown')  
- Converted data types (`hotel` → categorical, `is_canceled` → integer)  
- Detected and analyzed outliers using boxplots  
- Encoded categorical features:
  - **Label Encoding:** low-cardinality columns  
  - **One-Hot Encoding:** high-cardinality columns  
- Scaled numeric features (excluding target) for uniformity  

---

## Exploratory Data Analysis (EDA)
- Calculated cancellation rates by hotel type  
- Identified most frequently ordered meal types  
- Analyzed returning vs first-time guests  
- Determined the most booked room types  
- Explored correlations between room types and cancellations  

**Key insights:**

- **City Hotels** have higher cancellation rates (~42%) than Resort Hotels (~28%)  
- Guests overwhelmingly choose **Bed & Breakfast (BB)** packages  
- Majority of guests are first-time visitors, indicating opportunities for loyalty programs  
- Room Type A is the most booked, likely representing standard offerings  
- Certain room types and market segments exhibit higher cancellation risk

---

## Feature Engineering
- Created new features:
  - `total_nights` = weekday + weekend nights  
  - `total_guests` = adults + children + babies  
- Binned `lead_time` into categorical ranges (`<1 month`, `1–3 months`, etc.)  
- Applied encoding to categorical variables  
- Dropped leaky columns to prevent data leakage

---

## Model Training
- **Algorithm:** Decision Tree Classifier  
- **Train/Test split:** 70% training, 30% testing (stratified on `is_canceled`)  
- **Hyperparameters:** `criterion='entropy'`, `max_depth=10`  
- **Evaluation metrics:** Accuracy, Confusion Matrix, Precision, Recall, F1-score  

**Result:** Model achieved **>70% accuracy**, meeting project requirements.

---

## Feature Importance
The most influential factors in predicting cancellations:

1. **Deposit Type** – Non-refundable bookings are far less likely to cancel  
2. **Market Segment** – Online travel agency bookings have higher cancellations  
3. **Lead Time** – Longer booking periods increase likelihood of cancellation  
4. **Agent** – Certain booking agents show higher cancellations due to group or corporate bookings  

**Business Insight:**  
Hotels can use these insights to optimize pricing strategies, deposit policies, and room availability forecasting.

---

## Conclusion
- A complete data-driven workflow successfully predicted hotel booking cancellations  
- Key actionable insights were extracted to help hotel management reduce cancellations  
- Future improvements:
  - Explore ensemble models (e.g., Random Forest, XGBoost) for higher accuracy  
  - Incorporate seasonal trends and external factors  
  - Leverage customer feedback for enhanced predictions

---

## How to Run
1. Clone the repository:

```bash
git clone https://github.com/Krishnawadiwala/hotel-booking-cancellation-prediction.git
