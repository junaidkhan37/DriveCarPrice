# DriveCarPrice

📌 Overview

This project analyzes a large dataset of used vehicles to identify the key drivers of resale price and build predictive models for dealership stakeholders.
The goal is to fine-tune inventory strategy and pricing using data-driven insights.

What Drives the Price of a Car?



Dataset summary

This dataset contains listings for used vehicles and is structured to support price prediction and resale-value analysis. The target variable is price (sale price), and the table includes both numeric and categorical features that capture vehicle attributes, condition, and location.

Key features
year — model year (used to derive vehicle age)
price — sale price (target)
odometer / mileage — total miles driven (numeric)
manufacturer — vehicle make (e.g., Toyota, Ford)
model / type — model name and vehicle type (e.g., sedan, SUV, truck)
condition — seller-reported condition (ordinal: poor → like new)
cylinders — engine cylinder count (numeric/ordinal)
fuel — fuel type (gas, diesel, hybrid, electric)
transmission — transmission type (automatic, manual)
drive — drivetrain (FWD, RWD, AWD)
state / location — geographic location of the listing
additional fields — may include color, title status, VIN presence, posting date, and seller type
The dataset requires standard preprocessing: derive age from year, handle missing values and outliers, encode categorical variables (one‑hot or ordinal where appropriate), and consider log-transforming price for modeling stability.

Primary predictors observed: age, mileage, condition, and manufacturer — these drive most of the variance in resale price and are emphasized in the analysis.



📊 Summary of Findings

Best-performing model: XGBoost, with the lowest error (RMSE = 0.3384, R2 = 0.8323).
Key predictors of price:
Age: Steep depreciation in the first 5–7 years, then flattens.
Mileage: Strong negative effect, especially in the first 50k miles.
Condition: Step-wise premiums; “good” → “excellent” → “like new.”
Brand: Luxury brands (BMW, Mercedes, Lexus) retain higher value; mass-market brands (Toyota, Honda, Ford) show strong resale reliability.
Business impact:
Prioritize newer, low-mileage vehicles.
Invest in reconditioning when uplift > cost.
Adjust inventory mix by region and vehicle type (SUVs/trucks command higher resale).


🛠 Dealer-Facing Recommendations

Acquisition Strategy:

Prioritize newer, low-mileage vehicles.
Focus on brands with strong resale premiums.
Pricing Strategy:

Use mileage and age tiers to set discounts.
Apply condition premiums consistently to justify reconditioning costs.
Inventory Mix:

Stock more SUVs and trucks (higher average resale).
Adjust mix by region (e.g., trucks in Texas, hybrids in California).



📏 Evaluation Metrics

To assess model performance, we used two standard regression metrics:

RMSE (Root Mean Squared Error):
Measures the square root of the average squared differences between predicted and actual prices.

Penalizes larger errors more heavily.
Lower RMSE indicates better overall accuracy.
MAE (Mean Absolute Error):
Measures the average absolute differences between predicted and actual prices.

Easier to interpret (average dollar error).
Less sensitive to outliers compared to RMSE.
Why These Metrics?

RMSE highlights how well the model handles large deviations (important for luxury or high-value vehicles).
MAE provides a straightforward measure of the average prediction error in dollars, making it intuitive for dealership stakeholders.
📈 Model Comparison

Model	RMSE (Price, $)	MAE (Price, $)
XGBoost	4,746.60	2,828.19
GradientBoosting	5,809.49	3,550.30
Linear Regression	6,348.67	3,982.93
Ridge (alpha=10)	6,370.66	3,986.02
Lasso (alpha=0.001)	6,461.85	4,071.03
✅ XGBoost is the most accurate, reducing pricing error by ~$1,500 compared to linear models.

✅ Interpretation:

XGBoost achieves the lowest RMSE and MAE, meaning it consistently predicts prices with the smallest error margin.
Gradient Boosting performs reasonably well but with ~20% higher error.
Linear, Ridge, and Lasso models are less effective at capturing non-linear depreciation and brand effects.


📂 Project Organization

UsedCarPricePrediction/ │ ├── notebooks/ │ └── used_car_price_prediction.ipynb # Main Jupyter notebook with analysis & models │ ├── data/ │ └── vehicles.csv # Raw dataset (cleaned during preprocessing) │ ├── reports/ │ └── README.md # Project summary and findings │ └── requirements.txt # Python dependencies

├── data/
│ └── vehicles.csv # Source Data
│
├── Notebook/
│ └── WhatDrivesCarPrice.ipynb # Jupyter Notebook (analysis + visualizations)
│
├── README.md

No unnecessary files are included.
Directories and files are named clearly and placed in appropriate locations.


📓 Jupyter Notebook

The notebook WhatDrivesCarPrice.ipynb contains:

Clear headings and explanatory text.
Step-by-step workflow: preprocessing, model building, evaluation, and visualization.
