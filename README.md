# Zillow-House-Price-Prediction-iBuyer-Profitability

# Project Description
This project evaluates how well house price prediction models translate into real-world profitability in an iBuyer-style business. We combined supervised learning with a simulated offer-acceptance framework to show that strong predictive accuracy does not necessarily lead to positive financial outcomes.

# Data Modeling

We trained and compared several supervised learning models, including Multilayer Perceptron (MLP) neural networks and ensemble tree-based methods (XGBoost, CatBoost, AdaBoost). Model performance was evaluated using Median Error Rate (MER) and RMSE, with K-fold cross-validation and regularization techniques (dropout, norm regularization, early stopping) applied to ensure stable generalization.

The best-performing MLP achieved a validation MER of approximately 0.09, while ensemble models delivered competitive RMSE results, confirming strong predictive capability across multiple model families.

1. Base MLP	- 2 layers (256, 128)	: Mild overfitting, stable validation
2. Deeper MLP	- 4 layers:	Similar validation, slower convergence
3. +Norm Reg + Early Stop	Lasso + early stopping:	Stable but noisy validation
4. +Dropout + Norm Reg	Dropout + regularization: Best generalization

# Data Predictions

Predicted prices were used to simulate an iBuyer “make-an-offer” process. Offers were evaluated based on whether sellers accepted them, and realized profit was calculated as the difference between resale price and acquisition cost. This simulation revealed that accepted offers tended to occur when predicted prices overestimated true market value, introducing a selection bias against the buyer.
To benchmark neural networks against ensemble methods, we evaluated several tree-based models using cross-validation.

1. XGBoost: RMSE ≈ 115,688
2. CatBoost:	RMSE ≈ 112,468
3. AdaBoost:	RMSE ≈ 224,422
4. K-Fold XGBoost:	Avg RMSE ≈ 118,878

Tree-based models performed competitively, reinforcing that multiple model families can achieve strong predictive accuracy in this setting.

# Business Implications

Predicted prices were used to simulate automated offers in an iBuyer framework. Profit was calculated as the difference between resale price and acquisition cost, conditional on seller acceptance. Despite strong validation accuracy, mean profit was negative. Accepted offers disproportionately occurred when predicted prices overestimated true value, revealing a selection effect: sellers are more likely to accept offers that are unfavorable to the buyer. 
This result highlights a critical business lesson:
**Accurate predictions do not guarantee profitability when decision rules interact with human behavior.**
