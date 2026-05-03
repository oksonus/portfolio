
#  AI-Driven Demographic Segmentation Pipeline

An end-to-end data science project bridging **Unsupervised Learning** and **Generative AI** to transform abstract demographic data into actionable business personas. The results are available in outcomes

## 📖 Overview
This project builds a complete segmentation pipeline using demographic datasets. It combines demographic and socio-economic data—including population size, age structure, household size, income levels, and housing costs—to identify and interpret regional trends.

This pipeline solves a common industry problem by using a **Hybrid ML + GenAI approach**:
*   **Machine Learning:** Identifies hidden structures via KMeans clustering.
*   **Statistical Profiling:** Summarises the mathematical characteristics of each group.
*   **Generative AI:** Translates abstract cluster statistics into human-readable, business-friendly personas.

##  Methodology

### 1. Data Preparation & Engineering
The project utilizes a **Medallion Architecture** within **Databricks** to ensure data quality:
*   **Bronze:** Raw demographic and socio-economic records.
*   **Silver:** Cleaned and standardised features (Income, Rent, Mortgage, etc.).
*   **Gold:** Analysis-ready aggregates with identifiers removed and features scaled.

### 2. Machine Learning Workflow
*   **Feature Scaling:** Applied `StandardScaler` to ensure fair distance calculations.
*   **Clustering:** KMeans identifies distinct segments.
*   **Evaluation:** The **Elbow Method** (Inertia) was used to select the optimal number of clusters ($k=4$).
*   **Profiling:** Aggregated feature means per cluster to create statistical summaries.

### 3. Persona Generation (GenAI)
The pipeline feeds cluster statistics into an **LLM** to convert numerical data into:
*   **Named Segments:** Assigning identities like "Urban Renters."
*   **Narrative Descriptions:** Explaining the lifestyle and financial status of the group.
*   **Behavioral Interpretations:** Providing actionable business insights.


## Tech Stack
*   **Data Engineering:** Databricks, Spark, Delta Lake (Medallion Architecture)
*   **Machine Learning:** Python (pandas, scikit-learn), MLflow
*   **Generative AI:** LLM-based persona generation

## Business Value
*   **Interpretability:** Bridges the gap between data science and business stakeholders.
*   **Targeted Strategy:** Supports urban planning and precision marketing.
*   **Modern Architecture:** Demonstrates a production-ready ML + GenAI integration.


## Note on Repository Contents
To comply with data privacy standards and protect proprietary logic, certain elements of this repository have been redacted:
*   **Sensitive Decisions:** Specific LLM model selections and prompt engineering nuances are omitted.
*   **Data Access:** Underlying datasets are abstracted to prevent exposure of sensitive records.
*   **Execution:** This repository is intended as an ** showcase** of methodology and architecture. Due to the removal of specific credentials and sensitive configurations, the code is not "plug-and-play" ready.

