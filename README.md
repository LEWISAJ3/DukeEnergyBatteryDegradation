# Battery Degradation Modeling Using Functional Data Analysis

This project analyzes and predicts lithium-ion battery capacity degradation using Functional Principal Component Analysis (FPCA) and voltage rebound modeling. The goal is to estimate battery health and long-term performance from time-series charge and discharge behavior.

The work was completed in collaboration with East Tennessee State University and Duke Energy (Sept 2024 – May 2025).

---

## Problem

Lithium-ion batteries degrade over time, but degradation is not directly observable during operation. Instead, we observe voltage, current, and temperature time-series during charge/discharge cycles.
This project investigates whether battery health (capacity) can be predicted from those signals using functional data analysis techniques.

---

## Data Sources

Two publicly available datasets are used:

**NASA Battery Dataset**
https://labinfo.ing.he-arc.ch/gitlab/ticc/16TICc19/nasa-battery-dataset/-/tree/master?ref_type=heads

**Random Walk Battery Usage Dataset**
https://catalog.data.gov/dataset/randomized-battery-usage-2-room-temperature-random-walk

Due to size constraints, datasets are not stored in this repository.
After downloading, place the extracted files inside the `data/` directory.

---

## Project Structure

* `PreProcessing/` – Cleaning and preparation of the NASA battery dataset
* `FPCA/` – Functional Principal Component Analysis modeling of capacity degradation
* `VR/` – Voltage Rebound modeling and prediction
* `data/` – Location where downloaded datasets should be placed

Each folder contains a dedicated README with more detailed explanations.

---

## Setup & Running

1. Clone the repository

```
git clone <your repo link>
cd <repo name>
```

2. Install dependencies

```
pip install -r requirements.txt
```

3. Download datasets and place them inside:

```
data/
```

4. Run preprocessing before modeling:

```
python PreProcessing/<scriptname>.py
```

After preprocessing, notebooks in `FPCA/` and `VR/` can be executed.

---

## Results

The models estimate battery discharge capacity using time-series measurements of voltage, current, and temperature.
FPCA captures dominant functional patterns across cycles, while the voltage rebound method uses relaxation behavior after discharge to infer degradation.

---

## Attribution

This repository is a reorganized and documented version of a collaborative graduate data science project.
"# DukeEnergyBatteryDegradation" 
