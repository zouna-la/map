# 走哪啦 (ZounaLa) 开放地图插件中心

这里是 [走哪啦 (Zouna.la)](https://zouna.la) 的开放地图插件生态库。
本项目通过 GitHub Pages 静态托管于 `https://map.zouna.la/`，向所有 ZounaLa 用户开放精选与社区共建的主题地图数据。

---

## 目录索引

- `registry.json`：全量插件索引清单，记录所有已收录的地图插件元数据。
- `plugins/`：各主题地图插件的具体点位 JSON 数据。
  - `cn-three-mountains-five-peaks.json`：中国三山五岳名山录（8 个名胜点位）
  - `cn-provincial-capitals.json`：中国省会与首府城市（34 个省级行政中心，包括台湾台北）

---

## 插件数据规范 (Schema)

每个插件对应 `plugins/<plugin-id>.json`，格式示例如下：

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

### 字段说明
- `id`: 插件全局唯一英文标识（短横线命名，如 `cn-provincial-capitals`）
- `version`: 语义化版本号，如 `1.0.0`
- `coordType`: 经纬度坐标系，支持 `"wgs84"`（GPS、谷歌地图、OSM 采集）或 `"gcj02"`（火星坐标系，高德、腾讯地图采集）。客户端会自动适配纠偏。
- `themeColor`: 插件主题色，在进度条及无独立点位颜色时作为兜底色。
- `points`: 点位数组。每个点包含 `id`, `name`, `lat`, `lon`，支持设置 `category`（分类）、`badgeColor`（独立气泡色）与 `description`。

---

## 如何贡献新的地图插件？

1. **Fork 本仓库**；
2. 在 `plugins/` 目录下添加你的插件数据文件，如 `plugins/my-cool-map.json`；
3. 在 `registry.json` 的 `plugins` 列表中追加一条你的插件索引信息；
4. 提交 **Pull Request** 到 `main` 分支；
5. 审核通过合并后，GitHub Pages 会自动更新发布，ZounaLa App 端用户即可在“设置 -> 足迹 -> 地图插件”中发现并添加你的主题地图！

> **注意事项**：
> 1. 请确保提交的地理信息健康合规，不涉及敏感涉密地理地标；
> 2. 经纬度务必准确校验，请勿使用伪造或错误坐标。
