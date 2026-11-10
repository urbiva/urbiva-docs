# Vision integration specification

Status: **implemented**. Sources: `src/lib/vision/client.ts`, `src/lib/vision/handler.ts`, `src/lib/vision/analyze.ts`, `src/app/api/vision/route.ts`.

## Browser

- Accepts JPEG, PNG, WebP or HEIC up to 15 MB.
- Re-encodes to JPEG with the long side at most 1280 px. This strips EXIF and GPS metadata.
- Sends base64 data with a media type to the server.

## `POST /api/vision`

Runtime: Node.js, dynamic.

| Check | Rule |
| --- | --- |
| Method | `POST` only (405 otherwise) |
| Rate limit | 10 requests per minute per client (429) |
| Media type | `image/jpeg`, `image/png`, `image/webp` (415) |
| Size | at most 5 MB decoded (413) |
| Content | base64 alphabet and magic bytes must match the media type (400 or 415) |

### Responses

| Status | Body | UI |
| --- | --- | --- |
| 200 | `{ status: "ok", result: { category, confidence, rationale, requiresHumanReview: true }, model }` | AI estimate, person confirms or corrects |
| 503 | `{ status: "not_configured", message }` | "AI is not configured", manual classification |
| 4xx or 502 | `{ status: "error", message }` | Error notice, retry or manual classification |

Categories: `stairs`, `blocked_path`, `broken_surface`, `curb`, `obstruction`, `other`, `none`. Confidence: `low`, `medium`, `high`.

## Configuration

| Variable | Notes |
| --- | --- |
| `ANTHROPIC_API_KEY` | Server only. Missing key gives the `not_configured` path. |
| `URBIVA_VISION_MODEL` | Optional, default `claude-sonnet-5-5`. |

## Guarantees

- The key never reaches the browser.
- Images are not stored or logged.
- Provider errors are mapped to safe messages.
- A person always confirms before an estimate becomes a report.

## Planned

Replace the external model with UVA-Net S10 served locally, behind the same request and response contract (research, see `urbiva-ai`).
