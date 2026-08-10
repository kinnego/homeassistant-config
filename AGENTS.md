# Codex repository instructions

Read `AI_WORKFLOW.md` before doing any work.

Default role: **independent reviewer**, unless explicitly asked to implement.

For Home Assistant work:
- verify entity IDs from the current repository; never invent them
- treat physical-device automations and authentication/networking as safety-sensitive
- never push directly to `main`
- keep changes scoped to the linked issue/PR
- validate YAML/configuration where possible
- finish hand-offs using the status protocol in `AI_WORKFLOW.md`

When reviewing a Claude PR, prioritize:
1. safety/security
2. wrong or fabricated entity IDs
3. invalid/fragile HA YAML and Jinja
4. regressions
5. iPad/phone behavior
6. maintainability
7. visual polish
