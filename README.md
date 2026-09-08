# 走哪啦 (ZounaLa) 开放地图插件中心

这里是 [走哪啦 (Zouna.la)](https://zouna.la) 的开放地图插件生态库。
本项目通过 GitHub Pages 静态托管于 `https://map.zouna.la/`，向所有 ZounaLa 用户开放精选与社区共建的主题地图数据。

---

## 目录索引

- `registry.json`：全量插件索引清单，记录所有已收录的地图插件元数据。
- `plugins/`：各主题地图插件的具体点位 JSON 数据。

---

## 插件数据规范 (Schema)

每个插件对应 `plugins/<plugin-id>.json`，格式示例如下：

```json
{
  "id": "cn-world-heritage",
  "version": "1.0.0",
  "title": "中国世界遗产名录",
  "description": "简要介绍该地图插件的主题背景（推荐 100 字以内）",
  "contributor": "贡献者名称或机构",
  "contributorLink": "https://example.com",
  "coordType": "wgs84",
  "category": "世界遗产",
  "themeColor": "#E74C3C",
  "points": [
    {
      "id": "taishan",
      "name": "泰山",
      "lat": 36.255833,
      "lon": 117.1075,
      "category": "文化与自然双遗产",
      "badgeColor": "#E74C3C",
      "description": "可选补充说明"
    }
  ]
}
```

### 字段说明
- `id`: 插件全局唯一英文标识（短横线命名，如 `shanghai-coffee-guide`）
- `version`: 语义化版本号，如 `1.0.0`
- `coordType`: 经纬度坐标系，支持 `"wgs84"`（如 GPS、谷歌地图、OSM 采集）或 `"gcj02"`（火星坐标系，如高德地图、腾讯地图采集）。客户端会自动处理纠偏。
- `points`: 点位数组。每个点包含 `id`, `name`, `lat`, `lon`。

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
