# Disaster Response Coordination Hub

![Python](https://img.shields.io/badge/Python-3.9%2B-blue.svg)
![FastAPI](https://img.shields.io/badge/FastAPI-0.100%2B-green.svg)
![Folium](https://img.shields.io/badge/Folium-0.15%2B-lightgrey.svg)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)

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
* **`requirements.txt`**: Python dependencies to run the project.

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

2. Create and activate a virtual environment (optional but recommended):

   ```bash
   python -m venv venv
   source venv/bin/activate   # Linux / macOS
   venv\Scripts\activate      # Windows
   ```

3. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Run the FastAPI app:

   ```bash
   PORT=5000 uvicorn app:app --host 0.0.0.0 --port $PORT
   ```

5. Open in browser:

   * Statistics → [http://127.0.0.1:5000/fires/stats](http://127.0.0.1:5000/fires/stats)
   * Map → [http://127.0.0.1:5000/fires/map](http://127.0.0.1:5000/fires/map)

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

---

## Future Enhancements

* Extend to multiple disaster types (floods, cyclones).
* Add real-time alerts for new fire detections.
* Volunteer and resource coordination features.
* Integration with route planning for disaster response.

---

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

---

## Contact

For issues or contributions, please open a GitHub issue or pull request.
