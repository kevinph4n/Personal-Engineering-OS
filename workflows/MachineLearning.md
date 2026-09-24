# **I/ Data**
## **1/ Load Data & EDA**
- libraries: pandas, matplotlib, seaborn
- commonly used functions:
```
read data: df = pd.read_csv('data.csv')

overview: df.head(), df.info(), df.describe()

missing values: df.isnull().sum()
```
---
## **2/ Data Preprocessing & Cleaning**
- libraries: sklearn.preprocessing, sklearn.impute
- common used functions:
```
missing values: SimpleImputer(strategy='mean')

encode categorical data into numerical formats: LabelEncoder(), OneHotEncoder()

normalize/standardize data scales (crucial for models like SVM, KNN, or Neural Networks): StandardScaler() or MinMaxScaler()
```
- Integration Point: Your teammate must finalize and hand over these two crucial variables to you:

- X: The features (independent variables used for prediction).

- y: The target (the dependent variable you want to predict).
---

# **II/ Model Training & Optimization**:
## **1/ Train/Test Split**
```
from sklearn.model_selection import train_test_split
# Split data: 80% for training, 20% for testing
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
```
---
## **2/ Initialize & Train the Model**
Depending on whether your problem is Classification or Regression, you choose the appropriate algorithm. Below is an example using Random Forest (a robust algorithm that is less prone to overfitting)
```
from sklearn.ensemble import RandomForestClassifier # Or RandomForestRegressor for continuous numerical predictions

# 1. Initialize the model (you can pre-set some hyperparameters here)
model = RandomForestClassifier(n_estimators=100, max_depth=10, random_state=42)

# 2. Train the model (Learn from the training data)
model.fit(X_train, y_train)
```
---

## **3/ Model Evaluation**
- You will use `sklearn.metrics` to calculate the metrics and `seaborn` to visualize the Confusion Matrix (which looks great in project presentations).
```
from sklearn.metrics import accuracy_score, f1_score, confusion_matrix, classification_report
import seaborn as sns
import matplotlib.pyplot as plt

# Make predictions on the test set
y_pred = model.predict(X_test)

# --- 1. Calculate F1-Score ---
# Use average='binary' for 2 classes. If you have multiple classes (e.g., A, B, C), use average='weighted'
f1 = f1_score(y_test, y_pred, average='binary') 
print(f"F1-Score: {f1:.4f}")

# --- 2. Generate & Plot Confusion Matrix ---
cm = confusion_matrix(y_test, y_pred)
print("Raw Confusion Matrix:\n", cm)

# Plotting the matrix for a visual report
plt.figure(figsize=(6,4))
sns.heatmap(cm, annot=True, fmt='d', cmap='Blues', 
            xticklabels=['Predicted Negative', 'Predicted Positive'], 
            yticklabels=['Actual Negative', 'Actual Positive'])
plt.title('Model Confusion Matrix')
plt.xlabel('Prediction')
plt.ylabel('Actual Truth')
plt.show()

# You can still keep the classification report for a full summary
print("\nFull Classification Report:\n", classification_report(y_test, y_pred))
```
---

## **4/ How to Evaluate the Model Using These Two Metrics**
## **Confusion Matrix**
- The Confusion Matrix: Finding where the model is failing. A Confusion Matrix does not just give you a single score; it breaks down your model's predictions into four specific categories so you can see exactly what kind of mistakes it is making.

- Assuming a binary classification (e.g., predicting if a customer will buy a product or not):

- True Positives (TP - Bottom Right): The model predicted "Yes", and the actual answer was "Yes". (Correct)

- True Negatives (TN - Top Left): The model predicted "No", and the actual answer was "No". (Correct)

- False Positives (FP - Top Right / Type I Error): The model predicted "Yes", but the actual answer was "No". (Wrong - e.g., The model predicted a customer would buy, but they didn't).

- False Negatives (FN - Bottom Left / Type II Error): The model predicted "No", but the actual answer was "Yes". (Wrong - e.g., The model predicted the customer wouldn't buy, but they actually did).

- How to evaluate it: You want the numbers on the main diagonal (Top-Left and Bottom-Right) to be as high as possible. You want the numbers on the off-diagonal (Top-Right and Bottom-Left) to be as close to zero as possible.If your FP is very high, your model is too "trigger-happy" (guessing Yes too often). If your FN is very high, your model is too conservative (missing out on actual positive cases).

## **The F1-Score: The ultimate balance metric**
- Accuracy is often a misleading metric, especially if your dataset is imbalanced. For example, if 99% of your emails are normal and 1% is spam, a terrible model that simply predicts "Normal" every single time will still achieve 99% accuracy, but it is completely useless at catching spam. The F1-Score fixes this by combining two other metrics into one single score:

- Precision: Out of all the times the model predicted "Yes", how many were actually correct?

- Recall: Out of all the actual "Yes" cases in the dataset, how many did the model successfully find?

- How to evaluate it: The F1-Score ranges from 0.0 to 1.0 (or 0% to 100%). It will only give a high score if both Precision and Recall are high. 
- 0.90 - 1.00: Excellent model. It rarely misses positive cases and rarely makes false positive claims.

- 0.70 - 0.89: Good model. This is a very realistic and acceptable range for most real-world ML projects.

- 0.50 - 0.69: Mediocre model. It is making a significant amount of mistakes and you likely need to ask your teammate to extract better features from the data, or you need to tune your hyperparameters.

- < 0.50: Poor model. It is performing barely better than random guessing.
---

## **5/ Hyperparameter Tuning**
- To turn a "good" model into an "excellent" one, you need to tweak its internal parameters. Instead of guessing manually, use automated search over specified parameter values.
```
from sklearn.model_selection import GridSearchCV

# Define the parameter grid to search through
param_grid = {
    'n_estimators': [50, 100, 200],
    'max_depth': [None, 10, 20],
    'min_samples_split': [2, 5]
}

# Run the grid search (using Cross-Validation)
grid_search = GridSearchCV(estimator=RandomForestClassifier(random_state=42), 
                           param_grid=param_grid, 
                           cv=5, 
                           n_jobs=-1, # Use all available CPU cores
                           verbose=2)

grid_search.fit(X_train, y_train)

# Extract the best performing model
best_model = grid_search.best_estimator_
print("Best hyperparameters:", grid_search.best_params_)
```
---
## **6/ Export the Model**
- Once you have the best_model, you must save it to a file so you can deploy it later. This prevents you from having to retrain the model from scratch every time you launch the app.
```
import joblib

# Export the trained model to a file
joblib.dump(best_model, 'my_trained_model.pkl')

# (Optional) Export your teammate's scaler if StandardScaler was used
# joblib.dump(scaler, 'my_scaler.pkl')
```
---
# **III/ App Deployment (Building the Final Demo)**
- To showcase your project effectively, you should build a Web App rather than asking judges or users to run Python scripts in a terminal. Streamlit is currently the top choice for ML demos because of its rapid development speed and clean UI.
```
import streamlit as st
import joblib
import pandas as pd
import numpy as np

# 1. Load the trained model
model = joblib.load('my_trained_model.pkl')
# scaler = joblib.load('my_scaler.pkl') # Load this if you used scaling

# 2. Design the Web UI
st.title("Ultimate Prediction Web App")
st.write("Enter the parameters below to get a prediction from the model.")

# 3. Create input forms for the user (in a Sidebar or the Main body)
# Assuming your data has 3 features: Age, Salary, Credit Score
age = st.slider("Enter Age:", min_value=18, max_value=80, value=25)
salary = st.number_input("Enter Salary ($):", min_value=0, value=50000)
credit_score = st.slider("Credit Score:", min_value=300, max_value=850, value=650)

# 4. Action button to trigger the model
if st.button("Predict Now"):
    # Package the input data into a 2D array (the format sklearn expects)
    input_data = np.array([[age, salary, credit_score]])
    
    # input_data_scaled = scaler.transform(input_data) # Normalize if necessary
    
    # Execute the prediction
    prediction = model.predict(input_data) # or input_data_scaled
    
    # 5. Display the results
    if prediction[0] == 1:
        st.success("Prediction: The customer is LIKELY to purchase!")
        st.balloons()
    else:
        st.error("Prediction: The customer will NOT purchase.")
```
---
