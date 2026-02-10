# amap-skill

Claude Code skill for querying [AMap (高德地图) Web Service API](https://lbs.amap.com/api/webservice/summary) — geocoding, routing, weather, POI search, and more.

## Skills

| Skill | Description |
|-------|-------------|
| **amap** | 通过脚本直连高德 Web Service API，支持地理编码、逆地理编码、IP 定位、天气查询、路径规划、距离测量和 POI 搜索 |

## Supported Commands

| Command | Description |
|---------|-------------|
| `geocode` | 地理编码（地址 → 坐标） |
| `reverse-geocode` | 逆地理编码（坐标 → 地址） |
| `ip-location` | IP 定位 |
| `weather` | 天气查询 |
| `bike-route-coords` / `bike-route-address` | 骑行路径规划 |
| `walk-route-coords` / `walk-route-address` | 步行路径规划 |
| `drive-route-coords` / `drive-route-address` | 驾车路径规划 |
| `transit-route-coords` / `transit-route-address` | 公交路径规划 |
| `distance` | 距离测量 |
| `poi-text` / `poi-around` / `poi-detail` | POI 搜索 |

## Prerequisites

- [Bun](https://bun.sh) runtime
- AMap Web Service API Key — set via `AMAP_MAPS_API_KEY` environment variable

## Installation

Copy `skills/amap/` into your Claude Code skills directory:

```bash
# Project-level
cp -r skills/amap .claude/skills/amap

# Or user-level
cp -r skills/amap ~/.claude/skills/amap
```

Or install as a plugin:

```bash
claude plugin add kaichen/amap-skill
```

## Development

```bash
bun install
bun run test
bun run amap:help
```

## License

MIT
