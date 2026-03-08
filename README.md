# Diabetes Screening Tool for Low-Resource Settings

## Overview

This project is an **end-to-end machine learning deployment system**
that demonstrates how an ML model can move from a research notebook into
a **production-ready cloud application**.

The system predicts **diabetes risk probability** using non‑laboratory
indicators such as:

-   Age
-   Gender
-   BMI
-   Smoking history
-   Hypertension
-   Heart disease

The aim is to explore how **data‑driven screening tools** could support
early risk identification in **low‑resource environments** where
laboratory tests may not always be available.

⚠️ **Important:**\
This project is **not a medical device and not intended for clinical
diagnosis**. It is a technical demonstration of an ML deployment
pipeline.

------------------------------------------------------------------------

# Live Application

**Streamlit App**\
https://diabetes-screening-project.streamlit.app/

**API Documentation**\
http://35.179.154.100:8000/docs

**Docker Image**\
https://hub.docker.com/r/ofemimike/diabetes-screener-app

------------------------------------------------------------------------

# Project Architecture

User (Browser) → Streamlit Frontend\
→ FastAPI Backend (ML Inference API)\
→ Machine Learning Model\
→ Prediction Response

Deployment stack:

FastAPI\
→ Docker Container\
→ AWS EC2 Server\
→ Public API\
→ Streamlit Frontend

------------------------------------------------------------------------

# Tech Stack

**Machine Learning** - Python - Scikit-learn - Pandas - NumPy

**Model Serving** - FastAPI - Uvicorn

**Deployment** - Docker - Docker Hub - AWS EC2

**Frontend** - Streamlit

------------------------------------------------------------------------

# Machine Learning Model

The model was designed for **screening rather than diagnosis**.

Key design decisions:

-   Random Forest classifier
-   Feature set excludes laboratory diagnostic variables
-   Model optimized for **high recall**

Why recall?

In screening scenarios, **missing a true diabetes case is more costly
than generating false positives.**\
Therefore the decision threshold was tuned to prioritize sensitivity.

------------------------------------------------------------------------

# API Endpoints

### Health Check

GET /

Returns API status.

### Diabetes Screening

POST /screen-diabetes

Example request:

{ "age": 45, "gender": "Male", "height": 1.72, "weight": 80,
"smoking_history": "former", "hypertension": "Yes", "heart_disease":
"No" }

Example response:

{ "diabetes_risk_probability": 0.63, "screening_result": "High Risk",
"screening_threshold": 0.5 }

------------------------------------------------------------------------

# Running the Project Locally

## Clone Repository

git clone
https://github.com/OfemiAdeniyi/Diabetes-Screening-Tool-for-Low-Resouce-Settings.git

cd Diabetes-Screening-Tool-for-Low-Resouce-Settings

## Create Virtual Environment

python -m venv venv

Activate:

Linux/Mac: source venv/bin/activate

Windows: venv`\Scripts`{=tex}`\activate`{=tex}

## Install Dependencies

pip install -r requirements.txt

## Run FastAPI Server

uvicorn main:app --reload

Open:

http://127.0.0.1:8000/docs

------------------------------------------------------------------------

# Running with Docker

Build image:

docker build -t diabetes-screener .

Run container:

docker run -p 8000:8000 diabetes-screener

Or pull the image:

docker pull ofemimike/diabetes-screener-app

Run:

docker run -p 8000:8000 ofemimike/diabetes-screener-app

------------------------------------------------------------------------

# Cloud Deployment

The API is deployed on **AWS EC2**.

Deployment workflow:

1.  Build Docker image
2.  Push image to Docker Hub
3.  Launch EC2 instance
4.  Pull Docker image on the server
5.  Run container exposing port 8000

This makes the ML model accessible as a **live cloud API**.

------------------------------------------------------------------------

# Frontend Application

A lightweight **Streamlit interface** allows users to input patient
information and instantly receive a **diabetes risk screening result**.

------------------------------------------------------------------------

# Learning Journey

This project also represents a **learning milestone**.

After being advised that **Streamlit alone is not production-grade for
ML deployment**, I set out to learn:

-   FastAPI
-   Docker
-   Cloud deployment

This project became my **first complete end‑to‑end ML system**,
covering:

Model development → API creation → Containerization → Cloud deployment.

------------------------------------------------------------------------

# Future Improvements

Potential enhancements:

-   Model monitoring
-   API authentication
-   HTTPS with domain routing
-   CI/CD pipeline
-   Expanded dataset validation

------------------------------------------------------------------------

# Disclaimer

This project is **for educational and research purposes only**.

It is **not a licensed medical tool** and has not undergone medical
validation or regulatory approval. It should **not be used for clinical
decision-making**.

------------------------------------------------------------------------

# Author

**Ofemi Adeniyi**

Machine Learning \| Data Science \| HealthTech

GitHub:\
https://github.com/OfemiAdeniyi
