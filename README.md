# 🚦 Smart Traffic Pattern Forecasting using Decision Trees

Welcome to the **Smart Traffic Forecasting** project, developed during my internship at **TapTap under BlackBucks Pvt. Ltd.** This machine learning solution leverages timestamped traffic data to predict vehicle flow across multiple city junctions. With increasing urban congestion, this project aims to assist city planners, commuters, and administrators in building smarter, sustainable transportation systems.

---

## 📌 Table of Contents
- [🚨 Problem Statement](#-problem-statement)
- [🎯 Objectives](#-objectives)
- [📊 Dataset Overview](#-dataset-overview)
- [⚙️ Methodology](#️-methodology)
- [📈 Feature Engineering](#-feature-engineering)
- [🌲 Model Used](#-model-used)
- [📉 Evaluation Metrics](#-evaluation-metrics)
- [📊 Visualizations](#-visualizations)
- [🌍 Significance](#-significance)
- [🔮 Future Scope](#-future-scope)
- [🛠️ Tech Stack](#-tech-stack)

---

## 🚨 Problem Statement

Urban traffic congestion leads to wasted hours, increased pollution, and inefficient road usage. Traditional control systems do not adapt well to dynamic urban patterns. This project proposes a solution to predict future traffic volume using timestamped traffic data, thereby helping authorities optimize junction performance and guide commuters more efficiently.

---

## 🎯 Objectives

- Predict vehicle count at various traffic junctions using past traffic data.
- Understand which features (time, day, date) influence traffic patterns the most.
- Build an explainable and scalable forecasting solution using Decision Trees.
- Visualize traffic patterns to identify bottlenecks and trends.

---

## 📊 Dataset Overview

We used two primary CSV datasets:

### 🔹 Train Data (`Train data.csv`)
- **DateTime**: Timestamp of observation
- **Junction**: Identifier for the traffic junction
- **Vehicles**: Number of vehicles recorded at that timestamp

### 🔹 Test Data (`Test cases.csv`)
- **DateTime**: Timestamp for prediction
- **Junction**: Junction ID
- **ID**: Unique identifier for each prediction row

---

## ⚙️ Methodology

1. **Data Cleaning**
   - Parsed `DateTime` column into datetime format.
   - Handled any encoding issues using `ISO-8859-1`.

2. **Feature Engineering**
   - Extracted meaningful features:
     - Weekday, Month, Day, Year
     - Time in seconds from midnight
     - Week number
     - Quarter
   - Converted `DateTime` into Unix timestamp.

3. **Modeling**
   - Used `ExtraTreesClassifier` to rank feature importance.
   - Trained a `DecisionTreeClassifier` on the processed data.

4. **Prediction & Evaluation**
   - Predicted traffic for test data using the trained model.
   - Evaluated model performance using:
     - MAE, MSE, RMSE on validation split

---

## 📈 Feature Engineering

From the `DateTime` column, the following features were derived:

| Feature       | Description                             |
|---------------|-----------------------------------------|
| Weekday       | Day of the week (0 = Monday)            |
| Month         | Numeric month (1 to 12)                 |
| Day           | Day of the month                        |
| Year          | Year of the timestamp                   |
| Time          | Seconds elapsed since midnight          |
| Week          | Week number of the year                 |
| Quarter       | Quarter of the year (1 to 4)            |
| Unix Time     | Timestamp in seconds since epoch        |

---

## 🌲 Model Used

### 📌 ExtraTreesClassifier
- Used to determine feature importance.
- Helped us identify that `DateTime`, `Time`, and `Day` were most influential.

### 📌 DecisionTreeClassifier
- Final model for prediction.
- Benefits:
  - High interpretability
  - Captures non-linear temporal relationships

---

## 📉 Evaluation Metrics

After splitting the training data:

| Metric               | Value         |
|----------------------|---------------|
| Mean Absolute Error  | ~7.81         |
| Mean Squared Error   | ~166.13       |
| Root Mean Squared Error | ~12.89     |

---

## 📊 Visualizations

The following plots were generated:

- **Histogram**: Distribution of vehicle count.
- **Time Series**: Traffic trends for each junction.
- **Overlay Plot**: Comparison of predicted vs actual vehicle counts.

Example:
```python
plt.hist(df_train['Vehicles'], bins=range(min(data), max(data) + 1))
plt.title("Traffic Distribution")

## 🌍 Significance

This project provides:

- **Commuters**: Early warnings for congestion  
- **Authorities**: Resource optimization for traffic flow  
- **City Planners**: Better data for infrastructure planning  

By forecasting traffic accurately, we reduce travel delays, fuel consumption, and environmental impact.

---

## 🔮 Future Scope

- ✅ Integrate real-time data streams (e.g. GPS sensors, live feeds)
- ✅ Use ensemble models like `RandomForest` or `XGBoost`
- ✅ Deploy via REST API for integration with city dashboards
- ✅ Apply spatial analysis using geolocation data
- ✅ Build mobile/web dashboards for visualization

---

## 🛠️ Tech Stack

| Category         | Tools Used             |
|------------------|------------------------|
| **Language**     | Python                 |
| **Data Handling**| Pandas, NumPy          |
| **Modeling**     | Scikit-learn           |
| **Visualization**| Matplotlib             |
| **Time Handling**| datetime, time         |


