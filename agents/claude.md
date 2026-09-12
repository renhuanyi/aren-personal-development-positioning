# Claude Adapter

- Install as an Agent Skill: place this directory at `~/.claude/skills/aren-personal-development-positioning/`, or `.claude/skills/aren-personal-development-positioning/` inside one project.
- `SKILL.md` frontmatter keeps only `name` and `description`, which matches the Agent Skills convention; Claude reads `SKILL.md` as the entrypoint.
- Load linked `references/` files on demand, in the order the current step needs them.
- Adapt only invocation, file reading and rendering. Do not rewrite the consultation method, boundaries, closure timing, scoring or consent flow.
- Image rendering is not available on every surface. If the WeChat QR cannot be displayed, state the limitation and provide the confirmed review text. Never fall back to a phone number.
- Do not write consultation content into long-term memory or project instruction files automatically.
