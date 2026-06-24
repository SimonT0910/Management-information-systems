# Cybersecurity Incident Severity Predictor & Analytics Pipeline

## Project Overview
This repository contains an end-to-end Machine Learning and Data Science pipeline designed to predict, classify, and cluster the severity level (`IMPORTANCIA`) of cyber attacks registered in Colombia (historical records spanning from 2019 to 2025). 

The goal of this project is to build an automated operational alerting system that helps organizations evaluate cyber threats in real-time. By leveraging both **Supervised Machine Learning** (Classification) and **Unsupervised Learning** ($K$-Means Clustering + PCA), the project provides deep insights into how attack vectors behave across different administrative sectors, regions, and taxonomies (e.g., phishing, malware, fraud).

---

## Core Features & Architectural Workflow

1. **Automated Preprocessing:** Comprehensive data cleanup managing missing values, categorical encoding for high-cardinality features (`LabelEncoder`), and structural feature scaling (`StandardScaler`).
2. **Model Benchmarking:** Dynamic performance comparison using a stratified train-test split between a **Random Forest Classifier** and an optimized **XGBoost Classifier**. 
3. **Unsupervised Threat Profiling:** Multi-dimensional cluster discovery via the **Elbow Method** using $K$-Means to isolate behavioral patterns in attack vectors.
4. **Dimensionality Reduction:** Structural compression using **Principal Component Analysis (PCA)** to project high-dimensional cyber threat characteristics onto static 2D space visualizations.
5. **Real-Time Simulation Engine:** An end-to-end production-ready code block that takes a raw, custom incident JSON payload, dynamically matches it to its structural cluster, and predicts its overall severity level to trigger operational priorities.

---

## Technical Stack
* **Language:** Python 3.x
* **Data Processing & Analytics:** Pandas, NumPy, Scikit-Learn
* **Gradient Boosting Engine:** XGBoost
* **Visual Annotations & Plotting:** Matplotlib, Seaborn, Plotly Express

---

## Methodology & How It Works

### Phase 1: Classification Strategy (Supervised Learning)
The pipeline isolates the feature matrix `X` (comprising parameters like sector, entity type, region, taxonomy, and date) to target the label vector `y` (`IMPORTANCIA`). 
* The system evaluates both model architectures simultaneously on test metrics (`Accuracy Score` and `Classification Report`).
* It automatically flags the highest-performing model to execute the downstream inference tasks.
* A normalized feature importance plot isolates the top 5 structural variables driving the severity classification.

### Phase 2: Behavioral Clustering (Unsupervised Learning)
To understand trends without human-labeled parameters, the dataset passes through a $K$-Means clustering routine:
* **The Elbow Method** is plotted utilizing inertia scores to justify the optimal breakdown into 4 distinct incident clusters.
* **PCA Components 1 & 2** are mapped to evaluate spatial density and cluster boundaries, overlaying structural cluster groupings against factual historical importance markings.

### Phase 3: Live Inference Execution
The deployment simulator processes new incoming unstructured incident payloads seamlessly:
1. It validates categorical string matching against baseline historical vocabulary parameters.
2. It executes sequential transformations mirroring training scale states.
3. It pushes the clean array through the top-performing model to return categorical flags (`Muy Grave`, `Grave`, `Menor`, `Solicitud`), automatically establishing operational SLA reaction thresholds.

---

## Repository Directory Map
* `cybersecurity_analysis.ipynb`: Completely documented, production-ready Google Colab notebook with built-in remote dataset streaming.
* `DatasetClean_actualizado.xlsx`: Structured, preprocessed historical data tracking cyber events.
* `README.md`: System architectural documentation.
