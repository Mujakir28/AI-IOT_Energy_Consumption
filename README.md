# AI–IoT Convergence for Smart Home Energy Optimisation (Privacy-Preserving)

This repository contains the source code for a research study on smart home energy forecasting and optimisation using an AI–IoT pipeline with a federated learning simulation to support privacy-by-design. The workflow is implemented in Google Colab and is designed to handle large household energy datasets (e.g., ~500MB CSV files) using chunk-based loading and resampling.

## What this project does
The notebook/code:
- Loads a large smart home electricity dataset (timestamp + aggregate + appliance channels)
- Cleans and preprocesses the data (quality filtering using `Issues`, resampling to 1-minute intervals)
- Performs exploratory analysis and generates figures (profiles, distributions, correlations)
- Builds features (time features, lag features, rolling statistics)
- Trains and evaluates forecasting models (baseline + ML models)
- Simulates federated learning (FedAvg-style) to demonstrate privacy-preserving training
- Produces tables and plots used in the research report

## Dataset format expected
A CSV file with (at minimum) the following columns:
- `Time` (timestamp)
- `Aggregate` (whole-home demand)
- `Appliance1` ... `Appliance9` (optional but supported)
- `Issues` (data quality flag; rows with `Issues != 0` are excluded)

> Note: If your dataset uses different column names, update the `usecols` list in the notebook/script.

## How to run (Google Colab)
1. Open the notebook in Google Colab.
2. Upload your dataset CSV (or mount Google Drive).
3. Set the dataset path in the code (e.g., `DATA_PATH = "/content/CLEAN_House1.csv"`).
4. Run all cells from top to bottom.
5. Figures and tables will be displayed in the notebook and may be exported to an `outputs/` folder (if enabled in the code).

## Outputs
Typical outputs include:
- Missing values summary and descriptive statistics
- Time-series plots (week/month examples)
- Daily/weekly profiles and distribution plots
- Correlation heatmap and appliance contribution chart
- Model performance table (MAE, RMSE, MAPE, R²)
- Forecast vs actual plots and residual diagnostics
- Federated learning round-by-round performance plots (if enabled)

## Project structure (example)
- `notebooks/` — Colab notebook(s)
- `src/` — reusable Python modules (if you split the notebook)
- `outputs/` — exported tables/figures (optional)
- `README.md` — this file
