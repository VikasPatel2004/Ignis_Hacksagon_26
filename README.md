# Ignis
### *Next-Gen Forest Fire Detection & Real-Time Monitoring System*

---

## 📖 Introduction
Forest fires represent one of the most significant environmental threats of the 21st century, causing irreversible ecological damage, economic loss, and threatening human lives. Traditional detection methods often rely on manual observation or satellite data that suffers from latency and low resolution in critical early moments.

**Ignis is a dual-backend, high-performance monitoring ecosystem designed to bridge this gap. By utilizing state-of-the-art **YOLOv8 Computer Vision**, the system identifies smoke and fire patterns in real-time from drone or static camera feeds. Integrated with a live GIS dashboard, it provides decision-makers with immediate, actionable intelligence—transforming raw video data into life-saving alerts and strategic analytics.

---

## 🚀 Key Features

### 🤖 **Real-Time AI Detection**
- **YOLOv8 Vision**: High-accuracy detection of fire and smoke clusters.
- **Double Filtering**: Integrated HSV saturation and area-ratio filters to eliminate false positives from reflections or sunlight.
- **Temporal Validation**: Sequential frame confirmation ensures alerts are only triggered for sustained, real fire events.

### 🚁 **Drone Telemetry & Live HUD**
- **Dynamic Simulation**: Simulated drone flight paths with real-time GPS coordinate reporting.
- **Live Stream HUD**: Low-latency video streaming (Flask-based) with detection overlays directly on the dashboard.

### 📊 **Intelligent Analytics Hub**
- **FIRM Data Integration**: Visualization of global satellite-detected hotspots alongside local AI detections.
- **Historical Trends**: Interactive charts (Chart.js) showing detection frequency and intensity over time.
- **System Health**: Automated logs and status monitoring for all distributed services.

### 🗺️ **GIS Integration**
- **Live Leaflet Map**: Interactive geospatial visualization of every detection event.
- **Marker Clustering**: Efficiently manages thousands of satellite data points for a clean UI experience.

---

## 🛠️ Technology Stack

| Layer | Technologies |
| :--- | :--- |
| **Frontend** | React 18, Vite, Tailwind CSS 4.0, Leaflet, Chart.js |
| **Backend (Dashboard)** | Node.js, Express.js, CSV-Parser |
| **Backend (AI Worker)** | Python 3.x, Flask, YOLOv8, OpenCV, PyTorch |
| **Deployment** | Render (Live Hosting), Local Hosting Support |

---

## 📥 Access & Setup Guide

To access the project, you need to set up two main components: the **AI Worker (Python)** and the **Dashboard (React/Node)**.

### 1. Prerequisites
- **Node.js**: v18.x or higher
- **Python**: v3.9+ (with `pip`)
- **Git** (optional, for cloning)

### 2. Setup the Dashboard (Frontend)
```bash
# Navigate to the Frontend directory
cd Frontend

# Install dependencies
npm install

# Start the Express API server (Port 3000)
npm run server

# In a new terminal, start the React Dev server (Port 5173)
npm run dev
```

### 3. Setup the AI Worker (Backend)
```bash
# From the root directory, create a virtual environment
python -m venv venv
source venv/Scripts/activate  # Windows: .\venv\Scripts\activate

# Install requirements
pip install -r requirements.txt

# Run the detection service (Port 5000 & 10000)
python src/drone_stream.py
```

### 4. Direct Links
- **User Dashboard**: `http://localhost:5173`
- **Data API**: `http://localhost:3000`
- **AI Live Stream**: `http://localhost:5000/video`

---

## 🏗️ System Architecture
The system operates on a **Dual-Backend Architecture**:

1.  **AI Edge Worker**: A Python service that processes video streams, runs YOLO inference, and hosts a `/video` stream for the dashboard. When fire is confirmed, it POSTS the GPS data to the Dashboard API.
2.  **Central Dashboard Service**: A Node.js server that stores local detection history (`fire_log.txt`), serves global FIRMS satellite data, and provides the React frontend with a unified state.

---

## 📝 License
Distributed under the MIT License. See `LICENSE` for more information.

---
**Developed for the Hackathon - Engineering a Safer Future.**
