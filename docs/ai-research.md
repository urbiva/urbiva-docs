# AI research: UVA-Net S10

Status: **implemented in code, not trained**. Source: `urbiva-ai`.

## Goal

Replace the external vision provider behind `POST /api/vision` with a small local model, without changing the app. The model suggests a barrier category; a person always confirms.

## Model

| Property | Value |
| --- | --- |
| Architecture | Inverted residual CNN with depthwise convolutions, squeeze-and-excitation and hard-swish |
| Parameters | 3,963,191 at width 1.0; hard limit 10,000,000 enforced in code |
| Input | 320 x 320 RGB, letterboxed, metadata removed |
| Output | Probabilities over `stairs`, `blocked_path`, `broken_surface`, `curb`, `obstruction`, `other`, `none` |
| Decision rule | Barrier threshold set on validation data for a target false-positive rate (default 5 %) |

## Contract with the app

The local server accepts the same body as the app (`imageBase64`, `mediaType`, JPEG/PNG/WebP up to 5 MB) and returns the same response:

```json
{ "status": "ok", "model": "uva-net-s10:<experiment>",
  "result": { "category": "stairs", "confidence": "high", "rationale": "...", "requiresHumanReview": true } }
```

Without a model it answers `503 {"status": "not_configured"}`, which the app already handles with manual classification.

## Data rules

- Every image is listed in a manifest and linked to a registered source with a licence that permits commercial use.
- Records must confirm that faces and licence plates are blurred.
- Splits are assigned by location group to prevent leakage.

## What does not exist yet

Datasets, trained weights, measured accuracy, latency measurements. None of these may be reported until produced by a committed configuration on a recorded dataset version.
