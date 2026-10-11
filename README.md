# Smart Supply Chain & Demand Forecasting Dashboard

An AI-powered smart supply chain & demand forecasting platform that helps logistics and warehouse managers decide **how much to stock, when to re-order, and how to deliver**, by forecasting demand, flagging stockout risks, and suggesting efficient delivery routes.

> B.Tech 3rd Year (Data Science) mini project, team of 4.

---

## Problem Statement

Retail and e-commerce companies lose money in two ways:

- **Overstocking:** unsold goods lock up capital, increase warehouse rent, and may expire.
- **Stockouts:** customers find "Out of Stock" and move to a competitor, costing sales and trust.

Manual estimates based only on last year's sales cannot handle fast-changing demand, seasonal trends, or festival spikes.

## Features

| Module | What it does |
|---|---|
| **AI Demand Forecasting** | Predicts units sold per product for the next 7, 30, or 90 days using past sales, seasonality, and calendar trends |
| **Anomaly & Stockout Alerts** | Warns when an item will run out ("Item X will finish in 5 days, re-order now") and flags abnormal demand spikes or drops |
| **Route Optimization** | Suggests the shortest, lowest-cost delivery route from warehouse to shops |
| **What-If Simulator** | Sliders let a manager test scenarios, e.g. "What if demand rises 30% next week?", and see stock impact instantly |

## Tech Stack

- **ML / Data:** Python, pandas, scikit-learn, LightGBM / XGBoost, Google OR-Tools
- **Backend:** FastAPI, Uvicorn
- **Frontend:** Next.js, React, Recharts, Leaflet
- **Tools:** Git, GitHub

## Project Structure

```
.
├── ml/            # Data cleaning, feature engineering, forecasting, anomaly detection, routing logic
├── backend/       # FastAPI app that serves forecasts, alerts, simulation and routes
├── frontend/      # Next.js dashboard (charts, alerts table, simulator, route map)
├── README.md
└── .gitignore
```

## Datasets

- **Store Item Demand Forecasting Challenge** (Kaggle): 5 years of sales for 50 items across 10 stores. Used to train and test the forecasting model.
- **M5 Forecasting - Accuracy, Walmart** (Kaggle): larger dataset for extended experiments.
- **DataCo Smart Supply Chain** (Kaggle): shipping, delivery status, and late-delivery data for logistics analysis.

Datasets are **not stored in this repository**. Download them from Kaggle and place them in `ml/data/`.

> **Note:** Warehouse stock levels and delivery locations are **simulated**, because no public dataset contains real inventory or route data. Starting stock is set relative to each item's average demand, and routes use a fixed set of coordinates with haversine distances.

## API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| GET | `/forecast?item=&store=&horizon=30` | Forecasted units per day |
| GET | `/alerts` | Items at risk of stockout, with days left and re-order quantity |
| POST | `/simulate` | Applies a demand multiplier and returns shortfall and days to stockout |
| GET | `/route` | Optimized delivery order, distance, and coordinates |

## Getting Started

```bash
# 1. Clone the repository
git clone https://github.com/dakshsharma29455/Supply-Chain-Prediction-Engine-.git
cd Supply-Chain-Prediction-Engine-

# 2. Backend
cd backend
pip install -r requirements.txt
uvicorn main:app --reload

# 3. Frontend (new terminal)
cd frontend
npm install
npm run dev
```

The backend runs at `http://localhost:8000` (API docs at `/docs`) and the frontend at `http://localhost:3000`.

## Team

| Member | Role | Responsibilities |
|---|---|---|
| Member 1 | Data & ML Lead | Data cleaning, time-series features, training forecasting models |
| Member 2 | ML Logic & Optimization | Anomaly detection, route optimization, stockout logic |
| Member 3 | Backend API Lead | FastAPI setup, connecting ML outputs to the API |
| Member 4 | Frontend & Dashboard Lead | Next.js dashboard, charts, maps, simulator UI |

*(Replace "Member 1-4" with real names and GitHub usernames.)*

## Git Workflow

- Never commit directly to `main` once development starts.
- Create your own branch (for example `member1-ml`), commit often, and open a pull request.
- Work inside your own folder to avoid merge conflicts.

## Future Scope

- Real warehouse inventory integration
- Live traffic data for routing
- Multi-warehouse support
- Automatic re-order suggestions with supplier lead times 
