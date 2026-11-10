# Urbiva Go

Accessible route navigation for residents. Route: `/go`. Status: **implemented** on **sample data**.

## Flow

1. Choose a mobility profile: Piyada, Əlil arabası, Uşaq arabası.
2. Choose a destination (five sample destinations; the origin is fixed to the residential area).
3. Compare the suitable route with the shortest route. Badges explain trust: all segments verified, unverified barrier, unknown data.
4. Open route details: each segment with its passability state; unknown or uncertain segments link to Vision.

## States

- No accessible route for the profile: danger notice with options to change the destination or report a barrier.
- Unverified segment warning after a report.

## Not implemented

Turn-by-turn navigation (designed in Figma only). The app tells users not to use sample routes for real navigation.
