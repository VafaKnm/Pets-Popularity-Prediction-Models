# Pets Popularity Prediction Models

A machine learning and deep learning project for predicting pet popularity using multiple regression models.

This project was originally developed in a Kaggle Notebook environment and compares several classical machine learning models and an Artificial Neural Network (ANN) for pet popularity prediction.

The models used in this project include:

* Support Vector Machine / Support Vector Regression
* Logistic Regression
* Random Forest
* Artificial Neural Network

---

## Overview

Pet popularity prediction is a regression or scoring problem where the goal is to estimate how popular a pet profile may become based on available pet-related features.

In a pet adoption or pet profile platform, popularity can be influenced by many factors, such as:

* Pet type
* Breed
* Age
* Gender
* Color
* Health condition
* Description text
* Profile metadata
* Image quality
* Adoption-related attributes

This project explores how machine learning models can be used to learn patterns from pet profile data and predict a popularity-related target score.

---

## What This Project Does

This project demonstrates how to:

* Load pet popularity data in a Kaggle Notebook
* Explore structured pet-related features
* Prepare data for machine learning
* Encode categorical variables
* Scale numerical variables
* Train multiple regression models
* Compare classical ML models with an ANN model
* Evaluate prediction performance
* Build a baseline system for pet popularity prediction

---

## Problem Type

This project is mainly a prediction task.

Depending on how the target variable is represented, it can be treated as:

```text id="sfzo6f"
Regression:
    Predict a continuous popularity score

or

Classification:
    Predict a popularity category
```

The repository title and Kaggle notebook name suggest a regression-oriented workflow for predicting pet popularity.

Conceptually:

```text id="frd0kv"
Input:
    pet profile features

Output:
    predicted popularity score
```

---

## Dataset

The project uses a pet popularity dataset in a Kaggle environment.

A typical pet popularity dataset may contain features such as:

```text id="5pr5i9"
pet_id
type
breed
age
gender
color
maturity_size
fur_length
vaccinated
dewormed
sterilized
health
quantity
fee
state
description
photo_amount
popularity_score
```

The exact columns depend on the Kaggle dataset version used in the notebook.

---

## Input Features

Possible input features include:

| Feature Type           | Examples                                       |
| ---------------------- | ---------------------------------------------- |
| Numeric features       | Age, fee, quantity, photo amount               |
| Categorical features   | Type, breed, gender, color, health             |
| Binary features        | Vaccinated, sterilized, dewormed               |
| Text features          | Pet description                                |
| Image/profile features | Number of photos, image quality, visual appeal |
| Location features      | State or region                                |

---

## Target Variable

The target variable represents pet popularity.

It may be a score, ranking, adoption interest, engagement level, or another popularity-related value depending on the dataset.

Example:

```text id="mvlq3b"
popularity_score = 72.5
```

or:

```text id="n0gnb5"
popularity_level = high
```

In a regression workflow, the model predicts a numeric value.

---

## General Machine Learning Pipeline

The full project workflow can be described as:

```text id="h4qxm0"
Raw Pet Dataset
      ↓
Data Cleaning
      ↓
Exploratory Data Analysis
      ↓
Feature Engineering
      ↓
Categorical Encoding
      ↓
Numerical Scaling
      ↓
Train/Test Split
      ↓
Model Training
      ↓
Model Evaluation
      ↓
Popularity Prediction
```

---

## Models Used

### 1. Support Vector Machine / Support Vector Regression

SVM can be used for classification, while SVR is used for regression.

For popularity prediction, SVR is usually more appropriate if the target is continuous.

SVR attempts to find a function that predicts the target value while keeping prediction errors within a defined margin.

Useful when:

* Dataset is not extremely large
* Feature space is structured
* Nonlinear kernels are useful
* A strong classical baseline is needed

---

### 2. Logistic Regression

Logistic Regression is usually used for classification.

If popularity is converted into categories such as low, medium, and high, Logistic Regression can be used as a classification baseline.

Example:

```text id="xbk4m7"
low popularity
medium popularity
high popularity
```

If the task is pure regression, Linear Regression would usually be more appropriate than Logistic Regression.

---

### 3. Random Forest

Random Forest is an ensemble model based on multiple decision trees.

It is often strong for tabular datasets because it can capture nonlinear relationships and feature interactions.

Advantages:

* Works well with structured data
* Handles nonlinear patterns
* Less sensitive to scaling
* Can provide feature importance
* Strong baseline for tabular prediction problems

---

### 4. Artificial Neural Network

The ANN model learns nonlinear relationships through multiple dense layers.

A typical ANN for tabular regression looks like:

```text id="m26nq6"
Input Features
      ↓
Dense Layer
      ↓
Activation Function
      ↓
Dense Layer
      ↓
Activation Function
      ↓
Output Layer
      ↓
Predicted Popularity Score
```

ANNs can be useful when the dataset contains complex interactions between features, but they usually require careful preprocessing, regularization, and validation.

---

## Example ANN Architecture

A simplified Keras-style ANN for this type of project could look like this:

```python id="mwa66b"
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense, Dropout

model = Sequential()

model.add(Dense(128, activation="relu", input_shape=(num_features,)))
model.add(Dropout(0.3))

model.add(Dense(64, activation="relu"))
model.add(Dropout(0.2))

model.add(Dense(32, activation="relu"))

model.add(Dense(1, activation="linear"))

model.compile(
    optimizer="adam",
    loss="mse",
    metrics=["mae"]
)
```

For classification-style popularity prediction, the final layer and loss function would change.

---

## Example Model Comparison

The project can compare models like this:

| Model               | Task Type                    | Notes                                              |
| ------------------- | ---------------------------- | -------------------------------------------------- |
| Logistic Regression | Classification               | Useful if popularity is converted into categories  |
| SVR / SVM           | Regression or classification | Strong margin-based baseline                       |
| Random Forest       | Regression                   | Strong tabular ML baseline                         |
| ANN                 | Regression                   | Deep learning approach for nonlinear relationships |

---

## Input and Output

### Input

The input is a pet profile represented as structured features.

Example:

```text id="w6aew2"
type: cat
breed: domestic short hair
age: 12 months
gender: female
vaccinated: yes
sterilized: yes
health: healthy
photo_amount: 5
description: friendly and playful cat
```

### Output

The output is a predicted popularity value.

Example:

```text id="0ajgpj"
predicted_popularity_score = 68.4
```

If the task is classification-based:

```text id="ka10jj"
predicted_popularity_class = high
```

---

## Repository Structure

Current repository structure:

```text id="f5h4qf"
Pets-Popularity-Prediction-Models/
│
├── README.md
└── ml-dl-regressions-for-pets-popularity-prediction.ipynb
```

Suggested future structure:

```text id="pd6k6j"
Pets-Popularity-Prediction-Models/
│
├── README.md
├── requirements.txt
├── notebooks/
│   └── ml-dl-regressions-for-pets-popularity-prediction.ipynb
├── src/
│   ├── data_loader.py
│   ├── preprocessing.py
│   ├── feature_engineering.py
│   ├── train_ml_models.py
│   ├── train_ann.py
│   ├── evaluate.py
│   └── inference.py
├── models/
│   ├── random_forest_model.pkl
│   ├── svm_model.pkl
│   ├── logistic_regression_model.pkl
│   └── ann_model.h5
├── assets/
│   ├── target_distribution.png
│   ├── feature_importance.png
│   ├── model_comparison.png
│   └── prediction_vs_actual.png
└── examples/
    └── sample_predictions.md
```

---

## Installation

Clone the repository:

```bash id="nh0v72"
git clone https://github.com/VafaKnm/Pets-Popularity-Prediction-Models.git
cd Pets-Popularity-Prediction-Models
```

Create a virtual environment:

```bash id="v5djxw"
python -m venv .venv
source .venv/bin/activate
```

Install common dependencies:

```bash id="yoknln"
pip install numpy pandas matplotlib seaborn scikit-learn tensorflow keras jupyter
```

Start Jupyter Notebook:

```bash id="rlxgnh"
jupyter notebook
```

Open:

```text id="2c2dlg"
ml-dl-regressions-for-pets-popularity-prediction.ipynb
```

---

## Suggested `requirements.txt`

```txt id="cj2ik4"
numpy
pandas
matplotlib
seaborn
scikit-learn
tensorflow
keras
jupyter
```

If text or image features are added later:

```txt id="z6k33d"
nltk
spacy
pillow
opencv-python
transformers
```

---

## Example Preprocessing Steps

A script-based version of the project could include preprocessing steps like:

```python id="93ydzr"
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler, OneHotEncoder

def split_features_target(df, target_column):
    X = df.drop(columns=[target_column])
    y = df[target_column]
    return X, y
```

For numerical scaling:

```python id="e987f7"
scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)
```

For categorical encoding:

```python id="al8bl6"
encoder = OneHotEncoder(handle_unknown="ignore")
X_categorical_encoded = encoder.fit_transform(X_categorical)
```

---

## Example Random Forest Model

```python id="joy8t2"
from sklearn.ensemble import RandomForestRegressor

rf_model = RandomForestRegressor(
    n_estimators=300,
    random_state=42,
    n_jobs=-1
)

rf_model.fit(X_train, y_train)

predictions = rf_model.predict(X_test)
```

---

## Example SVR Model

```python id="hs740t"
from sklearn.svm import SVR

svr_model = SVR(
    kernel="rbf",
    C=10,
    gamma="scale"
)

svr_model.fit(X_train_scaled, y_train)

predictions = svr_model.predict(X_test_scaled)
```

---

## Example Logistic Regression Model

If the target is converted into categories:

```python id="ybdj1s"
from sklearn.linear_model import LogisticRegression

log_model = LogisticRegression(
    max_iter=1000,
    random_state=42
)

log_model.fit(X_train_scaled, y_train_class)

predictions = log_model.predict(X_test_scaled)
```

---

## Example Inference Function

A future inference function could look like this:

```python id="d9umls"
def predict_pet_popularity(pet_features, model, preprocessor):
    """
    Predict popularity score for a pet profile.
    """
    processed_features = preprocessor.transform(pet_features)
    prediction = model.predict(processed_features)

    return float(prediction[0])
```

Example input:

```python id="3pkl82"
sample_pet = {
    "type": "cat",
    "age": 12,
    "gender": "female",
    "vaccinated": "yes",
    "sterilized": "yes",
    "photo_amount": 5
}
```

Example output:

```text id="h621qk"
Predicted popularity score: 68.4
```

---

## Evaluation

The current README does not include final numeric evaluation results.

For regression, useful metrics include:

| Metric               | Meaning                 |
| -------------------- | ----------------------- |
| MAE                  | Mean Absolute Error     |
| MSE                  | Mean Squared Error      |
| RMSE                 | Root Mean Squared Error |
| R² Score             | Explained variance      |
| Spearman Correlation | Ranking quality         |

Example evaluation code:

```python id="84q9tt"
from sklearn.metrics import mean_absolute_error, mean_squared_error, r2_score
import numpy as np

y_pred = model.predict(X_test)

mae = mean_absolute_error(y_test, y_pred)
rmse = np.sqrt(mean_squared_error(y_test, y_pred))
r2 = r2_score(y_test, y_pred)

print("MAE:", mae)
print("RMSE:", rmse)
print("R2:", r2)
```

For classification-style popularity categories:

| Metric           | Meaning                                 |
| ---------------- | --------------------------------------- |
| Accuracy         | Overall correctness                     |
| Precision        | Correctness of positive predictions     |
| Recall           | Ability to detect each popularity class |
| F1-score         | Balance of precision and recall         |
| Confusion Matrix | Class-level mistakes                    |

---

## Suggested Result Table

After running evaluation, the README can be updated with:

| Model               | MAE | RMSE |  R² | Notes                   |
| ------------------- | --: | ---: | --: | ----------------------- |
| SVM / SVR           | TBD |  TBD | TBD | Classical baseline      |
| Logistic Regression | TBD |  TBD | TBD | If classification-based |
| Random Forest       | TBD |  TBD | TBD | Tree ensemble           |
| ANN                 | TBD |  TBD | TBD | Deep learning model     |

---

## Suggested Visualizations

Recommended plots:

* Target popularity distribution
* Missing value heatmap
* Feature correlation heatmap
* Feature importance plot
* Actual vs predicted popularity
* Residual error distribution
* Model comparison bar chart
* Learning curve for ANN

---

## Suggested Improvements

### 1. Clarify the Target Variable

The README should clearly define what “popularity” means.

Examples:

```text id="booo7g"
adoption speed
profile engagement
Pawpularity score
number of views
number of likes
```

A clear target definition makes the project easier to understand.

---

### 2. Add Model Evaluation Results

The project should include a model comparison table with real metrics.

Recommended metrics:

```text id="jly6do"
MAE
RMSE
R²
Spearman correlation
```

---

### 3. Add Feature Importance

Random Forest can provide feature importance.

Example:

```python id="l0twxj"
import pandas as pd

importance = pd.Series(
    rf_model.feature_importances_,
    index=feature_names
).sort_values(ascending=False)

print(importance.head(20))
```

This helps answer:

```text id="s7b8tj"
Which features influence pet popularity most?
```

---

### 4. Add Text Features

Pet descriptions can contain useful information.

Future versions can extract text features using:

| Method            | Description                 |
| ----------------- | --------------------------- |
| TF-IDF            | Simple text representation  |
| Word2Vec          | Word embeddings             |
| Sentence-BERT     | Sentence-level embeddings   |
| BERT / DistilBERT | Contextual language model   |
| LLM embeddings    | Strong modern text features |

---

### 5. Add Image Features

Pet profile images can strongly affect popularity.

Future versions can use image features from:

```text id="ncw90s"
ResNet
EfficientNet
CLIP
ViT
ConvNeXt
```

This can turn the project into a multimodal prediction system.

---

### 6. Build a Multimodal Model

A stronger model can combine:

```text id="53c4mu"
tabular pet metadata
description text embeddings
image embeddings
```

Conceptually:

```text id="kj9wt2"
Tabular Features ───── Dense Layers ┐
Text Embeddings ────── Dense Layers ├── Concatenate ── Final Prediction
Image Embeddings ───── Dense Layers ┘
```

---

### 7. Use Cross-Validation

Cross-validation provides more reliable performance estimates.

Recommended setup:

```text id="imhwg4"
K-Fold cross-validation
Stratified K-Fold on target bins
GroupKFold if shelter/user/source groups exist
```

---

### 8. Add a Demo App

A simple demo would make the project easier to test.

Recommended tools:

* Streamlit
* Gradio
* FastAPI

Example UI:

```text id="7gc5da"
Enter pet profile information
Upload pet image
Enter pet description
Click Predict
Show predicted popularity score
```

---

## Limitations

The current project has several limitations:

* It is notebook-based and not yet structured as reusable Python code.
* The README does not currently include full evaluation metrics.
* The trained models are not included in the repository.
* The exact definition of popularity should be documented more clearly.
* Tabular features alone may not capture visual attractiveness or description quality.
* Pet popularity can be affected by external factors such as platform traffic, location, timing, and adoption campaign exposure.
* Model predictions should not be treated as guaranteed adoption outcomes.

---

## Ethical Considerations

Pet popularity prediction should be used carefully.

Important points:

* Predictions may reflect dataset bias.
* Less popular pets should not be deprioritized unfairly.
* The model should support adoption improvement, not reduce visibility.
* Shelters should use predictions to improve descriptions, photos, and outreach.
* The system should not make final decisions about which animals deserve attention.

A responsible use case is:

```text id="w2jgk3"
Identify pets that may need better photos, descriptions, or promotion support.
```

---

## Use Cases

This project can be useful for:

* Learning regression modeling
* Comparing ML and ANN models
* Practicing tabular data preprocessing
* Understanding model evaluation
* Building pet adoption analytics tools
* Predicting profile engagement
* Supporting shelter marketing decisions
* Creating a baseline for multimodal ML projects

---

## Possible Future Work

Recommended future work:

* Add `requirements.txt`
* Add clean Python scripts
* Add saved models
* Add preprocessing pipeline
* Add model comparison table
* Add feature importance analysis
* Add actual vs predicted plot
* Add residual error plot
* Add cross-validation
* Add text embeddings from pet descriptions
* Add image embeddings from pet photos
* Add multimodal ANN
* Add Streamlit or Gradio demo
* Add Dockerfile

---

## Conclusion

This repository demonstrates a machine learning and deep learning workflow for pet popularity prediction.

The project is useful for learning:

```text id="jgq6ad"
tabular data preprocessing
feature engineering
SVM / SVR modeling
Logistic Regression baseline
Random Forest regression
ANN modeling
model comparison
Kaggle-based ML experimentation
```

With clearer target documentation, evaluation metrics, feature importance, saved models, and multimodal features from text and images, this repository can become a much stronger pet popularity prediction portfolio project.
