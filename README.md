# Disaster Response Coordination Hub

**A real-time wildfire and disaster monitoring platform powered by NASA FIRMS satellite data and interactive maps.**

---

## Overview

This project integrates NASA FIRMS (Fire Information for Resource Management System) data with a FastAPI backend and a Folium/Leaflet-based interactive map frontend. It provides:

* **Fire Detection Visualization**: Interactive map of detected fire locations across India.
* **Fire Statistics Dashboard**: Total fire counts, confidence levels, and brightness averages.
* **REST API**: FastAPI endpoints to fetch fire statistics and render interactive maps.

---

## Files in this Repository

* **`app.py`**: FastAPI backend server

  * Fetches fire data from NASA FIRMS API
  * Computes fire statistics (high/medium/low confidence, brightness)
  * Provides REST API endpoints
* **`index_map.html`**: Example of a generated interactive map with fire markers and statistics overlay.

---

## Features

* Pulls satellite fire data for India (configurable bounding box).
* Classifies fire confidence levels (High/Medium/Low).
* Displays fires as colored circle markers with popups showing location, confidence, brightness, and date.
* Automatically computes statistics and overlays them on the map.
* Provides both JSON stats and HTML map through API endpoints.

---

## API Endpoints

* **`/fires/stats`** → Returns JSON with fire statistics.

  ```json
  {
    "total": 25,
    "high": 10,
    "medium": 9,
    "low": 6,
    "avg_brightness": 315.4,
    "updated": "2025-08-24 14:30:00"
  }
  ```

* **`/fires/map`** → Returns JSON with fire data + rendered interactive HTML map.

---

## Quick Start

1. Clone this repository:

   ```bash
   git clone https://github.com/<your-username>/disaster-response-hub.git
   cd disaster-response-hub
   ```

2. Install dependencies:

   ```bash
   pip install fastapi uvicorn pandas folium
   ```

3. Run the FastAPI app:

   ```bash
   uvicorn app:app --reload --port 5476
   ```

4. Open in browser:

   * Statistics → [http://127.0.0.1:5476/fires/stats](http://127.0.0.1:5476/fires/stats)
   * Map → [http://127.0.0.1:5476/fires/map](http://127.0.0.1:5476/fires/map)

---

## Example Output

* **Interactive Map**: Fire markers with popups.
* **Statistics Panel**: Total fires, confidence breakdown, average brightness, and timestamp.

---

## Configuration

* `MAP_KEY`: NASA FIRMS API Key (required)
* `COUNTRY`: Region of interest
* `DAYS`: Number of past days to fetch fire data
* `SATELLITE`: Satellite source
* Bounding Box

---

## Future Enhancements

* Extend to multiple disaster types (floods, cyclones).
* Add real-time alerts for new fire detections.
* Volunteer and resource coordination features.
* Integration with route planning for disaster response.

---

## Contact

For issues or contributions, please open a GitHub issue or pull request.
