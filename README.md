# Project: Building a Robust MLOps Pipeline for Titanic Survival Prediction

**Course:** ID5003W | **Academic Year:** 2025 | **Institution:** IIT Madras

---
# advanced-mlops-titanic
A complete MLOps pipeline to train, deploy, and maintain a classification model. The pipeline handle large datasets efficiently and adapt to new data over time. It addresses the entire model lifecycle, from data ingestion to production monitoring.

---

## How to Set Up and Run

## 1. Project Overview

This project implements a complete, end-to-end MLOps pipeline to train, deploy, and monitor a machine learning model for predicting passenger survival on the Titanic. The focus is on automation, reproducibility, and robustness, using tools like Apache Spark, DVC, MLflow, and Docker.

---

## 2. Final Architecture

*(Here, you should insert the high-level diagram of your pipeline as required by the deliverables.)*

![Pipeline Architecture Diagram](path/to/your/diagram.png)

---

## 3. How to Set Up and Run

### Prerequisites

- Git
- Python 3.9+
- DVC (`pip install dvc`)
- Docker

### Installation & Setup

1.  **Clone the Repository:**
    ```bash
    git clone https://github.com/YOUR_USERNAME/iitm-mlops-titanic.git
    cd iitm-mlops-titanic
    ```

2.  **Install Python Dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

3.  **Download the Data:**
    Use DVC to pull the dataset tracked from our remote storage.
    ```bash
    dvc pull
    ```
    This will download `titanic.csv` into the `data/` directory.

### Running the Pipeline

1.  **Execute the Main Training Pipeline:**
    This script will run the entire pipeline: data preprocessing, training, evaluation, and model registration in MLflow.
    ```bash
    python src/train.py
    ```

2.  **Run the MLflow UI:**
    To inspect the experiments, open a new terminal and run:
    ```bash
    mlflow ui
    ```
    Navigate to `http://127.0.0.1:5000` in your browser.

### Running the API

1.  **Build the Docker Image:**
    From the root of the project, build the Docker image for the API.
    ```bash
    docker build -t titanic-api .
    ```

2.  **Run the Docker Container:**
    ```bash
    docker run -p 5001:5000 titanic-api
    ```
    *Note: We map to port 5001 on the host to avoid collision with the MLflow UI.*

3.  **Test the API:**
    Use the provided script to send a sample request to the running API.
    ```bash
    python scripts/test_api.py
    ```