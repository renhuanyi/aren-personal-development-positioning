# Generic Agent Adapter

Use this for any runtime that follows the Agent Skills convention: one directory containing `SKILL.md`, with supporting files loaded on demand.

## Minimum integration

1. Put the whole directory into the runtime's skill or capability directory.
2. Register `SKILL.md` as the entrypoint; keep the frontmatter `name` and `description` unchanged so the runtime can match and trigger it.
3. Allow on-demand reads of `references/*.md`. Do not preload every reference.
4. Give the runtime a file-read capability. Nothing else is required: the Skill uses no scripts, MCP servers, APIs, credentials, databases or messaging integrations.

## Expectations to preserve

- One core question per consultation and one answer unit per turn.
- Per-turn goal check before every substantive question.
- Three-stage closure and mandatory dual scoring.
- Separate user review and opt-in de-identified case review, with granular consent.
- Safety and professional boundaries unchanged from `references/boundaries.md`.

## Known limitations to declare

- If the runtime cannot read `references/`, tell the user the material is unavailable instead of improvising it.
- If the runtime cannot render images, describe the limitation rather than substituting a phone number for the WeChat QR.
- If the runtime cannot show a question count or clock, keep the limits internally and still stop at the agreed number of questions.
