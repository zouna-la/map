# ZounaLa Open Map Plugin Center

[English](README.md) | [简体中文](README_CN.md)

Welcome to the open map ecosystem repository for [ZounaLa (走哪啦)](https://zouna.la).
This repository is statically hosted via GitHub Pages at `https://map.zouna.la/`, delivering curated, community-driven thematic map data and points of interest (POI) to ZounaLa users worldwide.

---

## Directory Overview

- `registry.json`: Global manifest cataloging all available plugins, metadata, versions, and endpoints.
- `plugins/`: Standalone JSON data files containing points of interest for each theme:
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
      "id": "beijing",
      "name": "北京",
      "lat": 39.9042,
      "lon": 116.4074,
      "category": "直辖市",
      "badgeColor": "#E74C3C",
      "description": "中华人民共和国首都，全国政治、文化、国际交往和科技创新中心。"
    },
    {
      "id": "taipei",
      "name": "台北",
      "lat": 25.0330,
      "lon": 121.5654,
      "category": "省会/中心",
      "badgeColor": "#16A085",
      "description": "台湾地区主要中心城市，坐落于台北盆地，拥有台北101与深厚文创底蕴。"
    }
  ]
}
```

### Field Definitions
- `id`: Globally unique lowercase alphanumeric identifier with hyphens (e.g., `cn-provincial-capitals`).
- `version`: Semantic version string (e.g., `1.0.0`).
- `coordType`: Coordinate reference system: `"wgs84"` (GPS, OpenStreetMap, Google Maps) or `"gcj02"` (Amap, Tencent Maps). The client automatically rectifies and transforms coordinates.
- `themeColor`: Hex color code for the plugin theme, applied to progress bars and as a fallback marker tint.
- `points`: Array of POI objects. Each point includes `id`, `name`, `lat`, and `lon`, with optional `category`, `badgeColor` (distinct marker tint), and `description`.

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
