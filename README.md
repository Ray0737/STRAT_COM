# ICBM Simmulation (LGM-30G Tactical Interface)
### [LIVE INTERFACE ACCESS](https://stratcomtrack.vercel.app/)

A high-fidelity, interactive tactical map interface built with **Leaflet.js**. This system simulates the deployment, targeting, and impact visualization of LGM-30G Minuteman III assets. It features a sophisticated multi-unit management deck and real-time ballistic telemetry.

## DATA WARNING & DISCLAIMER

> [!CAUTION]
> **SENSITIVE GEOSPATIAL DATA:** All silo locations and military installation coordinates provided within this interface correspond to **actual, real-world ICBM sites** and defense facilities. 
> 
> This tool is strictly for **educational, historical, and creative visualization purposes**. Users are reminded that this data is sourced from publicly available military intelligence and should be handled with appropriate discretion.

---

## Features

* **Multi-Unit Management:** Deploy and monitor multiple independent missile cells simultaneously without overlapping data.
* **Persistent Blast Radii:** Automatic rendering of multi-stage thermal and pressure wave radii upon target selection. Unlike standard previews, these remain visible during flight for strategic assessment.
* **Hard-Target Locking:** Once a coordinate is designated, the logic "freezes" the target for that unit to prevent accidental drift or repositioning.
* **Real-Time Telemetry:** Calculates distance and flight time based on a Mach 20+ ($24,140 \text{ km/h}$) cruise speed using the Haversine formula.
* **Variable Yield Scaling:** Supports multiple warhead configurations (W87, W88, B83) with power-law scaling for blast effects:
    $$R \approx Y^{0.33}$$
* **Dynamic Intelligence Layers:** Interactive markers for silo locations and global military assets with detailed metadata popups.

## Operation Protocol

1.  **Initialize Unit:** Click **ADD NEW UNIT** in the command deck.
2.  **Designate Target:** Click **SET TARGET** on a specific missile card.
3.  **Lock Coordinates:** Click any location on the map. The system will immediately calculate telemetry and render the persistent blast zone. 
    * *Note: Once locked, the radius cannot be moved for that specific unit.*
4.  **Confirm Launch:** Press **CONFIRM LAUNCH**. The status will shift to **IN-FLIGHT** with a real-time countdown.
5.  **Impact:** Upon $T=0$, the flight trajectory is purged, and the permanent impact signature is rendered to the global map.

## Technical Stack

* **Engine:** [Leaflet.js](https://leafletjs.com/) (Geospatial rendering)
* **Basemap:** CartoDB Dark Matter (High-contrast tactical UI)
* **Logic:** Vanilla JavaScript (ES6+)
* **Math:** * **Distance:** Spherical Law of Cosines
    * **Radii:** $\text{Radius} = \text{Yield}^{0.4} \times \text{Constant}$

