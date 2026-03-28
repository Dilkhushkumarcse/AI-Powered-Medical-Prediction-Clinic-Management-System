---

#  AI-Powered Medical Prediction & Clinic Management System

An **AI-powered healthcare platform** that predicts multiple diseases using a **Random Forest ML model**, supports **role-based dashboards (Admin, Doctor, Patient)**, and enables **secure doctor–patient interaction** via dashboards and chat.

---

##  Key Features

### Role-Based Authentication

* **Admin** – Full system control
* **Doctor** – Patient management & treatment notes
* **Patient (User)** – Disease prediction & doctor assignment

###  AI Disease Prediction

* Uses **Random Forest Classifier**
* Predicts diseases with probability scores
* Admin-defined **custom thresholds** for classification
* Supports explainability (SHAP / LIME ready)

###  Dashboards

* **Admin Dashboard**

  * User & doctor management
  * Disease threshold tuning
  * Prediction logs & analytics
* **Doctor Dashboard**

  * Assigned patient list
  * Prediction history
  * Treatment notes
  * Real-time chat with patients
* **Patient Dashboard**

  * Health form submission
  * Disease prediction results
  * Doctor assignment & chat
  * Personal history

---

##  Machine Learning Model

### 🔹 Algorithm

* **Random Forest Classifier**

### 🔹 Input Features

```
Age, BMI, BP, Heart Rate, HbA1c, Glucose,
LDL, HDL, Triglycerides, Hemoglobin,
TSH, Depression Score, Sex, Smoking, Symptoms
```

### 🔹 Output

* Disease probabilities (e.g., Diabetes, Heart Disease, Kidney Disease)
* Final result based on admin-defined thresholds

---

## System Flow

1. **Patient enters health data (Streamlit UI)**
2. **Preprocessing pipeline** (scaling, encoding)
3. **Random Forest prediction**
4. **Threshold comparison**
5. **Prediction stored in DB**
6. **Doctor views patient & adds treatment**
7. **Admin monitors entire system**

---

## Project Structure

```
AIClinic/
│
├── app.py                  # Main Streamlit app
├── model_utils.py          # Load model & prediction logic
├── explain.py              # SHAP / LIME explanations
├── audit.py                # Database & logging utilities
├── auth.py                 # Authentication & user management
├── utils.py                # Helper utilities
├── requirements.txt        # Python dependencies
│
├── App/                    # FastAPI backend
│   ├── app.py
│
├── data/
│   ├── full_pipeline_rf.pkl
│   ├── label_cols.pkl
│   └── best_thresholds.pkl
│
├── profile_pics/           # Doctor profile images
├── users.db                # SQLite database
└── static/                 # CSS / images (optional)
```

---

## Environment Setup (Windows)

### 🔹 Step 1: Activate Virtual Environment

```powershell
.\ai-powered\Scripts\activate
```

You should see:

```
(ai-powered)
```

---

### 🔹 Step 2: Install Dependencies

```bash
pip install -r requirements.txt
```

---

##  Run Backend (FastAPI)

### 🔹 Set Admin Token

```powershell
setx ADMIN_TOKEN "2200421"
```

Restart terminal after setting.

### 🔹 Start API Server

```bash
python -m uvicorn App.app:app --reload --port 8000
```

---

## Run Dashboards (Streamlit)

### 🔹 Activate Environment (from App folder)

```powershell
& "..\ai-powered\Scripts\Activate.ps1"
```

### 🔹 Run Main Dashboard

```bash
streamlit run dashboard.py
```

### 🔹 Run Clinic Dashboard

```bash
streamlit run ai_clinic_dashboard.py
```

---

## Default Login Credentials

### 🔹 Admin

```
Username: admin1 / admin5
Password: 123
```

### 🔹 Doctor

```
Username: doctor1
Password: 123
```

### 🔹 Patient (User)

```
Username: admin0
Password: 123
```

---

##  Database Design (SQLite)

### 🔹 User Table

| Field         | Type | Notes                 |
| ------------- | ---- | --------------------- |
| id            | INT  | Primary Key           |
| username      | TEXT | Unique                |
| password_hash | TEXT | Hashed                |
| role          | TEXT | Admin / Doctor / User |
| name          | TEXT | Full name             |
| email         | TEXT | Optional              |
| profile_info  | JSON | Extra info            |

---

##  Admin Dashboard Highlights

*  Circular profile image upload (≤1MB)
*  Gradient sidebar UI
*  System analytics cards
*  User & role management
*  Disease threshold sliders
*  Prediction logs
*  Stable SQLite migrations

---

##  Tech Stack

* **Frontend**: Streamlit
* **Backend**: FastAPI
* **ML**: Scikit-learn (Random Forest)
* **Database**: SQLite
* **Auth**: Session-based + hashed passwords
* **Explainability**: SHAP / LIME (optional)

---

##  Future Enhancements

* JWT authentication
* Cloud deployment (AWS / Azure)
* Model retraining pipeline
* Email notifications
* Mobile-friendly UI

---

##  Author

**Dilkhush Kumar**
Computer Science Engineering
AI | Machine Learning | Data Science

---

