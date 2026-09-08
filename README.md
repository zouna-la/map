# 走哪啦 (ZounaLa) 开放地图插件中心

这里是 [走哪啦 (Zouna.la)](https://zouna.la) 的开放地图插件生态库。
本项目通过 GitHub Pages 静态托管于 `https://map.zouna.la/`，向所有 ZounaLa 用户开放精选与社区共建的主题地图数据。

---

## 目录索引

- `registry.json`：全量插件索引清单，记录所有已收录的地图插件元数据。
- `plugins/`：各主题地图插件的具体点位 JSON 数据。

---

## 插件数据规范 (Schema)

每个插件对应 `plugins/<plugin-id>.json`，格式示例如下（以中国三山五岳名山录为例）：

```json
{
  "id": "cn-three-mountains-five-peaks",
  "version": "1.0.0",
  "title": "中国三山五岳名山录",
  "description": "中华名山之精华，收录黄山、庐山、雁荡山“三山”与泰山、华山、衡山、恒山、嵩山“五岳”共八座传世名胜地标。",
  "contributor": "ZounaLa 探索社",
  "contributorLink": "https://github.com/zouna-la/map",
  "coordType": "wgs84",
  "category": "名山胜景",
  "themeColor": "#2E7D32",
  "points": [
    {
      "id": "huangshan",
      "name": "黄山",
      "lat": 30.1388,
      "lon": 118.1747,
      "category": "三山",
      "badgeColor": "#2E7D32",
      "description": "安徽黄山，以奇松、怪石、云海、温泉、冬雪“五绝”著称于世，素有“天下第一奇山”之美誉。"
    },
    {
      "id": "taishan",
      "name": "泰山",
      "lat": 36.2558,
      "lon": 117.1075,
      "category": "五岳",
      "badgeColor": "#E67E22",
      "description": "东岳泰山，位于山东泰安，巍峨耸立、五岳独尊，是中华民族的精神象征与历代帝王封禅圣地。"
    }
  ]
}
```

### 字段说明
- `id`: 插件全局唯一英文标识（短横线命名，如 `cn-three-mountains-five-peaks` 或 `shanghai-coffee-guide`）
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
