## Model Summary
The model is a Random Forest Classifier integrated into a scikit-learn Pipeline. Random Forests are highly effective for this type of data because they are scale-invariant, meaning they do not require features to be scaled to perform correctly.

Final Accuracy: ~81.56%

Key Predictors: Sex, Fare, and Age

Best Parameters:

n_estimators: 100

max_depth: 20

min_samples_split: 10

## Data Preprocessing
To ensure clean data and prevent data leakage, a ColumnTransformer was used to route features to specific pipelines:

Numeric Pipeline: Handles missing values (imputation) and scaling (though scaling is optional for RF, it is included for pipeline consistency).

Categorical Pipeline: Handles missing text values and converts categories into numbers using encoding (e.g., One-Hot Encoding).

## Hyperparameter Tuning
We used GridSearchCV to find the optimal balance between accuracy and overfitting. The search explored:

n_estimators: The number of trees in the forest. More trees generally increase stability.

max_depth: The maximum levels of each tree. A depth of 20 allows the model to capture complex patterns in continuous data like Age and Fare.

min_samples_split: The minimum number of samples required to split a node. Setting this to 10 acts as a "safety net" to prevent the model from over-fitting on small, noisy groups of data.

## Performance Metrics
The model was evaluated using a Classification Report to understand its strengths and weaknesses:

High Precision (0.82): When the model predicts someone survived, it is correct 82% of the time.

Recall Disparity: The model is better at identifying those who perished (Recall 0.89) than those who survived (Recall 0.72).

F1-Score: 0.85 for non-survivors and 0.76 for survivors, indicating a solid overall balance.
