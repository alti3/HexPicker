# Hex Picker – Leaflet × H3

Interactive web map for drawing **non‑overlapping, color‑coded zones** on an H3 hexagonal grid.


## Live demo
👉 [Try it on GitHub Pages](https://alti3.github.io/HexPicker/)


## Screenshot

![Hex Picker screenshot](image.png)
*(Note: Screenshot may not reflect the latest UI additions like Import/Export buttons and the zone summary display.)*

---

## Features

| Category                                                                               | Details                                                                                                                                                                                             |
| -------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Grid & view**                                                                        | Leaflet map with on‑the‑fly H3 tessellation (default resolution 8, changeable up to 15).                                                                                                            |
| **Selection**                                                                          | Click individual hexes or draw a polygon to bulk‑select free (un‑assigned) cells. Live counter shows how many cells are in the working selection.                                                    |
| **Zones**                                                                              |                                                                                                                                                                                                     |
| • Create zones from a selection – user picks **unique name & #hex color** (validated). |                                                                                                                                                                                                     |
| • Zones never overlap – a hexagon can belong to one zone only.                         |                                                                                                                                                                                                     |
| • Edit mode: add/remove hexes inside a zone.                                           |                                                                                                                                                                                                     |
| • Change zone color anytime by clicking the color swatch.                              |                                                                                                                                                                                                     |
| • Delete zones.                                                                        |                                                                                                                                                                                                     |
| • **Live summary:** Total count of zones, hexagons, and area displayed below the list.   |                                                                                                                                                                                                     |
| **Styling**                                                                            | Zone interiors fill with chosen color; a bold outline is generated from `h3.cellsToMultiPolygon`, so only the outer/inner perimeter is emphasized.                                                  |
| **Export & Import**                                                                    |                                                                                                                                                                                                     |
| • `Copy Zones Cells IDs`                                                               | → JSON array of zone details and H3 cell IDs (to clipboard).                                                                                                                                        |
| • `Copy Zones GeoJSON`                                                                 | → GeoJSON FeatureCollection of zones (MultiPolygons, to clipboard).                                                                                                                                 |
| • `Export GeoJSON File`                                                                | → Downloads the same GeoJSON FeatureCollection as a `.geojson` file.                                                                                                                                |
| • `Import GeoJSON Zones`                                                               | → Upload a GeoJSON FeatureCollection. Zones are created with names/colors from properties (defaults used if missing/conflicting). Includes H3 resolution check and prompts to clear existing data. |
| **Other UI**                                                                           | Resolution switcher (prompts before clearing data).                                                                                                                                                   |
|                                                                                        | Clear current working selection.                                                                                                                                                                    |

---

## Tech stack

* **HTML / CSS / JavaScript** (vanilla)
* [Leaflet](https://leafletjs.com/) – map rendering
* [Leaflet.draw](https://leaflet.github.io/Leaflet.draw/) – free‑hand polygon tool
* [H3‑js](https://github.com/uber/h3-js) – geospatial indexing & polygon utilities

---

## Usage

1.  **Select hexes**
    *Single click* or **Draw Polygon** to build a working selection.
2.  **Create Zone**
    Click **Create Zone** – enter a unique name and #RRGGBB color.
3.  **Import GeoJSON**
    Click **Import GeoJSON**, select your `.geojson` file. This allows you to load zones from a previously exported or externally created file. *Note: Importing will clear existing zones after confirmation if any are present.*
4.  **Edit zone**
    Press the <i class="fas fa-pencil-alt"></i> **Edit** button next to a zone, then click hexes on the map to add/remove them from that zone. Click **Finish Editing** to save changes.
5.  **Change color**
    Click the zone’s color swatch in the list, then enter a new *unique* #hex color.
6.  **Delete zone**
    Press the <i class="fas fa-trash-alt"></i> **Delete** button next to a zone.
7.  **Export**
    *   **Copy Zones Cells IDs**: Copies a JSON structure with zone names, colors, and their H3 cell IDs to the clipboard.
    *   **Copy Zones GeoJSON**: Copies a GeoJSON FeatureCollection (with MultiPolygons) of all zones to the clipboard (e.g., for pasting into [geojson.io](https://geojson.io/)).
    *   **Export GeoJSON File**: Downloads the same GeoJSON FeatureCollection directly as a `zones.geojson` file.

> **Tip:** Changing the H3 resolution clears all zones – you’ll be prompted first.

---

### Local development

```bash
git clone https://github.com/alti3/HexPicker.git
cd HexPicker
open index.html # this opens index.html in your default browser
```

### Bun

```bash
bun index.html
# then visit http://localhost:3000 in your browser
```

### Docker

```bash
docker build -t hexpicker .
docker run -p 8080:80 hexpicker
# then visit http://localhost:8080 in your browser
```

---

## Contributing
Pull requests and issues are welcome!

Please keep PRs focused and include screenshots/GIFs where relevant.

## License
[MIT](LICENSE)
