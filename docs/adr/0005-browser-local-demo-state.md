# ADR 0005: Demo state in localStorage

- Status: Accepted
- Date: 2026-11-10

## Context
The demo has no accounts or server storage, but must survive a page refresh.

## Decision
Persist reports, reviews and demo flags in `localStorage` (`urbiva-demo-v1`) with a reset in the demo bar. Photos are never stored.

## Consequences
Private by default and easy to reset; not shared between devices. Real use needs server storage with access control.
