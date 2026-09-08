# ZounaLa Open Map Plugin Center

[English](README.md) | [简体中文](README_CN.md)

Welcome to the open map ecosystem repository for [ZounaLa (走哪啦)](https://zouna.la).
This repository is statically hosted via GitHub Pages at `https://map.zouna.la/`, delivering curated, community-driven thematic map data and points/regions of interest to ZounaLa users worldwide.

---

## Directory Overview

- `registry.json`: Global manifest cataloging all available plugins, metadata, versions, and endpoints.
- `plugins/`: Standalone JSON data files containing points/regions of interest for each theme:
  - `cn-three-mountains-five-peaks.json`: Three Mountains and Five Sacred Peaks of China (8 prominent mountain landmarks)
  - `cn-provincial-capitals.json`: Provincial Capitals & Centers of China (34 provincial administrative centers, including Taipei)

---

## Plugin Data Specification (Schema)

Each plugin resides at `plugins/<plugin-id>.json`. The standard schema is illustrated below:

```json
{
  "id": "cn-provincial-capitals",
  "version": "1.0.0",
  "title": "中国省会与首府城市",
  "description": "收录中国 34 个省级行政区的省会城市、自治区首府、直辖市与特别行政区地标（包括台湾台北）。",
  "contributor": "ZounaLa 探索社",
  "contributorLink": "https://github.com/zouna-la/map",
  "coordType": "wgs84",
  "category": "人文地理",
  "themeColor": "#3498DB",
  "points": [
    {
      "id": "hangzhou",
      "name": "杭州",
      "lat": 30.2741,
      "lon": 120.1551,
      "category": "华东省会",
      "badgeColor": "#1ABC9C",
      "description": "浙江省省会，“人间天堂”，全球领先的数字经济与互联网创新之城。",
      "boundaryType": "polygon",
      "boundary": [
        [120.1234, 30.1234],
        [120.1567, 30.1456],
        [120.1890, 30.1678],
        [120.1234, 30.1234]
      ]
    },
    {
      "id": "beijing",
      "name": "北京",
      "lat": 39.9042,
      "lon": 116.4074,
      "category": "直辖市",
      "badgeColor": "#E74C3C",
      "description": "中华人民共和国首都，全国政治、文化、国际交往和科技创新中心。"
    }
  ]
}
```

### Field Definitions
- `id`: Globally unique lowercase alphanumeric identifier with hyphens (e.g., `cn-provincial-capitals`).
- `version`: Semantic version string (e.g., `1.0.0`).
- `coordType`: Coordinate reference system: `"wgs84"` (GPS, OpenStreetMap, Google Maps) or `"gcj02"` (Amap, Tencent Maps). The client automatically rectifies and transforms coordinates.
- `themeColor`: Hex color code for the plugin theme, applied to progress bars and as a fallback marker tint.
- `points`: Array of POI / ROI objects:
  - `id`: Unique point/region identifier (Required).
  - `name`: Display name (Required).
  - `lat`, `lon`: Center anchor coordinates (Required, used for badge pin positioning and map bounding box fitting).
  - `category`: Category tag (Optional).
  - `badgeColor`: Distinct marker/polygon tint color (Optional, e.g., `#1ABC9C`).
  - `description`: Summary description (Optional).
  - `boundaryType`: Geometry type (Optional, currently supports `"polygon"`).
  - `boundary`: Coordinates array defining the closed polygon vertices (Optional, format: `[[lon1, lat1], [lon2, lat2], ...]`, following the GeoJSON standard with longitude preceding latitude).

### Exploration & Check-in Matching Algorithm
- **Polygon Area Mode**: If a point has `boundaryType: "polygon"` and contains valid vertices ($\ge 3$), the client automatically performs the **Ray-Casting (Point-in-Polygon) Algorithm**. Any user footprint falling inside the closed boundary will instantly unlock/illuminate this area! The map also renders a translucent polygon overlay.
- **Physical Distance Mode**: If no boundary is configured or footprint falls outside, the client falls back to the default spherical physical distance check ($\le 1000$ meters from the center anchor).

---

## Community Submission Guidelines & Content Redlines

To maintain a healthy, trustworthy, and premium exploration experience for all ZounaLa users, every submitted or updated map plugin must strictly adhere to the following standards. Non-compliant submissions will be rejected without merge:

1. **Strict Prohibition of Advertising & Commercial Promotion**:
   - Do NOT include any commercial advertisements, promotional copy, social media/WeChat handles for lead generation, affiliate links, or external marketing URLs in point names, descriptions, or contributor fields.
   - All points of interest must hold genuine cultural, historical, geographical, or natural exploration value for the public.

2. **Strict Prohibition of Violent, Illegal, and Harmful Content**:
   - Content promoting violence, cruelty, terrorism, extremism, bullying, self-harm, or illegal acts is strictly forbidden.
   - Content containing pornography, obscenity, vulgarity, gambling, narcotics, harassment, or violations of law and public order is strictly forbidden.

3. **Authentic Geographical Data & Security Compliance**:
   - Prohibit inclusion of sensitive military exclusion zones, confidential state infrastructure, or undisclosed research facilities.
   - Place names, administrative jurisdictions, and boundaries must be accurate, respectful, and fully compliant with national surveying and geographical regulations.
   - Coordinates must represent real-world locations verified through accurate mapping tools. Spoofed, fake, or malicious coordinates are strictly forbidden.

4. **Versioning & Maintenance**:
   - Whenever you update or expand point data, bump the `version` field (e.g., `1.0.0` → `1.0.1`) so that client applications can automatically detect changes and sync seamlessly in the background.

---

## How to Contribute

1. **Fork** this repository.
2. Create your plugin data file under `plugins/` (e.g., `plugins/my-scenic-route.json`).
3. Append your plugin entry and metadata to `registry.json`.
4. Submit a **Pull Request** to the `main` branch with a concise summary of the map's theme.
5. Once reviewed and merged, GitHub Pages will automatically deploy the update, making your map immediately discoverable in the ZounaLa App under **Settings -> Footprint -> Map Plugins**!
