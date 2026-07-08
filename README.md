# Team Information

**Team Name:** ALT F4
**Project Name:** Busina

# Project Brief

Roughly eight million Filipinos ride jeepneys daily with no way to know when
one is arriving, and waits routinely stretch two to four hours. The 2017
Public Utility Vehicle Modernization Program consolidated independent
drivers into cooperatives but gave those cooperatives no digital tools —
no GPS, no ridership data, no operational visibility.

Busina is a real-time fleet intelligence system that closes this gap with
three layers: low-cost, passive GPS hardware installed in each vehicle, a
real-time backend that streams and processes location data, and
role-specific dashboards for commuters, cooperative dispatchers, and local
government planners.

**Intended users/beneficiaries:** commuters (free live map and ETA access),
jeepney cooperatives (fleet visibility and compliance tooling), and local
government units (route-planning data).

**Impact:** commuters reclaim hours previously lost to uncertainty about
arrival times; drivers gain visibility into passenger demand instead of
racing for fares under the traditional boundary system; and cooperatives
gain their first affordable operational tool since PUVMP consolidation —
with a direct link to the DOTr's Service Contracting Program, which pays
cooperatives per GPS-verified kilometer traveled.

# Team Members

| Name | Role |
|---|---|
| Christopher James A. Cresencio | Data & Team Lead |
| Joaqui Rainiel A. Jerez | Backend Lead |
| Jhon Rey D. Oquendo | Frontend Lead |
| Red Colby S. Dumdum | Hardware Lead |

# Google Technologies Used

- **Google Maps JavaScript API** — powers the live fleet map, vehicle
  markers, and route rendering on the frontend.
- **Firebase** — used during early backend development for real-time data
  sync; migrated to Supabase (PostgreSQL) later in development after
  hitting Firebase's free-tier limits.

# SparkFest 2026

This project was developed as part of SparkFest 2026, the flagship
hackathon organized by the Google Developer Groups on Campus – Polytechnic
University of the Philippines (GDG on Campus PUP).

# Repository Information

- **Live Demo:** https://busina-one.vercel.app/
- **Google Drive Submission Link:** https://drive.google.com/drive/folders/14pP6RJlxPU87m19KbBnbB4tg4eHHJFsI?usp=sharing
