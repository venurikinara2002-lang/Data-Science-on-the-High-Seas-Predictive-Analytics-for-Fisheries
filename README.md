# OceanGuard Optimizer: Data Science on the High Seas

![Boat Dashboard](boat_dashboard.png)

## 📌 Project Introduction & Industry Context

Offshore fisheries represent a vital sector in the maritime economy, yet they face massive operational risks and high capital costs. For offshore fishing voyages in developing countries like **Sri Lanka**, fuel expenses, vessel maintenance, and crew sizing represent significant financial risks, while changing weather conditions present constant safety hazards. 

This project addresses these **real-world maritime challenges** using a **real-world dataset**—containing **20,000+ Sri Lankan offshore fishing trip records**. By leveraging historical logs of vessel characteristics, weather metrics, and catch yields, **OceanGuard Optimizer** predicts the operational costs of upcoming trips and advises crew members on their financial break-even targets and departure safety.

---

## 📁 Repository Overview & Deliverables

This repository contains the source code for the Streamlit decision support system, the machine learning models (Random Forest, CatBoost, and XGBoost), and supporting documentation.

### 🔗 Quick Links to Project Assets:
* 📄 **[Full Project Report (PDF)](Full%20project%20report.pdf)**: Comprehensive analysis of models, feature extraction, and validation results.
* 📄 **[Individual Contribution Report (PDF)](Individual%20contribution%20report.pdf)**: Report detailing specific design, modeling, and analytics contributions.
* 📊 **[Presentation Slides (PDF)](slides.pdf)**: Pitch deck detailing models, metrics, and application workflow.
* 🎥 **[Video Demonstration (MP4)](fisheries%20video%20demonstration.mp4)**: Walkthrough of the OceanGuard Optimizer web dashboard.

---

## 💡 Business & Industry Impact: Why It Matters

### 1. Pre-Trip Financial Certainty
Fishing trips require massive upfront investments in fuel, ice, food, and bait. If a voyage yields a low catch, the crew can run a loss. By predicting operational costs beforehand (based on engine HP, trip duration, distance, and crew size), **OceanGuard Optimizer** eliminates financial uncertainty.

### 2. Profit Break-Even Target Setting
The app converts predicted trip costs into a concrete catch target:
* *“To cover your estimated cost of LKR 125,000, you must catch a minimum of 147 kg of mixed species.”*
This gives the captain a clear, data-backed operational goal for the voyage.

### 3. Sea Safety & Voyage Risk Mitigation
Rough seas endanger both crew lives and vessel assets. The live weather checking system uses real-time wave height (m) and wind speed (kph) forecasts to categorize departures:
* 🟢 **Calm**: Safe to depart.
* 🟡 **Moderate**: Proceed with caution.
* 🔴 **Rough**: Departure not recommended.

### 4. Crew and Vessel Specification Tuning
By visualizing the correlation between crew size and total operational cost, fleet owners can optimize crew scheduling to maximize net returns.

---

## 🚀 Key Features

* **Predictive Cost Model**: 
  Powered by a **Random Forest Regressor** (and optimized with **CatBoost/XGBoost** during training) that estimates voyage costs based on vessel and duration specifications.
* **Streamlit Maritime Dashboard**:
  Features a theme styled in deep maritime navy, presenting fleet operations, safety metrics, and financial tools in a clean sidebar configuration.
* **Live Weather safety tester**:
  Calculates sea conditions (Calm/Moderate/Rough) dynamically based on wind speed and wave height.
* **Break-Even Catch Calculator**:
  Dynamically computes required mixed-species weights (Yellowfin Tuna, Skipjack, Marlin) to cover predicted trip expenses at current market rates.
* **Fleet Risk Analytics**:
  Generates historical visualizations, crew sizing cost distributions, and species weight distributions using Matplotlib and Seaborn.

---

## 🛠️ Tech Stack & Architecture

* **Framework**: Streamlit (Python)
* **Libraries**: NumPy, Pandas, Scikit-Learn, Matplotlib, Seaborn
* **Model**: RandomForestRegressor

---

## 🔧 Installation & Setup

### Prerequisites
* **Python** 3.10 or higher
* **pip** (Python package installer)

### Quick Start

#### 1. Setup Environment & Dependencies
Navigate to the directory, create a virtual environment, and install dependencies:
```bash
python -m venv venv
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate

pip install -r requirements.txt
```

#### 2. Run the Streamlit Application
Start the Streamlit dashboard server:
```bash
streamlit run app.py
```
The application will open automatically in your browser at `http://localhost:8501`.
