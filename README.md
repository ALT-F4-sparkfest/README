# BUSINA

**Smarter commutes, better journeys.**

*Developed for SparkFest 2026.*

---

## Team ALT F4

| Name | Role |
|---|---|
| Christopher James A. Cresencio | AI & Data |
| Joaqui Rainiel A. Jerez | Backend |
| Jhon Rey D. Oquendo | Frontend |
| Red Colby S. Dumdum | Hardware |

---

## Project Brief

Roughly eight million Filipinos ride jeepneys daily with no way to know when one is arriving, and waits routinely stretch two to four hours. The 2017 Public Utility Vehicle Modernization Program forced independent drivers into cooperatives but gave those cooperatives no digital tools: no GPS, no ridership data, no operational visibility.

Busina closes that gap with a real-time fleet intelligence system: GPS-based vehicle tracking, live ETA prediction, and role-specific dashboards for commuters, cooperative dispatchers, and LGU planners. The current build is a fully working software MVP running on a realistic simulated fleet modeled on real Metro Manila jeepney routes, with live ETA prediction, bunching detection, and an AI insights dashboard. Physical GPS hardware is scoped for Phase 2.

---

## Key Features

- **Live Fleet Map** — real-time vehicle positions across all active routes on an interactive Google Map.
- **Commuter ETA Lookup** — select a stop and see live arrival estimates for every approaching jeepney.
- **Bunching Detection** — automatically flags jeepneys clustering on the same route and alerts dispatchers to correct spacing.
- **AI Insights Dashboard** — travel-time-by-hour charts, demand hotspot maps, and fleet performance KPIs generated from GPS data.

---

## Live Demo

**[https://busina.vercel.app/](https://busina.vercel.app/)**

No login required — the dashboard is open on load.

> **Note:** The backend is hosted on Render's free tier, which spins down after 15 minutes of inactivity. If you're the first person to open the site in a while, the map or ETAs may look empty at first — wait 1–2 minutes for the backend to wake up, then refresh.

---

## Google Technologies Used

- **Google Maps JavaScript API** — powers the live fleet map, vehicle markers, and route rendering on the frontend.
- **Firebase** — used during early backend development for real-time data sync; migrated to Supabase (PostgreSQL) later in the hackathon after hitting Firebase's free-tier limits.

---

## Tech Stack

**Frontend**

| Category | Technology |
|---|---|
| Framework | React.js |
| Build Tool | Vite |
| Maps | Google Maps JavaScript API |
| Charts | Recharts |
| Icons | Lucide React |
| Real-Time Communication | Socket.IO Client |
| API Communication | Fetch API |
| Styling | CSS3 (custom responsive design) |
| Hosting | Vercel |

**Backend**

| Category | Technology |
|---|---|
| Framework | Node.js + Express |
| Database | Supabase (PostgreSQL) |
| MQTT Broker | HiveMQ Cloud |
| Hosting | Render |

**AI & Data**

| Category | Technology |
|---|---|
| Language | Python (pandas, numpy) |
| Simulation | Custom GPS trace generator (5 routes, 10 vehicles) |
| Algorithms | Traffic-aware ETA heuristic, proximity-based bunching detection |
| Output | Aggregated analytics feeding the dashboard (travel time, demand hotspots, fleet KPIs) |

---

## Repository Structure

This submission is split across focused repositories under the organization:

| Repository | Contents |
|---|---|
| [README](https://github.com/ALT-F4-sparkfest/README) | This repository — project overview and submission entry point |
| [Simulated-GPS-Dataset](https://github.com/ALT-F4-sparkfest/Simulated-GPS-Dataset) | AI & Data: simulated GPS generator, ETA heuristic, bunching detection, AI insights pipeline |
| [Backend-MQTT-and-Firebase](https://github.com/ALT-F4-sparkfest/Backend-MQTT-and-Firebase) | Backend: Express API, MQTT ingestion, ETA/geofence logic, database layer |
| [Busina-Full-Stack](https://github.com/ALT-F4-sparkfest/Busina-Full-Stack) | Frontend: React dashboard (commuter view, cooperative dashboard, AI insights) |

Hardware (ESP32 + GPS firmware) is scoped for Phase 2 and is not yet part of this submission; the current MVP runs entirely on simulated GPS data modeled on real Cubao-area jeepney routes.

---

## Installation & Usage

The fastest way to see Busina is the live demo above. To run it locally instead:

### Prerequisites
- Node.js 18+ and npm
- A Supabase project (URL + API key)
- A HiveMQ Cloud broker (or any MQTT broker)
- A Google Maps JavaScript API key

### 1. Clone the repositories

```bash
git clone https://github.com/ALT-F4-sparkfest/Backend-MQTT-and-Firebase.git
git clone [INSERT FRONTEND REPO LINK]
git clone https://github.com/ALT-F4-sparkfest/Simulated-GPS-Dataset.git
```

### 2. Backend

```bash
cd Backend-MQTT-and-Firebase
npm install
# add Supabase and HiveMQ credentials to a .env file
npm start
```

Main endpoints: `/vehicles`, `/vehicles/:id/history`, `/vehicles/:id/eta/:stopId`, `/vehicles/:id/etas`, `/alerts`

### 3. Simulated GPS data (optional — a pre-generated dataset is already included)

```bash
cd Simulated-GPS-Dataset
python3 -m venv venv && source venv/bin/activate
pip install pandas numpy
python scripts/generate_multiroute_gps.py
python scripts/generate_ai_insights.py
```

### 4. Frontend

```bash
cd <frontend-repo>
npm install
# add your Google Maps API key and backend URL to a .env file
npm run dev
```

---

## Development Notes

This project was built end-to-end during SparkFest 2026 by a four-person remote team, with each member owning a distinct layer: hardware, backend, frontend, and AI/data. This repository consolidates the submission; the actual development history lives in the component repositories linked above, each showing incremental, timestamped commits made throughout the event rather than a single final upload.

---

## License

MIT License.
