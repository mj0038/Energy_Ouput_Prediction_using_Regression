# Energy Output Prediction Using Regression Models

This project aims to predict the hourly energy output of a [Combined Cycle Power Plant (CCPP) Dataset from UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Combined+Cycle+Power+Plant) using various regression models . The dataset contains ambient variables such as temperature, pressure, and humidity, which are used to predict the plant's energy output. The project explores both linear and non-linear models, including interaction terms and K-Nearest Neighbors (KNN) regression.

## Table of Contents
1. [Dataset](#dataset)
2. [Project Structure](#project-structure)
3. [Models and Analysis](#models-and-analysis)
4. [Results and Insights](#results-and-insights)
5. [Getting Started](#getting-started)


---

## Dataset

The dataset contains 9,568 observations recorded from a Combined Cycle Power Plant over six years. The variables include:
- **AT**: Ambient Temperature
- **V**: Exhaust Vacuum
- **AP**: Ambient Pressure
- **RH**: Relative Humidity
- **PE**: Net hourly electrical energy output (target variable)

> **File**: `dataset.xlsx`

## Project Structure


## Models and Analysis

1. **Simple Linear Regression**:
   - A basic model with each predictor individually regressed against the target variable.
   - **Best Model**: Using `AT` as the sole predictor yielded an R² score of 0.899.

2. **Multiple Linear Regression**:
   - All predictors were included, along with interaction terms and polynomial terms to capture non-linear relationships.
   - **Feature Selection**: Insignificant terms were iteratively removed based on p-values to avoid overfitting.

3. **Polynomial Regression**:
   - Extended the linear regression to include quadratic and cubic terms, allowing non-linear relationships with the target variable.

4. **K-Nearest Neighbors (KNN) Regression**:
   - A non-parametric model was applied to both normalized and raw features.
   - **Optimal k** was determined from values in the range {1, ..., 100} by comparing Mean Squared Error (MSE).

5. **Model Comparison**:
   - Each model was evaluated on training and testing data.
   - The **KNN regression with normalized features** provided the best generalization with the lowest test MSE, showing that a non-parametric approach can outperform linear models for this dataset.

## Results and Insights

| Model                         | Best Features                           | Optimal Parameters                    | Train MSE | Test MSE | Key Characteristics                                                                                      |
|-------------------------------|-----------------------------------------|---------------------------------------|-----------|----------|----------------------------------------------------------------------------------------------------------|
| **Simple Linear Regression**  | `AT`                                    | -                                     | 19.8      | 20.5     | Straightforward, interpretable, only captures linear relationships for a single predictor.                |
| **Multiple Linear Regression**| All predictors                          | Significant terms only (Model 2)      | 17.89     | 18.66    | Parametric, interpretable, includes interaction terms and polynomial terms, improved generalization.      |
| **Polynomial Regression**     | `AT` with quadratic and cubic terms     | Degree 3                              | 17.3      | 18.1     | Captures non-linearity, improved fit, but high risk of overfitting with complex terms.                    |
| **KNN Regression**            | Normalized Features                     | \( k = 4 \)                           | 13.67     | 14.31    | Non-parametric, adapts to non-linear relationships, benefits significantly from normalized features.      |

### Key Findings
- **Best Model**: KNN regression with normalized features achieved the lowest test MSE.
- **Normalization**: Essential for KNN to improve performance, as distance-based algorithms are sensitive to feature scaling.
- **Interpretability**: While KNN performed best, the linear models provide valuable insights into individual predictor effects on the energy output.

## Getting Started

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/Energy_Output_using_Regression.git
   cd Energy_Output_using_Regression
