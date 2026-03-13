# 🔥 Thermal Predictive Digital Twin

> ML-powered thermal digital twin for industrial equipment. LSTM with attention for multi-step temperature forecasting, real-time anomaly detection, FastAPI REST API, and Grafana dashboard.
>
> [![Python](https://img.shields.io/badge/Python-3.11+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
> [![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white)](https://pytorch.org)
> [![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com)
> [![Grafana](https://img.shields.io/badge/Grafana-F46800?style=for-the-badge&logo=grafana&logoColor=white)](https://grafana.com)
> [![InfluxDB](https://img.shields.io/badge/InfluxDB-22ADF6?style=for-the-badge&logo=influxdb&logoColor=white)](https://influxdata.com)
>
> ---
>
> ## 🧠 ML Architecture
>
> ```
> Sensor Input (6 features, 60 timesteps)
>         │
>         ▼
>    Multi-layer LSTM (3 layers, 128 hidden)
>         │
>         ▼
>    Self-Attention (4 heads)
>         │
>         ▼
>    FC Layers → 12-step Temperature Forecast
>         │
>         ▼
>    Anomaly Score + Time-to-Failure Estimate
> ```
>
> **Features used:** temperature, vibration_rms, current_draw, ambient_temp, load_percent, runtime_hours
>
> **Outputs:**
> - 12-step (1-hour) temperature forecast
> - - Anomaly score (0-1)
>   - - Estimated time-to-failure (hours)
>    
>     - ---
>
> ## 📁 Project Structure
>
> ```
> thermal-predictive-twin/
> ├── twin/
> │   ├── state_engine.py        # Real-time state tracking
> │   ├── physics_model.py       # Physics-based constraints
> │   └── sync_manager.py        # Sensor sync orchestration
> ├── ml/
> │   ├── lstm_predictor.py      # LSTM with attention model
> │   ├── anomaly_detector.py    # Isolation Forest + LSTM combo
> │   └── feature_engineering.py # Rolling stats, lag features
> ├── ingestion/
> │   ├── mqtt_consumer.py       # Real-time MQTT data ingestion
> │   └── data_validator.py      # Schema validation & cleaning
> ├── alerting/
> │   ├── alert_engine.py        # Rule-based + ML alerting
> │   └── slack_notifier.py      # Slack webhook notifications
> ├── api/
> │   └── main.py                # FastAPI REST endpoints
> ├── dashboards/
> │   └── grafana_dashboard.json # Pre-built Grafana dashboard
> ├── notebooks/
> │   ├── 01_eda.ipynb            # Exploratory data analysis
> │   └── 02_model_training.ipynb # Model training & evaluation
> ├── docker-compose.yml
> └── requirements.txt
> ```
>
> ---
>
> ## 🚀 Quick Start
>
> ```bash
> git clone https://github.com/dhanushhhhh01/thermal-predictive-twin.git
> cd thermal-predictive-twin
> cp .env.example .env
> docker-compose up -d
> ```
>
> **API:** `http://localhost:8000/docs`
> **Grafana:** `http://localhost:3000` (admin/admin)
>
> ---
>
> ## 📡 API Endpoints
>
> | Method | Endpoint | Description |
> |--------|----------|-------------|
> | `POST` | `/predict/{device_id}` | Get temperature forecast |
> | `GET` | `/status/{device_id}` | Current twin state |
> | `GET` | `/anomalies` | Recent anomalies |
> | `POST` | `/train` | Retrain model on new data |
>
> ---
>
> ## 📊 Performance
>
> | Metric | Value |
> |--------|-------|
> | MAE (1-step) | ~0.8°C |
> | RMSE (1-step) | ~1.2°C |
> | Anomaly Detection F1 | 0.94 |
> | Inference latency | <50ms |
>
> ---
>
> ## 📬 Author
>
> **Dhanush Ramesh Babu** | [LinkedIn](https://linkedin.com/in/dhanushrameshbabu16) | MSc. Industry 4.0 @ SRH Berlin | 🟢 Open to Werkstudent/Internship
