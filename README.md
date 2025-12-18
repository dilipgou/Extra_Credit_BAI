# Temporal Airbnb Seasonality and Modeling

**Course:** EAS 510 – Basics of AI
**Assignment:** Extra Credit – Temporal Airbnb Seasonality and Modeling

---

## 📌 Project Overview

This project analyzes **temporal seasonality patterns** in Airbnb markets using **Inside Airbnb calendar and listings data**. A night-level panel dataset is constructed to study how **prices and booking probabilities** vary across months, weekends, and listing characteristics. The project further evaluates **time-aware predictive models** using both **XGBoost** and **Neural Networks**, with training monitored using **TensorBoard**.

The primary goal is to demonstrate:

* Proper construction of a temporal panel dataset
* Seasonality analysis and visualization
* Realistic temporal train/validation/test splits
* Model comparison and generalization to future months

---

## 📂 Repository Structure

```
├── airbnb_temporal_analysis.ipynb   # Final notebook with analysis and models
├── README.md                        # Project overview and instructions
├── requirements.txt                 # Python dependencies
├── images/                          # TensorBoard screenshots
│   ├── nn_price_loss.png
│   └── nn_booking_accuracy.png
```

---

---

## Data Download Instructions (InsideAirbnb)

**Raw data is NOT included in this repository.** To reproduce the analysis, download data directly from the InsideAirbnb “Get the Data” page. For each city, you must first click **“Show archived data for this city”** on the site to reveal older snapshots, then choose the correct dates. [file:52]

For each city below, download **`listings.csv.gz`** and **`calendar.csv.gz`** for the specified archived dates:

- **Austin**
- 2025‑03‑06  
- 2024‑12‑14
- **Chicago**
- 2025‑03‑11  
- 2024‑12‑18
- **Santa Cruz**
- 2025‑03‑28  
- 2025‑12‑31
- **Washington, DC**
- 2025‑03‑13  
- 2025‑12‑18

---

## 📊 Data Sources

Data comes from **Inside Airbnb** ([https://insideairbnb.com/get-the-data/](https://insideairbnb.com/get-the-data/)).

For each city, both `listings.csv` and `calendar.csv` were downloaded for the following archived snapshot dates:

* **Austin:** December 14, 2024 and March 6, 2025
* **Chicago:** December 18, 2024 and March 11, 2025
* **Washington, DC:** March 13, 2025 and December 18, 2025
* **Santa Cruz:** March 28, 2025 and December 31, 2025

⚠️ **Note:** Raw CSV files are not included in this repository to comply with assignment guidelines. The notebook documents how to download and load the data.

---

## 🛠️ Methodology Summary

### 1. Night-Level Panel Dataset

* Merged `calendar.csv` with `listings.csv` using a left join on `listing_id`
* Cleaned and transformed price and availability variables
* Created time-based features: month, day of week, week of year, day of year, and weekend indicator

### 2. Seasonality Analysis

* Average price by month
* Average booking probability by month
* Weekend vs weekday comparisons
* Price trends by room type

### 3. Temporal Train / Validation / Test Split

* **Train:** January–September
* **Validation:** October–November
* **Test:** December–February

This split prevents temporal leakage and reflects realistic forecasting conditions.

### 4. Modeling

* **XGBoost:**

  * Regressor for price prediction
  * Classifier for booking prediction
* **Neural Networks:**

  * Feedforward regression network (MSE loss)
  * Feedforward classification network (binary crossentropy)

### 5. ## TensorBoard Visualizations

### Neural Network – Price Prediction
**epoch_loss** (training vs validation) shows stable convergence with minimal divergence, indicating limited overfitting under a temporal split.

<img width="1070" height="502" alt="Screenshot 2025-12-18 171512" src="https://github.com/user-attachments/assets/28fb2acf-a1c3-4742-86d8-7d62a453cfc9" />

### Neural Network – Booking Prediction
**epoch_accuracy** shows stable validation accuracy across epochs, reflecting the noisy but learnable nature of booking prediction.

<img width="870" height="512" alt="Screenshot 2025-12-18 171439" src="https://github.com/user-attachments/assets/169993ec-d0ce-4bce-90c0-9f62518a1ff3" />

### XGBoost – Price Model
**evaluation_loss_vs_iterations** demonstrates steady improvement across boosting rounds, confirming effective optimization.

<img width="1065" height="532" alt="Screenshot 2025-12-18 171548" src="https://github.com/user-attachments/assets/8273f308-0270-4c9a-84ce-2809a828b1ca" />

XGBoost – Price Model
evaluation_accuracy_vs_iterations fluctuates slightly across boosting rounds while remaining relatively stable overall, indicating modest but consistent predictive performance without clear overfitting.

<img width="1063" height="510" alt="Screenshot 2025-12-18 171527" src="https://github.com/user-attachments/assets/6cb9fc9e-3136-48f4-9b2a-b1e2004679a9" />

---

## 📈 Key Findings

* Strong **weekend effects** on both price and booking probability
* Moderate **seasonal variation** across months
* XGBoost models perform strongly on tabular data
* Neural networks require feature scaling but show stable training dynamics when properly configured
* Temporal splits provide a realistic assessment of generalization to future months

---

## ▶️ How to Run the Project

1. Clone the repository
2. Install dependencies:

```bash
pip install -r requirements.txt
```

3. Download Inside Airbnb data for the required cities and snapshot dates
4. Place data files in a local `data/` directory (not tracked by git)
5. Open and run `airbnb_temporal_analysis.ipynb`

---

## 📦 Requirements

All required packages are listed in `requirements.txt`. Key libraries include:

* pandas
* numpy
* matplotlib
* scikit-learn
* xgboost
* tensorflow

---

## ✅ Assignment Compliance

This repository satisfies all requirements for the **EAS 510 Extra Credit Assignment**, including:

* Temporal dataset construction
* Seasonality analysis and plots
* Time-aware model training and evaluation
* TensorBoard usage with visual evidence
* Final written analysis and business insights

---


