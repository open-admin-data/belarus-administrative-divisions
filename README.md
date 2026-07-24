# Belarus Administrative Divisions / Беларусь



## Overview

| Item | Details |
|------|---------|
| Region | 7 |
| District | 119 |
| Coordinates | ✅ Included (all levels) |
| Formats | JSON, NDJSON, CSV |
| License | CC-BY-4.0 |
| Last Updated | 2026-07-24 |
| Website | [openadmindata.org/by](https://openadmindata.org/by/) |
| API | [openadmindata.org/api/by](https://openadmindata.org/api/by/) |

## Browse by Region

| # | Region | Districts | Link |
|---|----|----|------|
| 1 | Брэсцкая (Brest) | 16 | [Browse](divisions/brest-by001/) |
| 2 | Гомельская (Gomel) | 21 | [Browse](divisions/gomel-by002/) |
| 3 | Гродзенская (Grodno) | 17 | [Browse](divisions/grodno-by003/) |
| 4 | Мінская (Minsk) | 22 | [Browse](divisions/minsk-by004/) |
| 5 | Мінск (Minsk City) | 1 | [Browse](divisions/minsk-city-by005/) |
| 6 | Магілёўская (Mogilev) | 21 | [Browse](divisions/mogilev-by006/) |
| 7 | Віцебская (Vitebsk) | 21 | [Browse](divisions/vitebsk-by007/) |

## Data Files

| File | Format | Description |
|------|--------|-------------|
| [all-region.json](data/all-region.json) | JSON | All 7 region records |
| [all-district.json](data/all-district.json) | JSON | All 119 district records |
| [all-flat.json](data/all-flat.json) | JSON | Levels 1-1 flat array |
| [all-flat.ndjson](data/all-flat.ndjson) | NDJSON | Streaming format |
| [all-flat.csv](data/all-flat.csv) | CSV | Spreadsheet format |
| [hierarchy.json](data/hierarchy.json) | JSON | Nested tree |
| [schema.json](data/schema.json) | JSON Schema | Data schema |

## Quick Start

### Python

```python
import json

with open("data/all-region.json", "r", encoding="utf-8") as f:
    data = json.load(f)

for r in data:
    print(f"{r['name']['local']} ({r['name']['en']}) — {r['children_count']['district']} districts")
```

### JavaScript

```javascript
import { readFileSync } from "fs";

const data = JSON.parse(readFileSync("data/all-region.json", "utf-8"));
console.log(`Total: ${data.length} regions`);
```

## Schema

| Field | Type | Description |
|-------|------|-------------|
| `id` | string | Unique identifier |
| `level` | integer | 1=region, 2=district |
| `level_name` | object | Level label (local + English) |
| `name.local` | string | Name in local script |
| `name.en` | string | English name |
| `name.slug` | string | URL-safe slug |
| `parent` | object/null | Parent division reference |
| `ancestors` | array | Full ancestor chain |
| `children_count` | object | Count of children per level |
| `zip_codes` | array | Postal codes (where available) |
| `geo.lat` | string | Latitude (WGS84) |
| `geo.lon` | string | Longitude (WGS84) |

Full schema: [data/schema.json](data/schema.json)

## Hierarchy Browse

```
divisions/{region-slug}/
```

Districts are listed inline in each region's README.

## AI Integration

- [llms.txt](docs/llms.txt) — Quick reference for AI agents
- [llms-full.txt](docs/llms-full.txt) — Summary with per-region links
- [Per-region data](docs/llms-full/) — Full data by region

## Citation

```
Belarus Administrative Divisions Dataset (CC-BY-4.0)
URL: https://github.com/open-admin-data/belarus-administrative-divisions
```

See [CITATION.cff](CITATION.cff) for machine-readable citation.

## License

- **Data**: [CC-BY-4.0](LICENSE)

## Related

- [Open Admin Data](https://openadmindata.org) — Browse, search and explore administrative divisions for every country
- [open-admin-data](https://github.com/open-admin-data) — GitHub organization with all country repos
- [ListBase](https://www.listbase.org) — Structured reference data for every country
