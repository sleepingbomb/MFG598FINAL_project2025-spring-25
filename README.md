# MFG598FINAL_project2025-spring-25 by Prof. BINIL STARLY
I am Anusha Chatterjee. This is my MFG 598 Final Project
## Youtube Video Link for demonstration
https://youtu.be/mxpIc-zR8Yo?si=wMF7i4yCIgKUk1gJ
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
## 🛠️ Methodology

The project is organised as **four sequential layers**.  
Each layer is isolated in its own helper functions / notebook cells so you can swap parts without breaking the others.

| # | Layer | Goal | Core Functions / Cells |
|---|-------|------|------------------------|
| 1 | **Synthetic Data** | Produce a privacy-safe traffic dataset that mimics real sensors | `create_minimal_real_data`, `train_timegan`, `timegan_generate` |
| 2 | **Pre-process & Forecast** | Clean → window → predict next-hour congestion | `preprocess_traffic_data`, `build_gru_model`, `train_model`, `evaluate_rmse` |
| 3 | **Dynamic Routing** | Turn forecasts into edge costs and find the least-delay path | `build_road_network`, `update_edge_weights`, `nx.shortest_path` |
| 4 | **Interactive Dashboard** | Let users explore forecasts & routes | `plot_time_series`, `plot_network` |

### High-Level Flow

```bash
flowchart TD
    A[Seed Data<br/>(300 days)] --> B[Train TimeGAN<br/>150 epochs]
    B --> C[Synthetic Dataset<br/>(400 days)]
    C --> D[Pre-process<br/>+ Window 24 h]
    D --> E[GRU (64) → Dense(32) → Dense(1)]
    E --> F[Next-Hour Forecast]
    F --> G[Update Edge Weights]
    G --> H[NetworkX<br/>Shortest Path]
    F --> I[Time-Series Plot]
    H --> J[Road-Graph Plot]
    I -->|Bokeh| K[Interactive Dashboard]
    J -->|Bokeh| K

````

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

````
## Sample Results
| Metric                              | Value (demo run) |
| ----------------------------------- | ---------------- |
| TimeGAN reconstruction loss         | 0.018            |
| GRU test-set RMSE (speed)           | **0.040**        |
| Avg. travel-time reduction vs. base | **17 %**         |

## Future Work
- Live data ingestion (loop detectors, CCTV)
- Transformer model for multi-step forecasting
- Bokeh Server + FastAPI deployment
- Dockerfile for push-button edge installation

## References
1. Yoon, J., Jarrett, D., & van der Schaar, M. (2019).
Time-Series Generative Adversarial Networks.
NeurIPS Workshop on Synthetic Data.

2. Cho, K., et al. (2014). Learning Phrase Representations with RNN Encoder-Decoder for Statistical Machine Translation.
EMNLP.

3. Bokeh 2.4.3 – Interactive Visualisation Library.
https://docs.bokeh.org/

4. NetworkX 3.3 – Complex-Network Analysis in Python.
https://networkx.org/

## License
This project is licensed under the MIT License—free for personal and commercial use.
Please ⭐ the repo if you find it helpful!


