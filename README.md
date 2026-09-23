# 🛡️ Guardian Risk Intelligence

> **An Autonomous Enterprise Risk Intelligence Agent** that continuously monitors operational, financial, legal, cybersecurity, and environmental risks — predicts severity using ML, maps relationships via graph analytics, and auto-generates mitigation strategies using Gemini AI.

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-0.110+-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![React](https://img.shields.io/badge/React-18-61DAFB?style=for-the-badge&logo=react&logoColor=black)
![Vite](https://img.shields.io/badge/Vite-5-646CFF?style=for-the-badge&logo=vite&logoColor=white)
![TailwindCSS](https://img.shields.io/badge/TailwindCSS-3-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-3-003B57?style=for-the-badge&logo=sqlite&logoColor=white)
![Gemini](https://img.shields.io/badge/Gemini-AI-4285F4?style=for-the-badge&logo=google&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)

---

## 📖 Table of Contents

- [Overview](#-overview)
- [Key Features](#-key-features)
- [Architecture](#-architecture)
- [Tech Stack](#-tech-stack)
- [Risk Categories](#-risk-categories)
- [Project Structure](#-project-structure)
- [Setup & Installation](#-setup--installation)
- [Environment Variables](#-environment-variables)
- [API Endpoints](#-api-endpoints)
- [Machine Learning Model](#-machine-learning-model)
- [Graph Analytics](#-graph-analytics)
- [Gemini AI Integration](#-gemini-ai-integration)
- [Screenshots](#-screenshots)
- [Roadmap](#-roadmap)
- [Contributing](#-contributing)
- [License](#-license)
- [Author](#-author)

---

## 🌟 Overview

**Guardian Risk Intelligence** is an autonomous AI agent designed to act as a **24/7 risk monitoring system** for modern enterprises. It simulates a real-world enterprise risk dashboard by:

1. **Streaming** live risk events from multiple domains (operational, financial, legal, cyber, environmental)
2. **Predicting** the severity of each event using a trained ML classifier
3. **Mapping** risk relationships through graph analytics to identify cascading risks
4. **Generating** actionable mitigation strategies using Google's Gemini AI
5. **Visualizing** everything in a real-time, beautiful React dashboard

This project was built as a **practice-level enterprise AI system** demonstrating the integration of:
- **Streaming data pipelines**
- **Graph analytics**
- **Predictive ML**
- **Large Language Models (LLMs)**

---

## ✨ Key Features

### 🔴 Real-Time Risk Monitoring
- Live streaming of risk events every 3 seconds via WebSockets
- Auto-scroll live feed with pulsing indicators for new events
- Severity-based color coding (Low → Medium → High → Critical)

### 🧠 Predictive ML
- Trained classifier predicts risk severity and risk score
- Feature engineering on risk type, source, historical patterns
- Model saved as `.pkl` and loaded at runtime for fast inference

### 🕸️ Graph Analytics
- Risk events connected as nodes based on shared attributes (type, source, time window)
- Centrality & community detection to find **critical risk hubs**
- Interactive force-directed graph visualization in the UI

### 🤖 AI-Powered Mitigation
- Gemini API generates **custom, contextual mitigation strategies** per risk
- Each strategy includes priority, estimated cost, timeline, and action steps
- Strategies stored in DB for audit trail

### 📊 Enterprise Dashboard
- Live stats (Total Risks, Critical Count, Active Alerts, Mitigations)
- Charts: trend line, severity distribution, category radar, live feed
- Alert center with severity badges and acknowledgment

### 🔐 Authentication
- JWT-based login/register
- Protected routes on both frontend & backend
- Role-based access (Admin / Analyst)

---

## 🏗️ Architecture


---

## 🛠️ Tech Stack

| Layer | Technology | Purpose |
|-------|-----------|---------|
| **Backend** | Python 3.10+, FastAPI | REST API + WebSocket server |
| **Frontend** | React 18, Vite | Fast, modern SPA |
| **Styling** | TailwindCSS, Framer Motion | Beautiful animations |
| **Database** | SQLite + SQLAlchemy | Lightweight, zero-setup DB |
| **ML** | scikit-learn, pandas, numpy | Severity prediction |
| **Graph** | NetworkX | Risk relationship analysis |
| **AI** | Google Gemini API | Mitigation strategy generation |
| **Streaming** | WebSockets (FastAPI) | Real-time event push |
| **Charts** | Recharts | Beautiful analytics charts |
| **Graph Viz** | react-force-graph-2d | Interactive graph rendering |
| **Icons** | lucide-react | Modern icon set |
| **Auth** | JWT (python-jose, passlib) | Secure authentication |

---

## 🎯 Risk Categories

The agent monitors **5 core enterprise risk domains**:

| # | Category | Icon | Example Events |
|---|----------|------|----------------|
| 1 | **Operational** | ⚙️ | Factory downtime, supply chain failure, equipment outage |
| 2 | **Financial** | 💰 | Stock crash, cash flow issues, fraud detection |
| 3 | **Legal** | ⚖️ | New regulations, lawsuits, compliance violations |
| 4 | **Cybersecurity** | 🔒 | Data breach, DDoS attack, phishing, ransomware |
| 5 | **Environmental** | 🌱 | Pollution, climate risk, carbon tax, ESG violations |

Each event carries:
- **Severity**: Low / Medium / High / Critical
- **Risk Score**: 0–100 (predicted by ML)
- **Source**: System / Sensor / Report / External Feed
- **Timestamp**: ISO 8601 UTC

---

## 📁 Project Structure


---

## 🚀 Setup & Installation

### Prerequisites

- **Python** 3.10 or higher
- **Node.js** 18 or higher
- **Git**
- **Google Gemini API Key** → [Get it free here](https://aistudio.google.com/app/apikey)

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/vishakha2121/guardian-risk-intelligence.git
cd guardian-risk-intelligence

cd backend

# Create virtual environment
python -m venv venv

# Activate (Windows)
venv\Scripts\activate

# Activate (Mac/Linux)
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Create .env file
copy .env.example .env      # Windows
cp .env.example .env        # Mac/Linux
# Now edit .env and add your GEMINI_API_KEY

# Initialize DB & seed data
python -m app.utils.seed_data

# Train ML model (one-time)
python -m app.ml.train_model

# Run backend
uvicorn app.main:app --reload --port 8000

cd frontend

# Install dependencies
npm install

# Create .env
copy .env.example .env      # Windows
cp .env.example .env        # Mac/Linux

# Run dev server
npm run dev