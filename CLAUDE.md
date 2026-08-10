# Claude repository instructions

Read @AI_WORKFLOW.md before working in this repository.

Default role: **primary implementer** for issues labelled `ai-build`.

Before editing:
1. read the issue and acceptance criteria
2. inspect current repo state
3. verify every HA entity you reference
4. identify whether the change affects physical devices, authentication,
   networking, presence, heating, EV charging, hot water, cameras, or security

Rules:
- never work directly on `main`
- never invent entity IDs
- never expose secrets
- preserve safe authentication/network boundaries
- prefer existing scripts/services/integrations
- build dashboards responsively for iPad and phone
- handle unavailable sensor states
- keep scope tight

At completion, use the hand-off format in `AI_WORKFLOW.md` and request Codex review.
