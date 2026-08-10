# AI Collaboration Workflow — Lugh / Home Assistant

GitHub is the coordination layer for human maintainers, Claude, and OpenAI Codex.
Issues define work, branches isolate changes, pull requests carry implementation
and review, and comments are the hand-off log.

## Roles

### Claude — primary implementer
Claude normally takes an `ai-build` issue, inspects the current repository,
implements on a feature branch, validates where possible, opens or updates a PR,
and leaves a structured hand-off comment.

### Codex — independent reviewer / fixer
Codex normally reviews Claude PRs, compares the implementation with acceptance
criteria, checks for invented Home Assistant entities, invalid YAML, unsafe
automations, security regressions, and unnecessary complexity, and may implement
a focused fix only when explicitly asked.

### Human — owner / merge authority
A human decides whether a change should exist, whether physical-device behavior
is safe, and whether a PR may merge.

## Status protocol

Every agent hand-off ends with exactly one of:

- `STATUS: DONE`
- `STATUS: REVIEW_REQUESTED`
- `STATUS: BLOCKED`
- `STATUS: HUMAN_DECISION_REQUIRED`

## Labels

Recommended:
- `ai-build`
- `ai-review`
- `ai-fix`
- `human-check`
- `ha-dashboard`
- `ha-automation`
- `ha-integration`
- `safe-to-merge`

## Branches

Never develop directly on `main`.

Preferred names:
- Claude: `claude/<issue-number>-<short-description>`
- Codex: `codex/<issue-number>-<short-description>`

Avoid both agents pushing independently to the same branch.

## Home Assistant source-of-truth rules

1. Entity IDs must come from current repository config or a user-provided HA
   entity export. Never invent an entity ID.
2. Preserve known device identifiers unless the issue explicitly changes them.
3. Do not expose secrets, tokens, API keys, passwords, webhook IDs, private URLs,
   or credentials.
4. Do not broaden `trusted_networks`, bypass authentication, expose HA directly
   to the internet, or modify firewall/router access without explicit human approval.
5. Destructive or safety-sensitive controls require human-approved behavior.
6. Do not silently alter heating, EV charging, hot water, presence, alarm,
   camera, lock, or security behavior.
7. Avoid editing `.storage` manually unless explicitly approved.
8. Reuse existing dashboard/theme conventions before adding dependencies.
9. Handle `unknown` and `unavailable` states safely.
10. Phone and kiosk layouts must remain usable at narrow widths.

## Known myenergi orientation

Verify exact IDs in the current branch before use:
- Hub: `kinnegoz`
- Zappi: `20250975`
- Eddi: `23541285`
- Harvi: `1254800`

## Dashboard acceptance checklist

- [ ] YAML structure valid
- [ ] no duplicate YAML keys
- [ ] all referenced entities verified
- [ ] unavailable states handled
- [ ] iPad and phone touch targets usable
- [ ] kiosk mode does not weaken authentication
- [ ] layout is responsive
- [ ] controls reuse existing safe HA services/scripts
- [ ] graphs use entities with valid history/statistics
- [ ] new HACS/frontend dependencies documented
- [ ] existing dashboards still load
- [ ] no secrets added

## Pull request hand-off format

### AI hand-off
**Issue:** #<number>  
**Agent:** Claude | Codex  
**Role:** implementation | review | fix

**Changed**
- ...

**Validated**
- ...

**Not validated**
- ...

**Risks / assumptions**
- ...

**Next agent action**
- ...

`STATUS: REVIEW_REQUESTED`

## Review priorities

- `P0` — dangerous / security / data-loss / physical-device risk
- `P1` — config likely fails or controls the wrong thing
- `P2` — material logic, responsiveness, maintainability, or UX issue
- `P3` — optional polish

A PR with unresolved P0/P1 findings must not be marked `safe-to-merge`.

## Stop conditions

Ask for human input if entity mapping is ambiguous, authentication/networking is
affected, a security device is changed, physical behavior is unclear, safe
validation is impossible, or repo state contradicts the issue.
