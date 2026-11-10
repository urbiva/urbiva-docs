# Product overview

**Mission.** Make cities more accessible, inclusive and intelligent through AI-powered infrastructure analysis and intervention simulation.

**Tagline.** Every city. Every possibility.

## Problem

The shortest walking route is not passable for everyone. Stairs, high curbs, broken surfaces and obstacles turn a short trip into a long or impossible one for wheelchair users, parents with strollers and older people. Cities rarely have up-to-date, trustworthy data about these barriers, and planners lack a simple way to see which repair would help the most people.

## Users

| User | Need | Module |
| --- | --- | --- |
| Resident with a mobility need | A route that suits me, and honesty about what is not verified | Urbiva Go |
| Any resident | A quick way to report a barrier | Urbiva Vision |
| City planner | A trustworthy picture of barriers and their verification state | Urbiva Urban |
| City planner | Evidence of what a repair would change | Urbiva Impact |

## What exists today (hackathon MVP)

- **Implemented:** graph routing with mobility profiles, barrier reporting with an AI estimate and human confirmation, planner review, reachability simulation, a guided nine-step demo.
- **Sample data:** everything runs on "Pilot zona A", an invented network of 17 nodes and 22 segments. No real streets, no real users.
- **Not built:** accounts, server storage, real map data, turn-by-turn navigation, a prioritisation view, the own vision model.

## The nine-step demo

1. Wheelchair profile and destination Poliklinika.
2. Suitable route (1,1 km, surveyed) vs shortest route (0,8 km, through the unsurveyed underpass S-07).
3. Report the underpass in Vision.
4. Confirm the category; report B-07 is stored as unverified.
5. The planner confirms B-07 in Urban.
6. The planner simulates removing B-07.
7. The graph is recalculated on a copy.
8. 15-minute reachability rises from 2 of 5 to 5 of 5 destinations.
9. Impact shows the result, the assumptions and the limits.
