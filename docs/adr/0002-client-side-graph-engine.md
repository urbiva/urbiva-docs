# ADR 0002: Graph engine in pure TypeScript, run in the browser

- Status: Accepted
- Date: 2026-11-10

## Context
The demo needs instant routing and simulation on a small network without a backend.

## Decision
Implement Dijkstra, passability, reachability and intervention simulation as pure functions in `src/lib/engine`.

## Consequences
Fast, testable and offline. A real city network will need server-side computation and spatial indexing.
