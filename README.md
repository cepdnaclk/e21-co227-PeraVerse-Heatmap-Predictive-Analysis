---
layout: home
permalink: index.html

# Please update this with your repository name and title
repository-name: e21-co227-PeraVerse-Heatmap-Predictive-Analysis
title: Heatmap Predictive Analytics for Exhibition Spaces
---

# PeraVerse Heatmap Predictive Analysis (Team-07)

---

## Team
- E/21/339, Rukshan A.D., [e21339@eng.pdn.ac.lk](mailto:e21339@eng.pdn.ac.lk)
- E/21/254, Manilgama N.C., [e21254@eng.pdn.ac.lk](mailto:e21254@eng.pdn.ac.lk)
- E/21/292, Perera K.A.P.M., [e21292@eng.pdn.ac.lk](mailto:e21292@eng.pdn.ac.lk)
- E/21/200, Jayasuriya A.R.M., [e21200@eng.pdn.ac.lk](mailto:e21200@eng.pdn.ac.lk)

## Supervisors
- Ms. Yasodha Vimukthi, [yasodhav@eng.pdn.ac.lk](mailto:yasodhav@eng.pdn.ac.lk)

## Table of Contents
1. [Introduction](#introduction)
2. [Solution & Impact](#solution--impact)
3. [Features & Architecture](#features--architecture)
4. [How to Run](#how-to-run)
5. [Deployment](#deployment)
6. [Links](#links)

---

## Introduction

Large events struggle with congestion, unpredictable visitor flows, and limited visibility into live occupancy. Our system ingests historical building data, predicts crowd levels for the next 15 minutes, and overlays the results on an interactive campus heatmap—empowering organisers to react before bottlenecks form.


## Solution & Impact

The Heatmap Predictive Analytics solution delivers:

- Real-time building snapshots fed by a synthetic data generator or live database
- Short-term forecasts via EMA, exposing predicted counts and confidence metadata
- Interactive heatmap with building drill-down, historical charts, and alert widgets
- Database-backed persistence and REST APIs for integrations
- Extensible architecture ready for additional analytics or notification channels

**Impact**

- Improves visitor experience by avoiding overcrowding
- Supports proactive staffing and facility allocation
- Reduces safety risks through early warnings
- Provides a reusable template for smart-campus crowd analytics


## Features & Architecture

### Key Features
- **Predictive analytics**: EMA-based forecasting (`utils/emaPrediction.js`)
- **Synthetic data generation**: Realistic occupancy traces for testing (`utils/dataGenerator.js`)
- **REST API**: `/heatmap/map-data`, `/heatmap/building/:id/history`, `/reports/*`
- **Heatmap UI**: SVG-based campus map with live colour coding and detail popovers
- **Historical & aggregate charts**: Building-specific timelines and global statistics
- **Report downloads**: CSV/PDF export endpoints (frontend button included)
- **Configurable backend**: .env-driven ports and Supabase/PostgreSQL credentials

### Architecture Overview
- **Frontend**: React + TypeScript + Vite (`src/pages/Heatmap/*`)
- **Backend**: Express.js + Node.js (`backend/heatmap/backend/exhibition-map-backend`)
- **Database**: PostgreSQL (Supabase) with `buildings`, `current_status`, `building_history` tables
- **Prediction**: EMA smoothing with configurable alpha & horizon (default 15 minutes)
- **Deployment**: Node.js server for backend, static build for frontend

## How to Run

### 1. Clone Repository
```bash
git clone https://github.com/cepdnaclk/e21-co227-PeraVerse-Heatmap-Predictive-Analysis.git
cd e21-co227-PeraVerse-Heatmap-Predictive-Analysis
```

### 2. Install Dependencies

**Backend**
```bash
cd backend/heatmap/backend/exhibition-map-backend
npm install
```

**Frontend** (from project root)
```bash
npm install
```

### 3. Environment Variables

Create/update `backend/heatmap/backend/exhibition-map-backend/.env`:

```env
DATABASE_HOST=localhost
DATABASE_PORT=5432
DATABASE_NAME=heatmap_db
DATABASE_USER=postgres
DATABASE_PASSWORD=your_password
PORT=3897
```

Frontend `.env` (project root):

```env
VITE_HEATMAP_API_URL=http://localhost:3897
VITE_DEV_PORT=5173
```

### 4. Database Setup

- Run SQL scripts in `backend/heatmap/database/` (`heatmapdb.sql`, `add_history_table.sql`)
- Optional helper: `node create_history_table.js`

### 5. Start Services

**Option 1: Run Everything Together**
```bash
npm run start:all
```

**Option 2: Run Separately**

**Backend**
```bash
cd backend/heatmap/backend/exhibition-map-backend
npm run dev
# or npm start
```

**Frontend**
```bash
npm run dev
# Vite dev server, default http://localhost:5173
```

Navigate to `http://localhost:5173/heatmap` to access the dashboard.

## Deployment

The system can be deployed using:

- **Frontend:** Static build deployed on Vercel/Netlify for fast content delivery
- **Backend:** Node.js server deployed on cloud platforms (AWS/Azure/Heroku)
- **Database:** PostgreSQL (Supabase) or managed PostgreSQL instance
- **Environment:** Production builds with optimized Vite bundling and Express server

## Links

- [Project Repository](https://github.com/cepdnaclk/e21-co227-PeraVerse-Heatmap-Predictive-Analysis)
- [Project Page](https://cepdnaclk.github.io/e21-co227-PeraVerse-Heatmap-Predictive-Analysis/)
- [Department of Computer Engineering](http://www.ce.pdn.ac.lk/)
- [University of Peradeniya](https://eng.pdn.ac.lk/)


### Tags
`Node.js`, `Express.js`, `React`, `TypeScript`, `Vite`, `EMA Algorithm`, `Real-time Analytics`, `Heatmap Visualization`, `Predictive Analysis`, `PostgreSQL`, `Supabase`, `Crowd Management`, `75Exhibition`


[//]: # (Please refer this to learn more about Markdown syntax)
[//]: # (https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
