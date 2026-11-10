# ADR 0003: AI output is an estimate until a person confirms it

- Status: Accepted
- Date: 2026-11-10

## Context
A false barrier sends people on longer routes; a missed barrier puts them in front of stairs.

## Decision
Vision results are labelled as estimates and become reports only after human confirmation. Planner review sets the final verification state. Without an API key the app offers manual classification instead of inventing a result.

## Consequences
Slower than full automation, but trustworthy. The same rule applies to the planned local model.
