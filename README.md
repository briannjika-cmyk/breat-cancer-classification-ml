# Breast Cancer Classification with Machine Learning

## 📋 Project Overview

This project implements a **binary classification model** to predict whether a breast tumor is **malignant (M)** or **benign (B)** based on diagnostic features from fine needle aspirate (FNA) images. The model leverages the **Breast Cancer Wisconsin (Diagnostic) Dataset**, containing 569 tumor samples with 30 diagnostic features.

The project demonstrates a complete machine learning pipeline: from data exploration and preprocessing through model training and evaluation, providing practical insights into tumor classification for clinical decision support.

---

## 🎯 Problem Statement

Breast cancer is one of the most common cancers affecting women worldwide. Early and accurate detection is crucial for effective treatment. This project aims to build a predictive model that can assist in distinguishing between benign and malignant tumors based on measurable diagnostic features, thereby supporting clinical diagnosis and reducing the need for invasive procedures.

---

## 📊 Dataset

### Dataset Source
**Breast Cancer Wisconsin (Diagnostic) Dataset**
- **File**: `data.csv`
- **Size**: 569 samples with 32 columns

### Dataset Structure
- **Rows**: 569 tumor samples
- **Columns**: 32 features (1 ID + 1 target + 30 diagnostic features)
- **No missing values**: All 569 samples have complete information

### Target Variable
- **Column**: `diagnosis`
- **Values**: 
  - `M` (Malignant) — Cancerous tumors
  - `B` (Benign) — Non-cancerous tumors

### Features (30 Diagnostic Variables)

The dataset contains three types of measurements for 10 key tumor characteristics:

| Characteristic | Mean | SE (Standard Error) | Worst |
|---|---|---|---|
| radius | radius_mean | radius_se | radius_worst |
| texture | texture_mean | texture_se | texture_worst |
| perimeter | perimeter_mean | perimeter_se | perimeter_worst |
| area | area_mean | area_se | area_worst |
| smoothness | smoothness_mean | smoothness_se | smoothness_worst |
| compactness | compactness_mean | compactness_se | compactness_worst |
| concavity | concavity_mean | concavity_se | concavity_worst |
| concave points | concave points_mean | concave points_se | concave points_worst |
| symmetry | symmetry_mean | symmetry_se | symmetry_worst |
| fractal dimension | fractal_dimension_mean | fractal_dimension_se | fractal_dimension_worst |

- **Mean**: Average value of the measurement
- **SE**: Standard error (variability) of the measurement  
- **Worst**: Largest value observed in the measurement

### Dataset Characteristics
- **Malignant cases**: 212 (37.3%)
- **Benign cases**: 357 (62.7%)
- **Numeric range**: Features range from approximately 0.0 to 4254.0 depending on the variable
- **Data type**: 30 float64 features, 1 object (diagnosis)

---

## 💻 Technologies and Libraries

The project uses the following Python libraries and frameworks:

| Library | Purpose |
|---|---|
| **Pandas** | Data manipulation, loading, and preprocessing |
| **NumPy** | Numerical computations |
| **Matplotlib** | Data visualization and plotting |
| **Seaborn** | Statistical and aesthetic data visualization |
| **Scikit-learn** | Machine learning models, preprocessing, and evaluation metrics |

### Environment
- **Python**: 3.x
- **Notebook**: Jupyter Notebook (`.ipynb`)

---

## 🔄 Project Workflow

```
Data Loading & Exploration
        ↓
    Data Cleaning
    (Remove unnecessary columns)
        ↓
Exploratory Data Analysis (EDA)
(Descriptive statistics, distribution analysis)
        ↓
   Data Preprocessing
(Encoding categorical variables)
        ↓
Feature Scaling/Normalization
   (if applied)
        ↓
Train/Test Split
        ↓
Model Training
(Multiple algorithms)
        ↓
   Model Evaluation
(Metrics & comparison)
        ↓
  Predictions & Results
```

---

## 🔬 Machine Learning Approach

### 1. **Data Cleaning**
- Removed the empty `Unnamed: 32` column
- Verified data integrity and completeness

### 2. **Exploratory Data Analysis (EDA)**
- Examined the first 5 rows of the dataset
- Reviewed data types and null values using `df.info()`
- Generated descriptive statistics with `df.describe()`
- Identified unique values in the target variable (`diagnosis`)

### 3. **Data Preprocessing**

#### Encoding the Target Variable
- Applied **one-hot encoding** on the `diagnosis` column using `pd.get_dummies()`
- Created a binary column `M` with values:
  - `1` for Malignant
  - `0` for Benign (dropped via `drop_first=True`)

#### Feature Preparation
- 30 diagnostic features are ready for model input
- All features are numeric and continuous

### 4. **Model Training & Evaluation**

The notebook implements classification models to predict tumor diagnosis. The project evaluates model performance using standard evaluation metrics including accuracy, precision, recall, and F1-score to ensure robust and reliable predictions.

---

## 📈 Key Findings

From the exploratory analysis:

1. **Dataset Balance**: The dataset is moderately imbalanced, with approximately 62.7% benign cases and 37.3% malignant cases.

2. **Feature Ranges**:
   - **Radius Mean**: 6.98 - 28.11 mm
   - **Area Mean**: 143.5 - 2,501.0 mm²
   - **Texture Mean**: 9.71 - 39.28 (scale units)
   - Features show significant variation, suggesting different tumor morphologies in the dataset

3. **Data Quality**: All samples are complete with no missing values, enabling clean model training.

4. **Diagnostic Features**: The three types of measurements (mean, SE, worst) provide multiple perspectives on tumor characteristics, which can improve model discrimination.

---

## 📁 Project Structure

```
breat-cancer-classification-ml/
├── Cancer prediction model.ipynb    # Main Jupyter notebook with full analysis
├── data.csv                         # Breast Cancer Wisconsin dataset
├── README.md                        # Project documentation
└── .gitignore                       # Git ignore file
```

---

## 🚀 How to Run the Project

### 1. **Prerequisites**
Ensure you have Python 3.x installed. You can download it from [python.org](https://www.python.org/downloads/).

### 2. **Install Required Libraries**

Install the necessary Python packages using pip:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

Alternatively, if you have a `requirements.txt` file:

```bash
pip install -r requirements.txt
```

### 3. **Clone or Download the Repository**

```bash
git clone https://github.com/briannjika-cmyk/breat-cancer-classification-ml.git
cd breat-cancer-classification-ml
```

### 4. **Launch Jupyter Notebook**

Start the Jupyter Notebook server:

```bash
jupyter notebook
```

This will open Jupyter in your default web browser.

### 5. **Open and Run the Notebook**

1. Click on `Cancer prediction model.ipynb` to open it
2. Execute cells sequentially by:
   - Selecting a cell and pressing `Shift + Enter`, or
   - Using the "Run All" option in the Cell menu

3. The notebook will:
   - Load the dataset from `data.csv`
   - Perform data cleaning and exploration
   - Preprocess features and target variable
   - Train classification models
   - Display evaluation results and predictions

### 6. **Alternative: Run Locally with Python**

If you prefer running the notebook programmatically (instead of interactive mode):

```bash
jupyter nbconvert --to script "Cancer prediction model.ipynb"
python "Cancer prediction model.py"
```

---

## 📊 Results

The model demonstrates the capability to classify breast tumors as malignant or benign. The evaluation includes:

- **Performance Metrics**: Accuracy, precision, recall, and F1-score
- **Robustness**: Cross-validation results (if applied)
- **Model Comparison**: Relative performance of different algorithms
- **Predictions**: Example predictions on test or new data

Detailed results and visualizations are generated and displayed within the Jupyter notebook.

---

## ⚠️ Limitations

1. **Dataset Size**: The dataset contains only 569 samples, which is relatively small for deep learning approaches. Traditional machine learning models are more appropriate.

2. **Class Imbalance**: The dataset has more benign cases (62.7%) than malignant cases (37.3%), which could bias models toward predicting benign tumors. Techniques like class weighting or resampling could address this.

3. **Feature Scaling**: Some features have widely different ranges (e.g., area vs. smoothness), which may require normalization for certain algorithms.

4. **No External Validation**: The model is validated on data from the same dataset without external testing on an independent cohort.

5. **Clinical Applicability**: This model is for educational purposes and should not be used for actual clinical diagnosis without proper medical validation and regulatory approval.

6. **Feature Engineering**: The project uses raw features without exploring advanced feature engineering or selection techniques that could improve model performance.

---

## 🔮 Future Improvements

1. **Advanced Feature Engineering**
   - Implement feature selection techniques (e.g., recursive feature elimination, PCA)
   - Explore feature interactions and polynomial features
   - Normalize and standardize features using StandardScaler or MinMaxScaler

2. **Class Imbalance Handling**
   - Apply oversampling (SMOTE) or undersampling techniques
   - Use class weights in model training
   - Evaluate using metrics robust to imbalance (e.g., AUC-ROC, F1-score)

3. **Model Optimization**
   - Implement ensemble methods (Gradient Boosting, XGBoost)
   - Perform hyperparameter tuning using GridSearchCV or RandomizedSearchCV
   - Apply cross-validation for more robust evaluation

4. **Deep Learning**
   - Build neural networks using TensorFlow/Keras
   - Experiment with different architectures and activation functions
   - Implement dropout and batch normalization for regularization

5. **Model Interpretability**
   - Use SHAP (SHapley Additive exPlanations) for feature importance analysis
   - Generate LIME (Local Interpretable Model-agnostic Explanations) explanations
   - Visualize decision boundaries and feature distributions

6. **Production Deployment**
   - Save the trained model using `joblib` or `pickle`
   - Create a REST API (Flask, FastAPI) for predictions
   - Develop a web interface for end-users

7. **Additional Validation**
   - Test on external datasets to validate generalization
   - Perform medical domain validation with clinical experts
   - Implement monitoring for model drift in production

---

## 📝 Conclusion

This project demonstrates a complete machine learning pipeline for medical data classification. By leveraging diagnostic features from the Breast Cancer Wisconsin dataset, the model learns to distinguish between benign and malignant tumors. While the current implementation provides a solid foundation, the proposed future improvements could significantly enhance model performance, interpretability, and real-world applicability.

The project serves as an educational resource for understanding:
- Data preprocessing and exploratory analysis
- Model training and evaluation workflows
- Practical considerations in medical AI applications

---

## 👤 Author

**Brian Njika**
- GitHub: [@briannjika-cmyk](https://github.com/briannjika-cmyk)

---

## 📜 License

This project is part of a machine learning educational initiative. The Breast Cancer Wisconsin dataset is publicly available and commonly used for academic purposes.

---

## 🔗 References

- **Dataset**: Breast Cancer Wisconsin (Diagnostic) Dataset
  - [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/breast+cancer+wisconsin+(diagnostic))
  
- **Scikit-learn Documentation**: https://scikit-learn.org/
- **Pandas Documentation**: https://pandas.pydata.org/
- **Jupyter Notebook**: https://jupyter.org/

---

**Last Updated**: September 2026  
**Status**: Active and under continuous development
