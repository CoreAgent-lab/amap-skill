---
name: amap
description: 通过命令行脚本直连高德地图（高德 / AMap）Web Service API，完成地理编码、逆地理编码、IP 定位、天气查询、路径规划（步行/骑行/驾车/公交）、距离测量与 POI 搜索，并可组合这些能力完成出行与旅游行程规划。当用户提到高德地图 / 高德 / AMap，或需要查询地点、天气、坐标，做路线规划 / 导航，搜索 POI（景点、餐厅、酒店等），或规划出行、旅游、一日游、周边游玩等行程时使用。
---

# AMap Skill

通过脚本直连高德地图 Web Service API。既能执行单条查询（地理编码、天气、POI、路线），也能把多条命令组合成完整的出行 / 一日游行程规划。

## Quick Start
1. 确认环境变量 `AMAP_MAPS_API_KEY` 已设置。
2. 在本 skill 目录运行 `bun scripts/amap.ts --help` 查看全部命令。
3. 从 `references/command-map.md` 选择匹配的命令，参考 `references/examples.md` 的可直接运行示例。

## Workflow
1. 判断用户意图，选择对应命令；用户给的是文字地址时优先用 `*-route-address` 系列路径规划命令。
2. 保持输出为高德返回的原始 JSON，不额外包裹字段。
3. 任何非 0 的 API 业务状态都视为失败（参见 `references/command-map.md` 的 Exit Codes）。

## 行程 / 一日游规划（组合用法）
当用户要求规划出行、旅游、一日游、周边游玩等行程时，按以下步骤组合现有命令：
1. **定位与搜索景点**：用 `poi-text`（按关键词，如「西湖」「景点」）或 `poi-around`（按坐标 + 半径）找出候选地点，必要时配合 `geocode` 把地址转坐标。
2. **查天气**：用 `weather --city <城市>` 获取当天 / 多天天气，辅助安排室内外行程。
3. **串联路线**：按游览顺序，对相邻两点用 `walk-route-*` / `drive-route-*` / `transit-route-*` 规划路线，用 `distance` 估算距离与耗时。
4. **汇总**：基于上述查询结果，输出包含景点、顺序、交通方式、用时和天气提示的行程安排。

## Commands
- 完整命令映射：`references/command-map.md`
- 可直接运行的示例：`references/examples.md`

## Notes
- 本 skill 以脚本为主，不运行 MCP server。
- 仅支持 `AMAP_MAPS_API_KEY` 一个环境变量。
