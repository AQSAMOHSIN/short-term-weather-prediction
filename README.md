# 🌦️ Short-Term Weather Prediction Using Deep Learning

![Python](https://img.shields.io/badge/Python-3.10+-blue)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange)
![Keras](https://img.shields.io/badge/Keras-RNN-green)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow)

A deep-learning approach to short-term temperature forecasting using **LSTM** and **GRU** recurrent neural networks.  
Developed as part of the *Practical Deep Learning for Climate Data* course (July 2025).

📄 Full technical report → [report/AQSA_PDCL_FINAL_REPORT.pdf](./AQSA_PDCL_FINAL_REPORT.pdf)

---

## 📁 Project Structure

```
short-term-weather-prediction/
├── notebooks/
│   └── AQSA_PDCL_FINAL_CODE.ipynb        # Main notebook (training + evaluation)
├── report/
│   └── AQSA_PDCL_FINAL_REPORT.pdf        # Final report
├── data/                                 # Dataset folder (optional; auto-downloaded)
├── models/                               # Saved models (.h5 if exported)
├── .gitignore
└── README.md
```

---

## 📊 Overview

Accurate weather forecasting is essential in agriculture, energy, and disaster management.  
Traditional numerical models are computationally intensive, so this project explores **deep learning alternatives** using time-series modeling.

### 🎯 Objective
Predict the **next day’s minimum temperature** based on the previous 7 days.

### 🧠 Models
| Model | Description |
|-------|--------------|
| **LSTM** | Long Short-Term Memory — retains long-term dependencies |
| **GRU** | Gated Recurrent Unit — efficient and faster than LSTM |
| **Persistence** | Baseline — tomorrow’s temp = today’s temp |
| **Climatology** | Baseline — average temperature for the same day of the year |

---

## 🧩 Dataset

**Source:** [Daily Minimum Temperatures – Melbourne 1981–1990](https://raw.githubusercontent.com/jbrownlee/Datasets/master/daily-min-temperatures.csv)  

- **Feature:** Daily minimum temperature (°C)  
- **Window:** 7-day input → 1-day forecast  
- **Split:** 80% train / 20% test  
- **Normalization:** Min–Max scaling  

---

## ⚙️ Environment Setup

1️⃣ **Clone the repository**
```bash
git clone https://github.com/<your-username>/short-term-weather-prediction.git
cd short-term-weather-prediction
```

2️⃣ **Create and activate a virtual environment**
```bash
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
```

3️⃣ **Install dependencies**
```bash
pip install tensorflow numpy pandas matplotlib scikit-learn
```

---

## ▶️ Running the Notebook

Run locally or open directly in **Google Colab**:
```
notebooks/AQSA_PDCL_FINAL_CODE.ipynb
```

⚠️ **Note:** You can simply run the notebook in **Google Colab** — pretrained models can be saved in the `models/` folder for reuse.  
Make sure to **import and load the correct `.h5` file** before evaluation.

---

## 📈 Results

| Model | MAE | RMSE |
|-------|------|------|
| **GRU** | **1.7849** | **2.2634** |
| **LSTM** | 1.8491 | 2.3343 |
| **Persistence** | 1.9551 | 2.4826 |
| **Climatology** | 2.1107 | 2.7046 |

### 🔍 Key Insights
- **GRU** achieved the best performance, slightly outperforming LSTM.  
- Both deep-learning models significantly outperformed the baselines.  
- **Overly complex mixed augmentation showed lower performance** because the number of epochs was not increased. Since data size grows with such augmentation, **more epochs would be needed for full convergence**.  
- Persistence and climatology are useful baselines but cannot adapt to short-term variations.

---

## 🧠 Loading Pretrained Models

If you saved trained models as `.h5` files, load them easily:

```python
from tensorflow.keras.models import load_model

# Load pretrained GRU model
model = load_model("models/gru_model.h5")

# Predict next day's temperature
y_pred = model.predict(X_test)
```

---

## 🧮 Visualizations

The notebook includes:
- Training vs Validation Loss curves  
- Predicted vs Actual Temperature comparison  
- Seasonal trend visualization  

All plots are automatically saved in the `report/` folder.

---

## 💡 Future Work

- Add multivariate features (humidity, wind speed, rainfall)  
- Extend prediction horizon (multi-day forecasting)  
- Experiment with **Transformer** or **Temporal Convolutional Networks (TCNs)**  
- Deploy as a simple web app using Streamlit or Flask  

---

## 🪪 License

This project is released under the **MIT License**.  
Dataset credit: *Jason Brownlee – Daily Min Temperature Dataset* ([source](https://raw.githubusercontent.com/jbrownlee/Datasets/master/daily-min-temperatures.csv))

---

## 🙌 Acknowledgments

- **TensorFlow / Keras** for model building  
- **Scikit-learn** for preprocessing and metrics  
- **Brownlee Datasets** for open data access  

---

## 📖 Citation

*Short-Term Weather Prediction Using Deep Learning*  
Course: *Practical Deep Learning for Climate Data*  
Author: *Aqsa Mohsin* – July 2025

---

⭐ **If you find this project useful, please star the repo and share it!**
