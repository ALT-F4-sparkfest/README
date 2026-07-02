# Busina
**Smarter commutes, better journeys.**

*This project was developed for SparkFest 2026.*

---

## Project Brief
In the Philippines, over 8 million daily commuters rely on jeepneys, frequently enduring unpredictable wait times and inefficient manual dispatching. While the Public Utility Vehicle Modernization Program (PUVMP) mandates fleet restructuring, transport cooperatives lack the accessible digital tools required to monitor, manage, and optimize their operations.

**Busina** bridges this operational gap with a real-time fleet tracking and ETA prediction platform tailored for modernized jeepneys. The system translates low-latency geographic and vehicular data into predictable schedules for commuters and analytical dashboards for dispatchers. By providing a software-complete Minimum Viable Product (MVP) powered by a robust data simulation pipeline, Busina demonstrates how real-time tracking can eliminate commuting uncertainty, mitigate vehicle bunching, and provide transport cooperatives with actionable, data-driven utility.

---

## Team ALT-F4
* **Christopher James A. Cresencio** — AI & Data Lead
* **Joaqui Rainiel A. Jerez** — Backend Lead
* **Jhon Rey D. Oquendo** — Frontend Lead
* **Red Colby S. Dumdum** — Hardware Lead

---

## Google Technologies Used
* **Google Maps JavaScript API:** Serves as the core visualization layer on the frontend client application. It maps real-time vehicle positions, tracks live transit paths, and visually represents demand hotspots.
* **Firebase (Initial Development):** Utilized during the initial prototyping and database structuring phase for real-time syncing and validation before migrating storage infrastructure to Supabase for production scaling.

---

## System Architecture & Component Breakdown

### 1. Frontend Client (Web Application)
Built using React and Vite, the user interface acts as a dual-purpose console serving both commuters and cooperative dispatchers. It establishes a persistent websocket connection to receive instantaneous position and alert streams.

### 2. Backend Server & Messaging Layer
An asynchronous Node.js and Express server serves as the orchestrator of the platform. It handles RESTful API requests, ingests continuous telemetric streams via HiveMQ Cloud (MQTT), processes system alerts, and broadcasts instantaneous updates down to client applications using Socket.IO.

### 3. Database Infrastructure
Supabase (PostgreSQL) acts as the state and historical repository. It logs vehicle master profiles, persistent telemetry histories, transit stop configurations, and compiled operational metrics.

### 4. Telemetry Strategy & Hardware Roadmap
* **Current State (Phase 1 MVP):** Driven by a high-fidelity data pipeline built in Python, simulating actual routes, transit times, stops, and historical telemetry across 7,390 trips and 68,880 exact GPS data entries.
* **Future State (Phase 2 Deployment):** Direct physical integration using low-cost ESP32 microcontrollers outfitted with GPS modules (such as the NEO-6M) mounted inside vehicles, broadcasting telemetry directly to the HiveMQ MQTT broker over cellular networks.

---

## Key Features

### Frontend Features
* **Live Interactive Map:** Renders high-fidelity markers for the entire operating fleet, reflecting geographic movements instantaneously on a customized Google Maps interface.
* **Commuter ETA Matrix:** A dynamic lookup interface where commuters select a specific transit stop and receive live arrival timelines for approaching vehicles.
* **Dispatcher Control Dashboard:** A comprehensive overhead management view showing active routes, total vehicles in service, and historical performance charts.

### Backend Features
* **Asynchronous Event Ingestion:** Uses a non-blocking architecture to consume telemetry packets simultaneously from multiple vehicular sources via MQTT.
* **Real-Time Data Distribution:** Converts incoming hardware/simulated message streams into instant client-side updates via Socket.IO, minimizing network polling overhead.
* **Algorithmic Bunching Detection:** Monitors distance intervals between successive vehicles on identical routes to trigger automated deployment warnings when vehicles crowd together.

### Data & AI Features
* **Heuristic Predictive Modeling:** Computes dynamic ETA windows by factoring in distance, historical travel times for specific hourly blocks, and current route congestion indicators.
* **Analytical Performance Charts:** Renders telemetry trends using Recharts, highlighting system-wide KPIs such as average speed vectors, demand heatmaps, and on-time percentages.

### Hardware Features (Phase 2 Blueprint)
* **Low-Cost Telemetry Units:** Modular ESP32 architecture designed to offer transport cooperatives an incredibly cheap alternative to expensive commercial GPS tracking devices.
* **Edge Processing:** Configured to bundle, parse, and transmit coordinate strings at optimized intervals to conserve cellular data footprints during active transit.

---

## Tech Stack
| Layer | Technologies Used |
| :--- | :--- |
| **Frontend UI/UX** | React.js, Vite, Google Maps API, Recharts, Tailwind CSS |
| **Backend Core** | Node.js, Express, Socket.IO |
| **Data Brokerage** | HiveMQ Cloud (MQTT) |
| **Database & Storage** | Supabase (PostgreSQL) |
| **Simulation Pipeline** | Python, Pandas |

---

## Production Deployment & Live Links

The application is deployed and accessible on cloud infrastructure for real-world testing and evaluation.

* **Frontend Interface (Live MVP):** `https://busina-full-stack.vercel.app`
* **Main GitHub Repository:** `https://github.com/orgs/ALT-F4-sparkfest/repositories`

---

## Core API Endpoints

The backend exposes the following RESTful endpoints to manage fleet states and supply historical analytics:

| Endpoint | Method | Description |
| :--- | :--- | :--- |
| `/vehicles` | GET | Returns a comprehensive array of all active vehicles, current locations, and operational statuses. |
| `/vehicles/:id/history` | GET | Retrieves the persistent historical GPS coordinate track for a designated vehicle ID. |
| `/vehicles/:id/eta/:stopId` | GET | Computes and returns the targeted time of arrival for a specific vehicle approaching a designated stop. |
| `/vehicles/:id/etas` | GET | Returns an array of predictive arrival times for a vehicle across all remaining stops on its assigned route. |
| `/alerts` | GET | Fetches all actively recorded operational anomalies, focusing primarily on current vehicle bunching incidents. |

---

## Local Setup & Development (Optional)

If you prefer to audit or run the architecture inside a local development environment, follow these steps:

1. Clone the central repository to your machine.
2. Verify that Node.js (v18+ recommended) is available locally.
3. Install dependencies by executing `npm install` inside both the frontend and backend project directories.
4. Construct a local `.env` file within the root directories to host your environment tokens:
   ```env
   GOOGLE_MAPS_API_KEY=your_api_key_here
   SUPABASE_URL=your_supabase_project_url
   SUPABASE_KEY=your_supabase_anon_key
