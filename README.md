# PCOD Conversational AI Assistant

A lightweight conversational AI assistant for **PCOD (Polycystic Ovarian Disease)** flare-up prediction and lifestyle management.  
Combines **Machine Learning (XGBoost)** and **Conversational AI (DialoGPT)** for intelligent health support.

---

## Definition
- AI-based system that:
  - Predicts **PCOD flare-up risk**
  - Provides **personalized lifestyle recommendations**
  - Offers **educational guidance**
  - Enables **natural language interaction**

---


---

### Core Components

#### 1. Data Layer
- Synthetic datasets:
  - `pcod_flareup_dataset.csv`
  - `user_habits_pcod_flare.csv`
- ~6,350 records with:
  - Symptoms (acne, mood, weight)
  - Lifestyle (sleep, stress, activity)
  - Cycle data (cycle phase)
- 24+ features

---

#### 2. Machine Learning Layer
- Models used:
  - **XGBoost (Primary Model)**
  - LightGBM, CatBoost (comparison)
- Input:
  - Preprocessed user features
- Output:
  - Flare prediction (Yes/No)
  - Probability score

---

#### 3. Deep Learning Layer (Hybrid Models)
- Models:
  - LSTM + Static Features
  - GRU + Static Features
- Purpose:
  - Capture **temporal patterns**
- Accuracy:
  - ~88.7%

---

#### 4. Conversational AI Layer
- Base Model:
  - **DialoGPT-small (117M parameters)**
- Fine-tuned on:
  - 3,424 conversational examples
- Categories:
  - Risk Assessment (44%)
  - Lifestyle Advice (44%)
  - Educational (12%)

---

#### 5. Prediction & Recommendation Engine
- Converts ML output into:
  - Risk Levels:
    - Low
    - Medium
    - High
- Generates:
  - Personalized advice
  - Trigger explanations
  - Confidence score

---

## Process / Workflow

### Step-by-Step Flow
1. User inputs:
   - Symptoms + lifestyle data OR query
2. Data preprocessing:
   - Encoding categorical variables
   - Feature scaling
3. ML prediction:
   - XGBoost predicts flare probability
4. Risk classification:
   - Threshold-based categorization
5. Conversational response:
   - DialoGPT generates natural reply
6. Output:
   - Risk level + recommendations + explanation

---

## Features

- 🔮 **Risk Assessment**
  - Predicts flare-up probability
- 💡 **Lifestyle Recommendations**
  - Personalized health advice
- 📚 **Educational Support**
  - Answers PCOD-related questions
- 💬 **Conversational Interface**
  - Natural language interaction
- ⚡ **Lightweight Deployment**
  - Works on CPU (mobile-friendly)

---

## Model Performance

### Traditional ML Models
- XGBoost:
  - F1 Score: **0.9972**
  - Accuracy: **0.9811**
  - AUC-ROC: **0.9989**
- LightGBM:
  - F1 Score: **0.9953**
- CatBoost:
  - F1 Score: **0.9972**

---

### Deep Learning Models
- LSTM + Static:
  - Accuracy: **88.70%**
- GRU + Static:
  - Accuracy: **88.70%**

---

### Overfitting Check
- Gap: **0.0189**
- Indicates:
  - **Excellent generalization**

---

## Key Predictive Features

- mood_score → 0.3195
- acne_severity → 0.1776
- stress_score → 0.1590
- cycle_phase → 0.1108
- pcod_severity → 0.0961

---

## Model Pipeline (XGBoost)

### Steps
1. Load dataset
2. Drop irrelevant columns:
   - user_id, date, etc.
3. Encode categorical features:
   - LabelEncoder
4. Scale features:
   - StandardScaler
5. Train model:
   - XGBClassifier
6. Evaluate:
   - Accuracy, F1, AUC
7. Save model:
   - `.pkl` file

---

## Testing Summary

### Risk Distribution
- High Risk: **70%**
- Low Risk: **30%**
- Medium Risk: **0% (in tests)**

---

### Scenario Insights

#### High Risk Cases
- High stress professionals
- Students during exams
- Postpartum women
- Irregular schedule workers

#### Low Risk Cases
- Athletes
- Well-managed lifestyle users
- Minimal symptom profiles

---

## Analysis Insights

### Stress Impact
- Low Stress (3/10) → 18.1% risk
- Medium Stress (6/10) → 82.7% risk
- High Stress (9/10) → 97.4% risk

---

### Cycle Phase Impact
- Follicular → 99.2%
- Ovulation → 98.9%
- Luteal → 98.1%
- Menstrual → 82.7%

---

## Applications / Use Cases

- 🏥 Personal health monitoring
- 📱 Mobile health assistant
- 👩‍⚕️ Clinical decision support (assistive)
- 📊 Lifestyle tracking apps
- 🤖 AI chatbot integration

---

## Advantages

- High accuracy (near clinical-grade)
- Personalized recommendations
- Real-time predictions
- Lightweight and deployable locally
- Combines ML + NLP

---

## Limitations

- Uses synthetic dataset
- Not a replacement for medical diagnosis
- Limited real-world validation
- Deep learning models underperform vs ML

---

## Future Enhancements

- Integration with wearable devices
- Real-time health tracking
- Multilingual support
- Deployment as mobile/web app
- Real clinical dataset integration

---

## Quick Start

### 1. Setup Environment
```bash
# Option A
chmod +x setup.sh
./setup.sh

# Option B
python -m venv pcod_llm_env
source pcod_llm_env/bin/activate  # Windows: pcod_llm_env\Scripts\activate
pip install -r requirements.txt

# Interactive
python pcod_chatbot.py

# Test mode
python pcod_chatbot.py test

Example
Risk Assessment
User: I'm sleeping 5 hours and stressed.
Assistant: HIGH risk. Improve sleep and reduce stress.
Lifestyle Advice
User: Stress = 80, day 20 cycle
Assistant: Practice meditation, manage luteal phase symptoms.
Educational
User: Foods to avoid?
Assistant: Avoid high glycemic foods like sugar and white bread.
