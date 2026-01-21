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



📏 Evaluation Metrics and XGBoost Performance


To evaluate model performance, we used RMSE and MAE, two standard regression metrics. RMSE emphasizes larger prediction errors and is particularly important for identifying poor performance on high-priced vehicles, while MAE represents the average absolute prediction error and is easier to interpret in business terms.
Among all tested models, XGBoost achieved the lowest RMSE and MAE and the highest R², indicating the strongest overall predictive accuracy and the best fit to the data. This suggests that XGBoost was more effective at capturing complex, non-linear relationships between vehicle characteristics and price compared to linear and standard ensemble models. As a result, XGBoost was selected as the final model for analyzing price drivers and generating business insights.


✅ Interpretation:

XGBoost achieves the lowest RMSE and MAE, meaning it consistently predicts prices with the smallest error margin.
Gradient Boosting performs reasonably well but with ~20% higher error.
Linear, Ridge, and Lasso models are less effective at capturing non-linear depreciation and brand effects.


