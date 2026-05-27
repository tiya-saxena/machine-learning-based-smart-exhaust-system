# 🚗💨 Intelligent Exhaust System — ML-Based Vehicular Pollution Control

> A Machine Learning powered IoT system for real-time vehicular exhaust monitoring, pollution classification, and adaptive carbon capture — designed for urban air quality improvement.

---

## 📌 Overview

Rising vehicular emissions are a critical public health issue in Indian cities. According to the **Centre for Science and Environment (CSE)**, vehicles contribute **50–53% of Delhi's local PM₂.₅ pollution**. Existing solutions like catalytic converters and diesel particulate filters (DPFs) are passive — they cannot adapt to real-time exhaust conditions.

This project proposes a **smart, non-intrusive exhaust attachment** that:
- Continuously monitors exhaust gases using sensors
- Classifies pollution levels using a **Decision Tree ML model**
- Triggers adaptive **filtration and carbon capture** mechanisms in real time

> ⚠️ This is a **conceptual/research prototype**. The framework has been validated through design-level analysis and simulation. Physical prototype testing is planned for future work.

---

## 🧠 Key Features

| Feature | Description |
|---|---|
| 🔴 Real-Time Monitoring | Continuously reads CO, CO₂, NOx, PM₂.₅, smoke density & temperature |
| 🤖 ML Classification | Decision Tree model categorizes emissions as **Low / Medium / High** |
| 🌿 Adaptive Control | Filtration and carbon capture intensity adjusts automatically |
| 🔧 Non-Intrusive Design | Fits on existing exhaust outlet — no engine or ECU modification required |
| 📡 IoT Integration | Arduino / ESP32 / Raspberry Pi compatible microcontroller unit |
| 💰 Cost-Effective | Low-power, scalable for different vehicle types |

---

## 🏗️ System Architecture

```
Exhaust Outlet
     │
     ▼
┌──────────────────────┐
│   Sensor Array       │  ← CO, CO₂, NOx, PM₂.₅, Smoke, Temperature
└──────────┬───────────┘
           │ Electrical Signals
           ▼
┌──────────────────────┐
│  Microcontroller     │  ← Arduino / ESP32 / Raspberry Pi
│  (Data Acquisition)  │
└──────────┬───────────┘
           │ Pre-processed Data
           ▼
┌──────────────────────┐
│  ML Model            │  ← Decision Tree Classifier
│  (Pollution Level    │     Low | Medium | High
│   Classification)    │
└──────────┬───────────┘
           │ Control Signal
           ▼
┌──────────────────────┐
│  Filtration &        │  ← Particulate Filter + Carbon Capture Unit
│  Carbon Capture      │     Adaptive intensity based on pollution class
└──────────────────────┘
```

---

## ⚙️ Hardware Components

- **Gas Sensors** — CO, CO₂, NOx detection (e.g., MQ series)
- **PM Sensor** — Particulate Matter (PM₂.₅) measurement
- **Temperature Sensor** — Exhaust heat monitoring
- **Microcontroller** — Arduino Uno / ESP32 / Raspberry Pi
- **Filtration Module** — Particulate exhaust filter
- **Carbon Capture Unit** — Adaptive carbon-based pollutant absorption

---

## 🤖 Machine Learning Model

| Parameter | Details |
|---|---|
| Algorithm | Decision Tree Classifier |
| Input Features | CO concentration, CO₂ level, NOx, smoke density, temperature |
| Output Classes | `Low`, `Medium`, `High` pollution |
| Why Decision Tree? | Low computational cost, interpretable rules, real-time embedded deployment |
| Platforms Supported | Arduino, ESP32, Raspberry Pi |

### Preprocessing Pipeline

1. **Noise Filtering** — Remove sensor signal noise
2. **Outlier Removal** — Handle sensor drift and anomalies
3. **Normalization** — Scale features for consistent model input
4. **Feature Selection** — CO, CO₂, NOx, smoke density, temperature

### Control Logic

```
IF pollution == LOW:
    → Normal exhaust mode

IF pollution == MEDIUM:
    → Activate exhaust filters
    → Set carbon capture to MODERATE intensity

IF pollution == HIGH:
    → Fully activate filters
    → Set carbon capture to HIGH intensity
    → Regulate exhaust flow
```

---

## 📊 Pollution Context

- Vehicles account for **20–30% of ambient PM₂.₅** in Indian urban areas
- India had ~**295 million registered vehicles** by 2019 (6× increase since 2000)
- PM₂.₅ particles (≤2.5 µm diameter) penetrate lungs and bloodstream, causing respiratory and cardiovascular diseases
- Delhi's transport sector contributes ~**30% of greenhouse gases** in the city alone

---

## 🚀 Getting Started

### Prerequisites

```bash
# For Python-based ML simulation
pip install scikit-learn pandas numpy matplotlib

# For Arduino/ESP32 firmware
# Install Arduino IDE: https://www.arduino.cc/en/software
# Required Libraries: ArduinoJson, DHT sensor library, MQ sensor library
```

### Repository Structure

```
intelligent-exhaust-system/
│
├── ml_model/
│   ├── dataset/              # Training data (sensor readings + labels)
│   ├── train_model.py        # Decision Tree training script
│   ├── evaluate_model.py     # Model evaluation and metrics
│   └── model.pkl             # Saved trained model
│
├── firmware/
│   ├── sensor_read.ino       # Arduino sensor data acquisition
│   ├── ml_inference.ino      # On-device ML inference
│   └── control_logic.ino     # Filter & carbon capture actuation
│
├── simulation/
│   └── exhaust_sim.py        # Software simulation of the system
│
├── docs/
│   └── system_design.pdf     # Full research paper
│
└── README.md
```

### Run the ML Simulation

```bash
git clone https://github.com/<your-username>/intelligent-exhaust-system.git
cd intelligent-exhaust-system/ml_model

python train_model.py       # Train the Decision Tree model
python evaluate_model.py    # Evaluate accuracy and classification report
```

---

## 📈 Results & Findings

- The system design demonstrates **non-intrusive installation** with zero impact on engine performance or ECU
- ML-based classification effectively handles **Low / Medium / High** emission states in simulated scenarios
- Post-exhaust filtration and carbon capture module strengthens existing emission control technologies
- Framework is **scalable** across different vehicle types and adaptable for smart city integrations

---

## ⚠️ Limitations

- Sensor accuracy may degrade over time; **regular calibration is required**
- ML model performance depends on **training data quality and diversity**
- Environmental factors (temperature, humidity) can impact sensor reliability
- Physical prototype **not yet implemented** — results are design/simulation based

---

## 🔮 Future Scope

- [ ] Physical prototype development and lab testing
- [ ] Integration with **smart city IoT platforms**
- [ ] OBD-II vehicle data integration for richer feature inputs
- [ ] Deep learning models (LSTM) for time-series pollution forecasting
- [ ] Cloud dashboard for fleet-level emission analytics
- [ ] Policy-level data reporting to pollution control boards

---

## 🔩 Hardware Prototype & 3D Model

### 🖨️ 3D Model Design

> CAD/3D model of the exhaust attachment unit showing the sensor housing, filtration chamber, and carbon capture module.

| View | Preview |
|---|---|
| Front View | ![3D Model Front](docs/images/3d_model_front.png) |
| Side View | ![3D Model Side](docs/images/3d_model_side.png) |
| Exploded View | ![3D Model Exploded](docs/images/3d_model_exploded.png) |

---

### 🛠️ Hardware Prototype

> Physical assembly of the smart exhaust unit with sensor array and microcontroller mounted on the exhaust outlet.

| Component | Image |
|---|---|
| Full Assembly | ![Prototype Full](docs/images/prototype_full.jpg) |
| Sensor Array | ![Sensor Array](docs/images/sensor_array.jpg) |
| Microcontroller Unit | ![MCU Setup](docs/images/mcu_setup.jpg) |
| Filtration Module | ![Filtration Module](docs/images/filtration_module.jpg) |

---


> *"If this system is implemented even in a small number of vehicles, it will enhance air quality and promote sustainability in the environment."*
