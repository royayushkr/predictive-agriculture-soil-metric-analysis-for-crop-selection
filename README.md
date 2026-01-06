# Crop Prediction Analysis

## Project Overview
Measuring essential soil metrics such as nitrogen, phosphorous, potassium levels, and pH values is critical for assessing soil condition, but it can be expensive and time-consuming. This project aims to assist farmers in selecting the best crop for their field by identifying the single most important soil feature for predictive performance.

## Dataset
The analysis uses `soil_measures.csv`, which contains data on soil composition and the optimal crop for those conditions.

**Features:**
* `"N"`: Nitrogen content ratio in the soil
* `"P"`: Phosphorous content ratio in the soil
* `"K"`: Potassium content ratio in the soil
* `"pH"`: pH value of the soil
* `"crop"`: Categorical target variable containing various crops (e.g., rice, maize, chickpea, apple, etc.)

## Methodology

### 1. Data Preprocessing
* Loaded the dataset using `pandas`.
* Verified that there were no missing values in the dataset.
* Split the data into features (`X`) and target (`y`), followed by a train-test split (80/20).

### 2. Modeling Strategy
To isolate the importance of each soil metric, the project utilized an iterative approach:
1.  **Feature Isolation:** Looped through each feature (`N`, `P`, `K`, `ph`) individually.
2.  **Model Training:** Trained a multi-class `LogisticRegression` model for each specific feature.
3.  **Evaluation:** Calculated the **F1-score** (weighted average) to assess predictive performance for each feature.

## Results
The analysis evaluated the predictive power of each soil metric in isolation. The F1-scores were as follows:

| Feature | F1-Score |
| :--- | :--- |
| **K (Potassium)** | **0.239** |
| P (Phosphorous) | 0.148 |
| N (Nitrogen) | 0.091 |
| pH | 0.045 |

**Conclusion:** The feature **`K` (Potassium)** was identified as the single most predictive feature for determining the optimal crop type.

## Technologies Used
* **Python**
* **pandas**: For data manipulation.
* **scikit-learn**: For `LogisticRegression`, `train_test_split`, and `metrics` (F1 score).

## Usage
1.  Ensure `soil_measures.csv` is present in the directory.
2.  Run the Jupyter Notebook to execute the training loop.
3.  The script will output the F1 score for each feature and print the dictionary containing the best predictive feature.
