# Full-Stack Machine Learning Prediction App

## 1. Project Overview

This project is a full-stack machine learning application that provides two types of predictions:

- **Stroke Prediction:** Uses a classification model to predict whether a person is classified as having a stroke or not, based on health-related information.
- **House Price Prediction:** Uses a regression model to estimate a house's price based on its features.

The application includes machine learning models, a FastAPI backend, and an HTML frontend that allows users to enter information and view predictions.

## 2. Technologies Used

- **Python:** Main programming language.
- **Pandas:** Used to load and process datasets.
- **Scikit-learn:** Used for preprocessing, training, and evaluating machine learning models.
- **Joblib:** Used to save and load trained models.
- **FastAPI:** Connects the frontend to the machine learning models through API endpoints.
- **Uvicorn:** Runs the FastAPI application server.
- **HTML, CSS, and JavaScript:** Used to create the user interface.

## 3. Datasets

### Stroke Prediction Dataset

File: `healthcare-dataset-stroke-data.csv`

This dataset contains health and demographic information, including age, gender, hypertension, heart disease, average glucose level, BMI, and smoking status.

- **Target variable:** `stroke`
- **Problem type:** Binary classification
- **Model:** Logistic Regression

The target values are:
- `0` — No stroke predicted
- `1` — Stroke predicted

### House Price Prediction Dataset

File: `kc_house_data.csv`

This dataset contains housing information, including bedrooms, bathrooms, living area, location, condition, and other property features.

- **Target variable:** `price`
- **Problem type:** Regression
- **Model:** Linear Regression

The model estimates a numerical house price based on the provided features.

## 4. Data Preprocessing

The datasets are prepared before model training. The preprocessing steps include:

- Checking and handling missing values.
- Separating input features from the target variable.
- Excluding unnecessary identifier columns from model inputs.
- Converting categorical variables into numerical features using One-Hot Encoding.
- Preparing numerical and categorical features through preprocessing pipelines.

StandardScaler is only used if included in the implemented preprocessing pipeline.

## 5. Model Training and Evaluation

The project uses two supervised machine learning algorithms.

### Logistic Regression

Used for the stroke classification task.

The model is evaluated using **Accuracy** and can also be examined using a confusion matrix and other classification metrics.

### Linear Regression

Used for house price prediction.

The model is evaluated using **R² score**, Mean Absolute Error (MAE), and Mean Squared Error (MSE).

The evaluation results indicate how well the models perform on the test data. Actual scores should be reported from the model training output.

## 6. Saving Trained Models

The trained models are saved using Joblib so they can be loaded by the backend without training them again every time the application starts.

- `stroke_model.joblib`
- `house_model.joblib`

## 7. Application Architecture

The application works in the following sequence:

1. The user enters information into the HTML frontend.
2. The frontend sends the input data to a FastAPI endpoint.
3. FastAPI receives the data and converts it into the format required by the model.
4. The saved machine learning model generates a prediction.
5. FastAPI returns the result to the frontend.
6. The user sees the prediction on the website.

## 8. Project Structure

```text
ml/
├── app.py
├── index.html
├── healthcare-dataset-stroke-data.csv
├── kc_house_data.csv
├── stroke_model.joblib
└── house_model.joblib
```

Additional notebooks, training scripts, or dependency files may be present depending on the implementation.

## 9. Installation and Setup

### Step 1: Open the project folder

Open the `ml` folder in Visual Studio Code.

### Step 2: Install the required packages

Open the VS Code terminal and run:

```bash
python -m pip install pandas scikit-learn joblib fastapi uvicorn
```

### Step 3: Start the application

Make sure the terminal is in the project folder, then run:

```bash
python -m uvicorn app:app --reload
```

### Step 4: Open the website

Open Google Chrome and visit:

http://127.0.0.1:8000

Keep the terminal running while using the application.

To view the available API documentation, visit:

http://127.0.0.1:8000/docs

## 10. API Endpoints

| Endpoint | Method | Purpose |
|---|---|---|
| `/` | GET | Opens the website |
| `/predict/stroke` | POST | Returns a stroke classification prediction |
| `/predict/house` | POST | Returns an estimated house price |

The prediction endpoints accept input data in JSON format and return prediction results.

## 11. Project Objectives

- Build classification and regression models using real-world datasets.
- Apply data preprocessing techniques.
- Evaluate model performance using appropriate metrics.
- Save and reuse trained machine learning models.
- Develop a FastAPI backend for prediction requests.
- Create a simple frontend that makes machine learning predictions accessible to users.

## 12. Limitations

- Stroke predictions are educational model outputs and must not be treated as medical diagnoses.
- Prediction quality depends on the datasets, preprocessing, and model performance.
- The house price dataset reflects its original data source and period; predictions may not represent current property prices in other markets.
- The application is a local demonstration and may require additional validation, security, and deployment work for production use.

## 13. Conclusion

This project demonstrates how machine learning models can be integrated into a full-stack application. It combines data preprocessing, classification, regression, model evaluation, model saving, a FastAPI backend, and a user-friendly HTML frontend in one working system.
