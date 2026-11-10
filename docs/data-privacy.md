# Data and privacy considerations

## Today (implemented)

| Data | Handling |
| --- | --- |
| Photos | Re-encoded in the browser (EXIF and GPS removed), sent once to `/api/vision`, never stored or logged by Urbiva |
| Reports and reviews | Stored only in the user's browser (`localStorage`); no server database, no accounts |
| Location | No device location is used; the origin is fixed in the sample scenario |
| API key | Server-side environment variable only |
| Third-party processing | With a key configured, the photo is sent to the Anthropic API for analysis |

## Before a real pilot (planned)

- Privacy notice and consent text in Azerbaijani, explaining third-party image analysis.
- Blur faces and licence plates before storing any image.
- Server storage with access control, retention limits and deletion on request.
- Data protection review for the pilot city.
- Licensed map data (OpenStreetMap, ODbL attribution).

## Research data (urbiva-ai)

Every dataset source needs a provenance record and a compatible licence before use. See `urbiva-ai/datasets/`.
