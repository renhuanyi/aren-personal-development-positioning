# WorkBuddy Adapter

- Register `SKILL.md` as the instruction source, following the Agent Skills layout (`SKILL.md` plus optional `references/`).
- Keep `name` and `description` in the frontmatter; WorkBuddy uses the description as the invocation trigger.
- Load only the reference files the current step needs, in the order the flow requires them.
- Map WorkBuddy-native tools to runtime operations only. Do not create a second coaching policy.
- If a reference cannot be loaded, follow the conservative branch in `SKILL.md` and mark the missing fact as `待确认`.
- Preserve one-question-per-turn, per-turn navigation, three-stage closure, dual scoring and granular consent.
- Any memory, task or reminder integration stays outside this Skill and must never silently store consultation content.
