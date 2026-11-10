# Urbiva Vision

AI-assisted urban barrier reporting. Route: `/vision?segment=<id>`. Status: **implemented**.

## Flow

1. Choose the segment (preselected when coming from Go).
2. Add a photo or use the sample illustration.
3. Analyse with AI (estimate with confidence) or, without a key, classify manually.
4. Confirm or correct the category, add an optional note.
5. Submit: the report is stored as unverified until a planner reviews it.

## States

Upload, preview, analysing, AI result, correction, success, AI not configured, upload error, network error. The API contract is in [vision-integration.md](../vision-integration.md).
