# Early PCOD Flare-Up Detection System (Machine Learning)

---

## Definition
- Predictive system for **early detection of PCOD flare-ups**
- Uses **XGBoost and ensemble ML models**
- Outputs:
  - Flare probability
  - Risk level
  - Recommendations

---


---

## XGBoost Model Deployment (Detailed)

### Overview
- Successfully deployed an **XGBoost classifier** for PCOD flare prediction
- Achieved:
  - **AUC-ROC: 0.9989**
  - **Accuracy: 0.9811**
- Demonstrates:
  - High precision
  - Strong generalization

---

## Implementation Workflow

### Step-by-Step Process

1. **Dataset Loading**
   - Source:
     ```
     /content/drive/MyDrive/user_habits_pcod_flare.csv
     ```
   - Records: ~6350

---

2. **Environment Setup**
- Libraries used:
  - pandas, numpy → data handling
  - sklearn → preprocessing & evaluation
  - xgboost → model training
  - matplotlib, seaborn → visualization

---

3. **Custom Class Design**

### XGBoostPCODPredictor

#### Responsibilities
- Encapsulates entire ML pipeline:
  - Preprocessing
  - Training
  - Evaluation
  - Prediction
  - Saving/loading

---

## Data Preprocessing

### Steps
- Rename target:
  - → `flare_label`
- Drop irrelevant columns:
  - `typical_symptoms`
  - `user_id`
  - `date`
  - `personal_deviation_score`
  - `day_of_study`
- Encode categorical features:
  - cycle_phase
  - pcod_severity
  - insulin_resistant
- Method:
  - **LabelEncoder**
- Ensure:
  - All features are numeric

---

## Model Training

### Training Function: `train_xgboost_model()`

#### Steps
1. Train-test split:
   - 80% training
   - 20% testing
2. Feature scaling:
   - **StandardScaler**
3. Model training:
   - XGBClassifier

---

### Hyperparameters
- n_estimators = 200
- max_depth = 6
- learning_rate = 0.1

---

## Model Evaluation

### Evaluation Function: `evaluate_model()`

#### Metrics
- Accuracy: **0.9811**
- F1 Score: **0.9812**
- AUC-ROC: **0.9989**

---

### Overfitting Analysis
- Gap: **0.0189**
- Interpretation:
  - **Excellent generalization**

---

## Visualization

### Included Plots
- Confusion Matrix
- Feature Importance Plot

---

### Key Features Identified
- mood_score → 0.3195
- acne_severity → 0.1776
- stress_score → 0.1590
- cycle_phase → 0.1108
- pcod_severity → 0.0961

---

## Prediction System

### Method: `predict_flare_risk()`

#### Input
- New user data (symptoms + lifestyle)

#### Output
- Prediction:
  - Flare / No Flare
- Probability score
- Risk level:
  - Low / Medium / High
- Recommendation
- Confidence score

---

---

## Key Evaluation Findings

### Confusion Matrix
- High:
  - Precision
  - Recall
  - F1-score
- Balanced classification:
  - Flare vs No Flare

---

### Feature Importance Ranking
1. mood_score
2. acne_severity
3. stress_score
4. cycle_phase
5. pcod_severity

---

## Test Prediction

### Example Case
- Prediction:
  - **No Flare**
- Probability:
  - **0.1232 (12.3%)**
- Risk Level:
  - **Low**

---

### Includes
- Trained model
- Scaler
- Label encoders

---

## Model Loading

### Function
- `load_xgboost_predictor()`

### Purpose
- Load saved model for:
  - Instant predictions
  - Deployment

---

---

## Final Performance Insight

- Model described as:
  - **"OUTSTANDING - Clinical-grade performance"**
  - **"EXCELLENT generalization"**
- Capabilities:
  - Accurate classification
  - Reliable predictions
  - Real-world applicability

---

## Key Insight
- Combines:
  - **Robust preprocessing**
  - **Optimized XGBoost model**
- Achieves:
  - High accuracy (~98%)
  - Near-perfect AUC
  - Explainable AI predictions
