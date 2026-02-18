# 🌸 Iris ML Classifier - Fullstack Project

A fullstack machine learning application that predicts Iris flower species using Random Forest classifier.

## 🛠️ Tech Stack

| Layer | Technology |
|-------|------------|
| **Backend** | FastAPI, SQLAlchemy, PostgreSQL |
| **Frontend** | React, Vite, Axios |
| **ML** | Scikit-learn (Random Forest) |

## 📁 Project Structure

```
ProjectFullStack/
├── backend/
│   ├── app/
│   │   ├── main.py          # FastAPI endpoints
│   │   ├── database.py      # PostgreSQL connection
│   │   ├── models.py        # SQLAlchemy models
│   │   ├── schemas.py       # Pydantic schemas
│   │   └── ml_model.py      # ML prediction
│   ├── train_model.py       # Model training script
│   └── requirements.txt
└── frontend/
    ├── src/
    │   ├── App.jsx
    │   └── components/
    └── package.json
```

## 🚀 Quick Start

### Prerequisites
- Python 3.10+
- Node.js 18+
- PostgreSQL running locally

### 1. Setup Database

```bash
# Create the database (PostgreSQL should be running)
psql -U postgres -c "CREATE DATABASE iris_ml;"
```

### 2. Setup Backend

```bash
cd backend

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Train the ML model
python train_model.py

# Start the server
uvicorn app.main:app --reload --port 8000
```

### 3. Setup Frontend

```bash
cd frontend

# Install dependencies
npm install

# Start dev server
npm run dev
```

### 4. Access the App

- **Frontend**: http://localhost:5173
- **Backend API**: http://localhost:8000
- **API Docs**: http://localhost:8000/docs

## 🔌 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/predict` | Make species prediction |
| `GET` | `/predictions` | Get prediction history |
| `GET` | `/model-info` | Get model information |

### Example Request

```bash
curl -X POST "http://localhost:8000/predict" \
  -H "Content-Type: application/json" \
  -d '{"sepal_length": 5.1, "sepal_width": 3.5, "petal_length": 1.4, "petal_width": 0.2}'
```

## 📊 Model Details

- **Algorithm**: Random Forest Classifier
- **Dataset**: Iris (150 samples, 3 classes)
- **Train/Test Split**: 80/20
- **Expected Accuracy**: ~96%

## 🔧 Database Configuration

| Parameter | Value |
|-----------|-------|
| Host | localhost |
| Port | 5432 |
| Database | iris_ml |
| Username | postgres |
| Password | root |
