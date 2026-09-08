# 走哪啦 (ZounaLa) 开放地图插件中心

[English](README.md) | [简体中文](README_CN.md)

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

## 社区提交规范与内容红线 (Community Guidelines)

为保障广大走哪啦（ZounaLa）用户的探索体验与数据健康，所有提交或修改的地图插件必须严格遵守以下规范。违规内容将直接被拒绝合并（Close PR）：

1. **严禁发布商业广告与导流推广**：
   - 严禁在点位名称、描述说明、外部链接或贡献者署名中夹带任何商业广告、推广软文、微信/公众号引流、优惠促销、虚假宣传或跳转外链；
   - 地图标注点应具备广泛的公共探索价值、人文历史底蕴、自然景观或纯粹的地理文化特色。

2. **严禁宣传暴力、违法违规与违背公序良俗的内容**：
   - 严禁宣扬暴力恐吓、血腥残忍、恐怖主义、极端主义、霸凌、自残或唆使违法犯罪行为；
   - 严禁包含淫秽色情、低俗庸俗、赌博、毒品、封建迷信以及任何侵犯他人隐私或违背公序良俗的内容。

3. **地理地标真实合规与保密红线**：
   - 严禁收录涉及国防军事禁区、国家涉密工程、科研未公开设施等敏感地理信息；
   - 地理标注名称、行政归属与边界描述必须准确严肃，严格遵守国家测绘地理信息法律法规；
   - 经纬度坐标必须经过真实地理验证，严禁伪造坐标或故意偏移恶搞。

4. **版本迭代与维护**：
   - 插件修正或扩充点位时，请按规范递增 `version` 版本号（如 `1.0.0` → `1.0.1`），以便客户端自动感知并静默同步最新数据。

---

## 如何贡献新的地图插件？

1. **Fork 本仓库**；
2. 在 `plugins/` 目录下添加你的插件数据文件，如 `plugins/my-cool-map.json`；
3. 在 `registry.json` 的 `plugins` 列表中追加一条你的插件索引信息；
4. 提交 **Pull Request** 到 `main` 分支，并在 PR 描述中简述地图主题；
5. 审核通过合并后，GitHub Pages 会自动更新发布，ZounaLa App 端用户即可在“设置 -> 足迹 -> 地图插件”中发现并添加你的主题地图！
