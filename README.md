# Hex Picker – Leaflet × H3

Interactive web map for drawing **non‑overlapping, color‑coded zones** on an H3 hexagonal grid.


## Live demo
👉 [Try it on GitHub Pages](https://alti3.github.io/HexPicker/)


## Screenshot


![Hex Picker screenshot](image.png)

---

## Features

| Category                                                                               | Details                                                                                                                                            |
| -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Grid & view**                                                                        | Leaflet map with on‑the‑fly H3 tessellation (default resolution 8, changeable up to 15).                                                           |
| **Selection**                                                                          | Click individual hexes or draw a polygon to bulk‑select free (un‑assigned) cells. Live counter shows how many cells are in the working selection.  |
| **Zones**                                                                              |                                                                                                                                                    |
| • Create zones from a selection – user picks **unique name & #hex color** (validated). |                                                                                                                                                    |
| • Zones never overlap – a hexagon can belong to one zone only.                         |                                                                                                                                                    |
| • Edit mode: add/remove hexes inside a zone.                                           |                                                                                                                                                    |
| • Change zone color anytime by clicking the color swatch.                              |                                                                                                                                                    |
| • Delete zones.                                                                        |                                                                                                                                                    |
| **Styling**                                                                            | Zone interiors fill with chosen color; a bold outline is generated from `h3.cellsToMultiPolygon`, so only the outer/inner perimeter is emphasized. |
| **Export**                                                                             | One‑click clipboard copy:                                                                                                                          |
| `Copy Zones Cells IDs` → JSON array `[{zone_name, zone_color, zone_cells:[...]}, …]`   |                                                                                                                                                    |
| `Copy Zones GeoJSON` → FeatureCollection (MultiPolygon per zone).                      |                                                                                                                                                    |
| **Other UI**                                                                           | Resolution switcher (prompts before clearing data).                                                                                                |
| Clear current working selection.                                                       |                                                                                                                                                    |

---

## Tech stack

* **HTML / CSS / JavaScript** (vanilla)
* [Leaflet](https://leafletjs.com/) – map rendering
* [Leaflet.draw](https://leaflet.github.io/Leaflet.draw/) – free‑hand polygon tool
* [H3‑js](https://github.com/uber/h3-js) – geospatial indexing & polygon utilities

---

## Usage

1. **Select hexes**
   *Single click* or **Draw Polygon** to build a working selection.
2. **Create Zone**
   Click **Create Zone …** – enter a unique name and #RRGGBB color.
3. **Edit zone**
   Press **Edit** next to a zone, then click hexes to add/remove. **Finish Editing** to save.
4. **Change color**
   Click the zone’s color swatch, enter a new *unique* #hex.
5. **Delete zone**  ✕ button.
6. **Export**  Use **Copy Zones Cells IDs** or **Copy Zones GeoJSON** and paste where needed (e.g. [geojson.io](https://geojson.io/)).

> **Tip:** Changing the H3 resolution clears all zones – you’ll be prompted first.

---

### Local development

```bash
git clone https://github.com/alti3/HexPicker.git
cd HexPicker
# open index.html in your favourite browser
```

### Docker

```bash
docker build -t hexpicker .
docker run -p 8080:80 hexpicker
```

Then visit [http://localhost:8080](http://localhost:8080).

---

## Contributing
Pull requests and issues are welcome! Please keep PRs focused and include screenshots/GIFs where relevant.

## License
[MIT](LICENSE)
