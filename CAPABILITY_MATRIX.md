# Capability Matrix

| Surface | Package relationship | Required files | Current evidence | Status |
|---|---|---|---|---|
| Codex | active canonical consumer | `SKILL.md`; `references/`; optional `agents/openai.yaml` | Installed at the user-level path; `quick_validate.py`, audit and catalog discovery pass; Codex CLI 0.133.0 passed v1.4.2 task routing, emergency cash map, correction repair, mandatory safety check and post-safety return regressions | Observation; complete live multi-turn consultation pending |
| ChatGPT | deployment variant | `SKILL.md`; `openai.yaml`; `references/` | v1.4.2-chatgpt.1 package generated from the canonical source; structure, YAML, ten linked references and ZIP integrity pass | Staged package; cloud installation and runtime behavior pending |
| Hermes 0.19.0 | shared-canonical | `SKILL.md`; `references/` | Native frontmatter parser read name/description/body; Skills Guard verdict `safe` with no findings | Structurally verified |
| OpenClaw 2026.4.21 (QClaw bundled runtime) | shared-canonical | `SKILL.md`; `references/` | Native `parseFrontmatterBlock` read exactly `name` and `description`; current official docs confirm AgentSkills layout | Structurally verified |
| Claude Code | shared-canonical | `SKILL.md`; `references/` | Frontmatter keeps only `name` and `description`, matching the portable Agent Skills minimum | Portable layout; runtime install pending |
| WorkBuddy | shared-canonical | `SKILL.md`; `references/` | Same portable layout and adapter contract as the other runtimes | Portable layout; runtime install pending |
| Other Agent Skills-compatible runtimes | shared-canonical | `SKILL.md`; `references/` | Adapter contract documented in `agents/generic.md` | Portable layout; runtime install pending |

The core Skill uses no scripts, MCP servers, APIs, credentials, browsers, databases or messaging integrations. It includes one static contact asset, `assets/aren-wechat-qr.jpeg`, which is shown only after the user confirms a de-identified case review and explicitly chooses to self-send it. The Skill never sends WeChat messages, never adds contacts, and never falls back to exposing a phone number. For career decisions that depend on current occupational or labor-market facts, web access is an optional evidence source rather than a runtime requirement: verify reliable current sources when available, otherwise mark the claim `待核实`. External file writes, messages and persistence are outside the default capability and require explicit user instruction plus runtime support.

Codex installation, discovery and the v1.4.2 focused regression gates are verified. The ChatGPT deployment package is structure-verified but not yet installed in the cloud. Complete live emergency-action, 15-minute and 60-minute multi-turn behavior remains pending. Hermes and OpenClaw installation, discovery and live behavior remain pending.
## Multi-agent shared-canonical operation

- Status: Supported in v1.6.0.
- Runtimes: Codex, Claude Code, OpenClaw, WorkBuddy, ChatGPT, Hermes, and other Agent Skills-compatible runtimes.
- Core guarantee: identical consultation method, boundaries, closure, scoring and consent logic.
- Runtime differences allowed: invocation, tool wiring, file loading and persistence availability only.
- Validation requirement: same scenario should produce materially consistent stage judgment across available runtimes.


## Contact handoff rendering

| Capability | Preferred behavior | Fallback | Prohibited fallback |
|---|---|---|---|
| Inline image supported | Render `assets/aren-wechat-qr.jpeg` after explicit self-send confirmation | None | Showing early |
| File/attachment supported only | Provide QR as image attachment or file card | Explain how to open and scan | Phone number |
| No image output | State that the runtime cannot display the QR; still provide the confirmed copy text | User may save the review for another channel | Phone number or claim of submission |
