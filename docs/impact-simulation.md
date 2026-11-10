# Impact simulation

Status: **implemented**, on **sample data**. Source: `simulateIntervention` and `reachability` in `src/lib/engine/graph.ts`, `src/modules/impact/ImpactScreen.tsx`.

## Method

1. Candidates are barriers that are confirmed and block the wheelchair profile.
2. `simulateIntervention(net, barrierId)` returns a copy of the network with the barrier removed and its segment marked as surveyed. The original network is never changed.
3. 15-minute wheelchair reachability (4 km/h) is computed before and after.
4. The screen shows both maps, the destinations reached, deltas and a generated explanation.

## Results in the sample scenario

| Scenario | Destinations within 15 min | Passable segments | Route to Poliklinika |
| --- | --- | --- | --- |
| Before (B-07 confirmed) | 2 of 5 | 14 of 22 | 1,1 km |
| Remove B-07 (stairs, S-07) | 5 of 5 | 15 of 22 | 0,8 km |
| Remove B-11 (blocked path, S-11) | 2 of 5 | 15 of 22 | 1,1 km |

These numbers come from the sample graph and are not real-world measurements.

## Assumptions shown in the app

- The intervention meets the standard and removes the barrier completely.
- Speed is a constant 4 km/h.
- Only surveyed segments without barriers count as accessible.
- Other segments do not change.
- Cost and population impact are not calculated.

## Empty and invalid states

- No barrier selected: "Hələ simulyasiya yoxdur" with a link to Urban.
- Unknown id in the URL (for example `?barrier=B-99`): "B-99 bu məlumatda tapılmadı".
