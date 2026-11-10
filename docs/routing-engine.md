# Routing engine

Status: **implemented**, on **sample data**. Source: `src/lib/engine/graph.ts`, `src/lib/engine/scenario.ts`, `src/data/pilot-network.ts`.

## Model

- **Nodes** with map coordinates (1 map unit = 2.2 m) and optional points of interest.
- **Segments** (edges) with a surveyed flag and a label.
- **Barriers** on segments with a type (`stairs`, `blocked_path`, `broken_surface`, `curb`, `obstruction`, `other`) and a verification state (`confirmed`, `unverified`, `ai_estimate`, `rejected`).

## Passability per profile

| State | Meaning |
| --- | --- |
| `blocked` | A confirmed barrier blocks this profile |
| `uncertain` | An unverified or AI-only barrier exists |
| `unknown` | The segment was never surveyed |
| `ok` | Surveyed, no blocking barrier |

## Routes

- **Suitable route:** Dijkstra that excludes `blocked` segments and multiplies the cost of `uncertain` segments by 3 and `unknown` segments by 2.
- **Shortest route:** geometric shortest path for a pedestrian, then evaluated honestly for the chosen profile.

## Reachability

Conservative 15-minute reachability from the origin: only `ok` segments count. Speeds: 4.8 km/h pedestrian, 4 km/h wheelchair and stroller. Partial coverage of a segment is reported as a fraction.

## Metrics

`metrics(net, profile)` returns segments total, surveyed and unknown, passable segments for the profile, barrier records (confirmed and pending), and reachable destinations. Every number in Urban and Impact comes from these functions.

## Tests

`tests/engine.test.ts` covers route choice, penalties, reachability and intervention behaviour.
