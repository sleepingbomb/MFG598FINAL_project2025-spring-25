# MFG598FINAL_prroject2025-spring-25 by Prof. BINIL STARLY
I am Anusha Chatterjee. This is my MFG 598 Final Project
# AI-Based Traffic Congestion Prediction & Visualisation

A Jupyter Notebook that **generates realistic traffic data, forecasts congestion with an LSTM/GRU model, finds network-aware optimal routes, and visualises everything in Bokeh**—all in one runnable file.

---

## ✨ Key Features
| Layer | What it does | Tech |
|-------|--------------|------|
| **Synthetic Data** | Manufactures thousands of speed & volume samples with statistical realism | **TimeGAN** |
| **Forecasting** | Predicts next-hour speed/volume | **TensorFlow 2 GRU** (swap in LSTM/Transformer easily) |
| **Routing** | Computes lowest-delay path that adapts to predicted traffic | **NetworkX** |
| **Dashboard** | Interactive time-series & road-graph plots | **Bokeh** |

---

## 🚀 Quick Start

```bash
# 1. Clone
git clone https://github.com/<your-user>/traffic-congestion-ai.git
cd traffic-congestion-ai

# 2. Create environment
python -m venv .venv
source .venv/bin/activate      # Windows: .venv\Scripts\activate

# 3. Install deps
pip install -r requirements.txt

# 4. Launch
jupyter notebook Traffic_Congestion_prediction.ipynb

