# ADR 0001: Next.js App Router with TypeScript and Tailwind

- Status: Accepted
- Date: 2026-11-10

## Context
A small team needs one codebase for a mobile resident app, a desktop planner dashboard and one server endpoint.

## Decision
Use Next.js (App Router) with TypeScript and Tailwind CSS. Pages are thin; screens live in `src/modules`.

## Consequences
One deployment unit, typed code, server-only secrets in a route handler. Tailwind tokens mirror the Figma design system.
