# Example issue

**Title:** `[AI] Build futuristic Lugh myenergi kiosk dashboard`

**Labels:** `ai-build`, `ha-dashboard`

## Goal
Create a dedicated Lugh Energy dashboard that works full-screen on an iPad and
remains usable on a phone.

## Acceptance criteria
- Uses current repo entities for Kinnegoz, Zappi, Eddi and Harvi.
- Essential live values are visible without scrolling on iPad.
- Shows generation, home, grid import/export, Zappi and Eddi.
- Includes useful today/history views.
- Uses existing Zappi/Eddi controls only.
- Does not loosen authentication or trusted networks.
- Handles unavailable myenergi values.
- Existing Lugh dashboard still works.
- No new frontend dependency unless justified.

## Agent sequence
Claude implements and opens PR.
Codex reviews against the issue and `AI_WORKFLOW.md`.
Claude resolves P0-P2 findings.
Codex re-reviews.
Human tests on iPad/phone and merges.
