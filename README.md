🌲 Maple Sap Flow Prediction

Satellite-powered maple tapping prediction app built at BramHacks 2025

🏆 Winner — “Smart Cookie” Award ($400)

---------------------------------------------------------------------------------------------------------------------------------------------------------------------

📌 Project Overview

  Maple syrup yield depends heavily on choosing the right tapping window, which is driven by temperature cycles, soil moisture, and pressure changes. Producers often rely on guesswork or outdated regional forecasts.
This project uses satellite data, environmental processing scripts, and a Python API to determine when sap flow is most likely to begin — helping farmers prepare and maximize yield.
The frontend (inside myMapleSite/) visualizes predictions and allows users to select regions across Ontario.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------

🚀 Features

 - Land Surface Temperature (LST) analysis
 - Soil Moisture extraction & normalization
 - Atmospheric Pressure Trend processing
 - Seasonal Planning Alerts for producers
 - Interactive map viewer (Ontario SMAP tile viewer)
 - REST API for tapping-window predictions
 - Support for regions beyond Brampton (recent bug fix)
 - Repository Structure
   
---------------------------------------------------------------------------------------------------------------------------------------------------------------------

    Maple-Sap-Flow-Prediction/
    │
    ├── myMapleSite/                 # Frontend UI (HTML/CSS/JS)
    │     ├── index.html
    │     ├── styles.css
    │     ├── app.js
    │     └── assets/
    │
    ├── api.py                       # Main FastAPI backend
    ├── PressureData.py              # Pressure extraction & preprocessing
    ├── SoilMoistureData.py          # Soil moisture data pipeline
    ├── SeasonalPlanningAlerts.py    # Alert logic for tapping readiness
    ├── lst_data.py                  # Land Surface Temperature handler
    ├── utils.py                     # Shared helpers
    │
    ├── smap_ontario.html            # Standalone SMAP map visualization
    ├── requirements.txt             # Python dependencies
    └── README.md

---------------------------------------------------------------------------------------------------------------------------------------------------------------------

🧠 How It Works

1. Data Collection & Processing (Python scripts)

Each environmental factor is handled by a dedicated module:

    File Purpose

    PressureData.py:	Fetches & predicts the Pressure data for a given region and range of time returing a normalized range from 0-1 depending on how good the pressure is for optimal tapping

    SoilMoistureData.py:	Fetches & predicts the SMAP data for a given region and range of time returing a normalized range from 0-1 depending on how good the pressure is for optimal tapping

    lst_data.py:	Fetches & predicts the Land Surface Temp data for a given region and range of time returing a normalized range from 0-1 depending on how good the pressure is for optimal tapping

    SeasonalPlanningAlerts.py:	Handles sending a text message

These scripts are imported inside api.py.

2. API Inference Layer (api.py)

The backend accepts a location, runs the prediction models to get the data for the location, and returns the Recommended tapping window and optimal tapping date

3. Frontend (myMapleSite/)

The UI provides:

Location selection

SMS selection

Prediction results

Clean, minimalistic screens built with HTML/CSS/JS

---------------------------------------------------------------------------------------------------------------------------------------------------------------------

🏁 Getting Started

1️⃣ Clone the repo

    git clone https://github.com/Parth-Joshi0/Maple-Sap-Flow-Prediction.git

    cd Maple-Sap-Flow-Prediction

2️⃣ Install dependencies

    pip install -r requirements.txt

3️⃣ Run the backend

    uvicorn api.py:app --reload 

Server runs on http://localhost:8000/ (or http://127.0.0.1:8000/ depending on your FastAPI setup).

4️⃣ Launch frontend

    run http://localhost:8000/

Sample JSON:

    post /freeze-thaw
    {
      "location": "Brampton, ON",
    }

    output
    {
        "start_date_freeze_thaw": '2026-03-04',
        "pick_date": '2026-03-07',
        "end_date_freeze_thaw": '2026-04-03',
        "lat": 43.685832,
        "lon": -79.7599366
    }

---------------------------------------------------------------------------------------------------------------------------------------------------------------------

👤 Author

- Parth Joshi
- Amal Chaylil SreeKumar
- Rajveer
- Osajile
- Saurodeep Majumdar
- Aksha
