# Medical Insurance Cost Prediction - ANN

## Overview

This project implements an Artificial Neural Network (ANN) using TensorFlow/Keras to predict medical insurance charges for individuals based on their personal and lifestyle attributes. This is a regression problem where the target variable is a continuous numerical value representing insurance charges.

---

## Dataset

* **Source:** `insurance.csv`
* **Rows:** 1,338 (1,337 after removing 1 duplicate)
* **Columns:** 7
* **Target Variable:** `charges`

### Features

| Feature  | Description           |
| -------- | --------------------- |
| age      | Age of the individual |
| sex      | Male / Female         |
| bmi      | Body Mass Index       |
| children | Number of dependents  |
| smoker   | Yes / No              |
| region   | Geographic region     |

---

## Data Preprocessing

The following preprocessing steps were applied:

* Checked for missing values
* Removed duplicate records
* Split features and target variable
* Identified numerical and categorical columns
* Applied preprocessing using `ColumnTransformer`

### Numerical Pipeline

* SimpleImputer (mean strategy)
* StandardScaler

### Categorical Pipeline

* SimpleImputer (most frequent strategy)
* OneHotEncoder (`drop='first'`)

### Train-Test Split

* 80% Training Data
* 20% Testing Data
* `random_state=42`

---

## Model Architecture

```text
Input Layer
      ↓
Dense(64, activation='relu')
      ↓
Dropout(0.3)
      ↓
Dense(32, activation='relu')
      ↓
Dense(1, activation='linear')
```

### Configuration

| Parameter        | Value                    |
| ---------------- | ------------------------ |
| Optimizer        | Adam                     |
| Loss Function    | Mean Squared Error (MSE) |
| Epochs           | 100                      |
| Batch Size       | 32                       |
| Validation Split | 10%                      |

---

## Model Performance

| Metric   | Value         |
| -------- | ------------- |
| MAE      | 5415.19       |
| MSE      | 54,797,098.87 |
| R² Score | 0.7018        |

### Interpretation

* Average prediction error is approximately **$5,415**
* Model explains approximately **70%** of the variance in insurance charges
* Performance is reasonable but can be improved for high-cost insurance cases

---

## Sample Predictions

| Predicted | Actual    |
| --------- | --------- |
| 8,220.21  | 8,688.86  |
| 7,499.83  | 5,708.87  |
| 14,837.73 | 11,436.74 |
| 27,797.70 | 38,746.36 |
| 12,686.93 | 4,463.21  |

---

## Future Improvements

* Apply log transformation on `charges`
* Create interaction features such as:

  * smoker × bmi
  * smoker × age
* Tune hyperparameters
* Experiment with deeper neural networks
* Use k-fold cross-validation

---

## Tech Stack

* Python 3.13
* NumPy
* Pandas
* Scikit-learn
* TensorFlow / Keras

---

## Installation

```bash
pip install numpy pandas scikit-learn tensorflow
```

---

## Usage

1. Place `insurance.csv` in the project directory.
2. Open `Notebook.ipynb`.
3. Run all cells sequentially.

---

## Project Structure

```text
.
├── insurance.csv
├── Notebook.ipynb
└── README.md
```

---

## Author

**Muhammad Taha Sattar Arain**

AI & Data Science Student — SMIT (Batch 10)

GitHub: https://github.com/funterpie

Portfolio: https://tahatradz.online
