# Task 03 — Feature Engineering & Preprocessing Pipeline

**RabTech Academy AI/ML Internship**

## Files
- `feature_engineering.ipynb` — step-by-step Jupyter notebook.
- `customer_churn_training.csv` — CSV supplied for this task.
- `requirements.txt` — required Python packages.

## Run from scratch
1. Install Python 3.10+ (Python 3.12 recommended).
2. Open a terminal in this folder.
3. Install dependencies: `python -m pip install -r requirements.txt`
4. Start Jupyter: `jupyter notebook`
5. Open `feature_engineering.ipynb` and select **Run All**.

## Method
The target (`churned`) and identifier (`customer_id`) are excluded from model inputs. Data is split before preprocessing is fitted. Numeric features use median imputation and standard scaling; categorical features use most-frequent imputation and one-hot encoding. A Random Forest pipeline is compared with a majority-class baseline. Correlation and feature-importance plots are included.

## Limitation
The supplied CSV has 12 rows only. Metrics are a workflow demonstration and should not be used to claim real-world performance. Dataset provenance, consent, license, and churn definition were not supplied and should be verified with the provider.
