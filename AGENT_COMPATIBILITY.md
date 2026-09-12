# Multi-Agent Compatibility and Deployment

## 1. Canonical architecture

This Skill uses one shared core:

- `SKILL.md`: routing, consultation rules, hard constraints and run flow.
- `references/`: domain boundaries, session modes, evidence gates, question patterns, reporting, consent and regression tests.
- `VERSION.md`, `CHANGELOG.md`, `CAPABILITY_MATRIX.md`: published governance and release evidence. The maintainer also keeps a private observation log that is deliberately not published, because it contains raw consultation scenarios.

Runtime-specific configuration is an adapter only. An adapter may describe invocation, file loading, tool access and persistence limits, but must not rewrite the consultation method.

## 2. Supported runtimes

### Codex

- Canonical maintainer and packaging environment.
- Use the local Skill directory as the editable source.
- Run validation and packaging from Codex after every version update.
- Codex may update files only after a real test, explicit design decision or approved maintenance task.

### ChatGPT

- Use `agents/openai.yaml` for interface metadata and implicit invocation.
- Load `SKILL.md` first and only then load directly relevant references.
- Do not assume local persistence, background work or connector access.

### Hermes

- Mount or copy the same Skill directory.
- Configure Hermes to read `SKILL.md` as the entrypoint.
- Preserve one-question-per-turn, per-turn navigation, closure, scoring and consent rules.
- Any Hermes memory integration is external to this Skill and must never silently store consultation content.

### OpenClaw

- Register `SKILL.md` as the primary instruction source.
- Map OpenClaw-specific tools only to runtime operations; do not add a separate coaching policy.
- If a required reference cannot be loaded, use the conservative branch in `SKILL.md` and mark missing facts as pending confirmation.

### Claude Code and other Agent Skills runtimes

- Place this directory under the runtime's skill directory (`~/.claude/skills/` or a project-level `.claude/skills/` for Claude Code).
- The frontmatter keeps only `name` and `description`, which is the portable Agent Skills minimum.
- Load `references/` on demand. Do not preload every reference file into context.
- Do not write consultation content into long-term memory or project instruction files automatically.
- For any other runtime that follows the same convention, see `agents/generic.md`.

### WorkBuddy

- Register `SKILL.md` as the instruction source and keep the frontmatter `description` as the invocation trigger.
- Map WorkBuddy-native tools to runtime operations only; do not create a second coaching policy.
- Keep any memory, task or reminder integration outside this Skill, and never store consultation content silently.

## 3. Non-negotiable cross-agent invariants

Every runtime must preserve:

1. One core question per consultation.
2. One answer unit per turn.
3. Fact-based acknowledgment before advancing when the user has made a meaningful distinction or correction.
4. A lightweight goal check before every substantive question.
5. No new question unless its answer could materially change the current judgment.
6. Three-stage closure: stage answer and issue separation; hypothesis and user-owned insight; co-created action.
7. Mandatory dual scoring before formal completion.
8. Separate user review and opt-in de-identified case review.
9. Granular consent for case use, quotation, full-record retention and further contact.
10. No psychological diagnosis, crisis treatment, medical/legal/financial judgment or guaranteed outcomes.
11. User-approved de-identified case review before any contact handoff.
12. WeChat contact is user-initiated through `assets/aren-wechat-qr.jpeg`; never expose the phone number as fallback.

## 4. Adapter rules

Adapters may define:

- display name and icon;
- invocation keywords;
- native read-file calls;
- connector availability;
- local or cloud installation paths;
- output rendering conventions.

For the WeChat QR asset, render the image inline when supported. If inline rendering is unavailable, provide it as an image attachment or file card. If neither is possible, state the limitation and do not reveal a phone number. The user must manually scan, add and send the confirmed de-identified review.

Adapters must not change:

- problem-routing logic;
- evidence thresholds;
- question sequence constraints;
- safety and professional boundaries;
- hypothesis verification;
- closure timing;
- scoring and consent.

## 5. Release process

1. Collect a real consultation observation.
2. Distinguish execution deviation from missing rule.
3. Modify the smallest possible shared-core rule.
4. Add or update a regression test.
5. Validate the package.
6. Run the same test scenario in at least two runtimes when possible.
7. Update version, changelog, capability matrix and observation log.
8. Package one complete archive.
9. Deploy the same version to all runtimes; record any adapter-only difference separately.

## 6. Cross-agent acceptance test

A release is not globally ready until each available runtime can demonstrate:

- correct short/long consultation opening;
- stable single-goal focus;
- acknowledgment before questioning;
- no drift after the main issue is answered;
- correct hypothesis verification;
- user-generated action before coach suggestions;
- clarity score and consultation-quality score;
- consent-separated reporting;
- identical stage judgment from the same facts.

## 7. Governance principle

> One coaching method, one evidence base, one version number; multiple thin runtime adapters.

If two agents produce materially different judgments from the same facts, treat that as a regression to investigate, not as acceptable platform personality variation.

## 8. Portable installation summary

| Runtime | Where the directory goes | Entry point | Extra metadata |
|---|---|---|---|
| Codex | `~/.codex/skills/aren-personal-development-positioning/` | `SKILL.md` | `agents/openai.yaml` optional |
| Claude Code | `~/.claude/skills/aren-personal-development-positioning/` or project `.claude/skills/` | `SKILL.md` | none required |
| OpenClaw | OpenClaw AgentSkills directory | `SKILL.md` | none required |
| WorkBuddy | WorkBuddy skill directory | `SKILL.md` | none required |
| Hermes | mounted or copied directory | `SKILL.md` | none required |
| ChatGPT | custom GPT instructions | `SKILL.md` as Instructions | `openai.yaml` optional |

Exact paths follow each platform's own convention. Nothing in this Skill depends on a specific runtime's proprietary capability.
