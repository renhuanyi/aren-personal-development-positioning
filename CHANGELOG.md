# Skill Changelog

## 1.9.3 — 2026-09-12

- 将用户可见名称从“阿任个人发展定位教练”更新为“阿任个人发展梳理教练”，使名称更贴合当前第一阶段的实际交付：把混乱表达梳理为阶段性判断与下一步。
- 同步更新 Codex/OpenAI 发现元数据、默认调用提示、复盘标题和相关当前流程文案。
- 保留技术标识 `aren-personal-development-positioning`、既有安装路径、GitHub 地址和旧名称兼容调用，避免已安装用户失效。
- 不改变咨询判断、证据门槛、控场、评分、授权、安全边界或输出流程。

## 1.9.2 — 2026-08-16

- Added an insight-to-action readiness gate: after the user's own stage insight, ask whether it is stable and whether the user wants continued understanding, tool-building, observation or action.
- Added explicit action states: `已共创`, `用户选择延后`, `用户明确拒绝` and `不适用`; only `已共创` enters the normal seven-day experiment flow.
- Added a valid deferred-action closure with an observation point, review time and next-session entry; no forced experiment when the user chooses to observe or declines action.
- Expanded the internal navigation state from six to eight items by adding action state and closure-gate state.
- Added a closure state machine covering goal review, user insight, action state, dual scores, personal report, separate consent, case review and feedback/delivery routing. Omission is not completion.
- Separated user experience scores from process-gate quality notes; the latter is not called an objective score without the formal quality rubric.
- Added regression Cases BB—BE for continued understanding, tool-first requests, deferred action and unprompted closure-gate completion. Existing frozen labels AR, AS and BA were not reused.
- No new theory or case-specific action formula was added. v1.9.1 remains the rollback baseline.
- Lifecycle remains Observation; the new gates have static regression coverage but require renewed live-user validation.

## 1.9.1 — 2026-08-13

- Added mandatory metadata to consultation reviews and de-identified case reviews: case ID, Skill version, version-confirmation method, runtime, consultation mode, evidence level and separately tracked consent states.
- Added a hard rule that historical case versions must be preserved; when a version cannot be confirmed, write `版本待确认` instead of guessing from the current active canonical or a filename.
- Added regression Case AQ from external case `PDP-EXT-001`, covering resignation/income-transition framing, target-versus-experiment separation, one seven-day experiment and version traceability.
- Preserved v1.9.0 consultation judgment, closure behavior, evidence gates and consent flow; this release changes traceability and regression coverage only.
- Lifecycle remains Observation; the external case was supplied as a complete de-identified review without raw transcript or runtime logs.

## 1.9.0 — 2026-08-04

- Added `references/high-quality-case-library.md` with Case 001, a live 9/10 consultation that moved from no clear topic to a concrete market-validation experiment while preserving user agency.
- Added a formal first-use opening for users who request a complete consultation or do not know what to discuss.
- Added explicit behavior for “What can this Skill do / how do I use it?” so users do not need to know how to formulate a coaching problem in advance.
- Hardened the autonomous WeChat handoff: affirmative answers such as “愿意” now trigger immediate QR, send-copy and confirmed-case delivery; no additional summary, thanks, inspiration or confirmation is allowed before delivery.
- Added regression cases AM—AO for formal opening, high-quality long-session flow and affirmative-response QR delivery.
- Codex 接管时恢复 v1.8.1 的问题轮次计数栏与低剩余轮次证据优先级，并移除未通过当前兼容验证的 `api`、`atlas` 产品声明；不改变咨询判断逻辑。
- Kept lifecycle at Observation while establishing the initial consultation case library for continued real-session calibration.

## 1.8.0 — 2026-08-03

- Added first-use speech-to-text guidance: users may speak freely without organizing or editing; Doubao Input Method is preferred and WeChat Input Method is supported.
- Added hard consultation control with time lock, substantive-question lock and state lock.
- Changed navigation checks from descriptive recaps into mandatory stage decisions.
- Added a new-topic parking lot to prevent adjacent issues from extending the current consultation.
- Rebuilt reporting and consent: personal review, granular permissions, actual de-identified case generation, user review and confirmation.
- Replaced phone/WeChat text disclosure with the static asset `assets/aren-wechat-qr.jpeg`.
- Added user-initiated handoff: the user chooses whether to scan the QR and manually send the confirmed de-identified review; no automatic submission or phone-number fallback.
- Added regression cases AH—AL for opening guidance, hard closure, case review approval, QR handoff and no-image fallback.

## 1.7.1 - 2026-08-02

- Fixed a live-session closure bug where the conversation completed dual scoring but skipped the user-facing review and granular consent flow before moving into Skill-version discussion.
- Made the post-scoring sequence a hard gate: personal consultation review, separate consent for de-identified case use, anonymous quotation, raw-record retention and further contact, then conditional contact disclosure or de-identified case handoff.
- Replaced soft wording such as “可询问”, “默认可生成” and “若用户愿意” with mandatory process language while preserving the user's right to decline.
- Added explicit rules that verbal summaries do not replace the personal review, creator self-tests do not waive the flow, and lack of outbound capability must not be represented as successful submission or contact.
- Added regression case AG for post-scoring report-and-consent omission.
- Lifecycle remains Observation.

## 1.7.0 - 2026-08-02

- Added the explicit dual role of coach plus Process Facilitator / 控场教练 (Facilitator).
- Made the coach responsible for session goal, stage, rhythm, cognitive load, topic boundaries and closure; users no longer need to host the consultation themselves.
- Added a hard navigation gate before the fourth consecutive substantive question and immediate triggers for confusion, task-type changes, major new topics and core-problem reframing.
- Added a persistent internal state bar: original problem, current task/stage, confirmed conclusions, single missing evidence, clue classification and closure proximity.
- Required every new clue to be classified as evidence, background, by-product or a new main issue before exploration continues.
- Added energy-aware pacing and autonomous closure.
- Added regression cases AE and AF from a 2026-08-02 live consultation that opened with short-video overuse and drifted across several topics.
- Lifecycle remains Observation pending blind tests where the user does not actively police the process.

## 1.6.0 - 2026-08-01

- Converted the package from Codex agent-exclusive to a shared-canonical multi-agent Skill.
- Declared `SKILL.md` and `references/` as the single coaching source of truth for Codex, ChatGPT, Hermes and OpenClaw.
- Added `AGENT_COMPATIBILITY.md` with adapter boundaries, deployment governance, release process and cross-agent acceptance tests.
- Added thin runtime adapter notes for Codex, Hermes and OpenClaw while retaining `agents/openai.yaml` for OpenAI surfaces.
- Preserved all v1.5.4 consultation behavior, including per-turn navigation, three-stage closure, dual scoring and consent-separated reporting.

## 1.5.4 - 2026-08-01

- Add a user-facing consultation review report after the full consultation close, without making it conditional on case-use consent.
- Add a separate de-identified consultation case review for improving the Skill, focused on the initial problem, actual resolved problem, consultation path, effective moments, process defects and improvement proposals.
- Require separate explicit consent for de-identified case use, anonymous quotation, retention of full raw records and further contact; a generic “yes” authorizes only de-identified case use.
- Show Aren's contact information only after the user explicitly consents to further contact or directly requests it; do not claim that the case has been submitted or that contact has occurred without real platform capability.
- Add `references/consultation-reporting-and-consent.md` and link it from the closing workflow and output template.
- Keep lifecycle at Observation pending live tests of consent wording, report usefulness and privacy boundaries.

## 1.5.3 - 2026-08-01

- Make the two closing scores mandatory rather than optional: problem clarity before/after and consultation quality.
- Separate outcome quality from process quality so a useful conclusion cannot hide a poor consultation experience.
- Require one follow-up on either the most effective element or the single change needed to improve by one point.
- Treat a consultation-quality score below 7 as explicit quality feedback: acknowledge, record, and do not defend or reopen the consultation.
- Add a regression case where clarity rises from 5 to 9 while consultation satisfaction remains 5 because of drift, late closure, incomplete process, and missing scoring.

# v1.5.1 - 2026-08-01

- Raised the default exploration response ceiling from 120 to 200 Chinese characters to make room for fact-based acknowledgment without crowding out the next question.
- Added mandatory `acknowledge-before-advance` and `closure-before-next-question` checks.
- Strengthened closure triggers when the user says the original problem is basically solved, begins proposing action, reports the session is near the agreed duration, or remaining uncertainty requires reality testing.
- Added a rule to park useful side findings as by-products and return directly to the original target.
- Corrected the failure mode where the coach continued evidence gathering after the client had already clarified the priority among several competing work lines.

# Skill Changelog

## 1.5.0 - 2026-07-31

- Add five consultation controllers based on a real consultation test with drift, premature closure, action-dictation and missing-acknowledgment findings:
  1. Navigation check (rule 33): every 3-5 substantive questions or major discovery, check original goal, clarified facts, remaining blanks, whether current question still serves the goal, and whether closure is near; require user consent before switching to a new topic.
  2. Closure signal recognition (rule 34): when the user summarizes, proposes actions, asks "what now," shortens answers, repeats content, or reaches 7+ clarity with remaining gaps being verification rather than cognition, prioritize closure check instead of continued exploration.
  3. Action co-creation (rule 35): default to 2-3 rounds of co-creation before the coach designs an experiment; first the user proposes, then the coach helps concretize, then an executability check. Switch to limited advisor mode only after two failed user attempts, explicit request, unverifiable proposal, or obvious risk.
  4. Awareness acknowledgment (rule 36): when the user independently states a new insight, corrects a judgment, admits a hard fact, separates conflated concepts, corrects the coaching direction, or expresses cost-bearing willingness, pause with one fact-based acknowledgment before continuing.
  5. Dual scoring (rule 37): near closure, ask pre-/post-clarity scores, where the improvement came from, and whether the remaining gap is cognitive or verification; optionally ask session quality score and what would improve it.
- Add session duration expectations (rule 38): opening must state short (~10-20 min, narrow issue) or long (~45-60 min, one core issue with full exploration), with user rights to pause, correct, or end.
- Add four-quadrant sufficiency guidance (rule 39): the quadrants are a sufficiency check tool, not a must-complete checklist; close when the original question is sufficiently answered rather than mechanically completing all quadrants.
- Adjust rule 19 (expression length): add that brevity is not coldness; one fact-based acknowledgment is permitted when warranted, but total length should remain restrained.
- Adjust rule 24 (user's own words): after user completes a stage summary, do awareness acknowledgment first, then decide whether a key fact is still missing or action co-creation should begin.
- Adjust rule 25 (experiment): experiments must first go through user co-creation; if the user only needs judgment, explicitly refuses action design, or real conditions are unsuitable for a 7-day experiment, clearly record the next key fact to verify instead of forcing a template action.
- Restructure the run flow section into 11 numbered steps incorporating navigation, acknowledgment, co-creation and dual scoring.
- Add the session-end navigation template to output-template.md with clarity and quality scoring.
- Add 6 new regression test cases (Y-AD) covering drift, premature explanation, action dictation, user impatience, short consultation, and quality-versus-clarity scoring.
- Expand quality self-check from 22 to 27 items covering navigation, acknowledgment, co-creation, scoring and pre-session expectation setting.
- Expand test scoring from 10 to 12 dimensions and from 17/20 to 21/24 threshold.
- Keep lifecycle at Observation pending full multi-turn regression and real user validation.

## 1.4.3 - 2026-07-31

- Add a mandatory focusing pause when an opening background contains multiple doubts: after enough context to identify the topics and before deep exploration, ask the user which single problem they most want to solve in this session.
- Park all non-selected topics for later instead of cross-exploring them in the current session.
- Treat a user-selected small problem as a valid consultation target; do not replace it with a supposedly deeper or more important issue, and do not promise that solving it will resolve every other concern.
- Add a neutral fallback with two or three user-language candidate topics only when the user cannot choose, without letting the coach decide priority.
- Add a regression case covering income, partnership, family and positioning doubts arriving together.
- Keep lifecycle at Observation pending a live multi-issue conversation and blind regression.

## 1.4.2 - 2026-07-30

- Add a pre-depth task router for understanding, judgment, action, emergency stabilization and crisis requests.
- Allow action and emergency-stabilization requests to receive a low-risk, non-diagnostic path map after one or two decisive clarifications without bypassing evidence gates for deep interpretation or high-stakes decisions.
- Add an answer-first-question-next rhythm so action users receive immediate minimum value instead of repeated extraction.
- Add a hard repair protocol when the user says not to discuss X and asks for Y; the same turn must stop X, acknowledge drift, restate Y, provide Y-related help and ask only one feasibility-changing question.
- Make ambiguous safety checks proportional: one brief check is allowed, but a negative response returns immediately to the original task.
- Add short-term cash boundaries against income guarantees, mathematical pseudo-certainty, deposits, advance-payment scams, loan cycling, usury and illegal work.
- Add an emergency-action output template and five regression cases covering vague cash shortage, seven-day income, rejected negotiation, ambiguous safety language and explicit user correction.
- Incorporate the ten-skill consultation self-assessment and tutorial principles for content/relationship, advisor stance, resource recognition and action readiness into the existing quality standard without adding a new theory module.

## 1.4.1 - 2026-07-30

- Add a six-part hard gate before any “the real problem is not X but Y” reframing: complete recent event, one attempt-result chain, trigger/pattern/structure distinction, decision stage, high-stakes responsibility/resource facts and user-confirmed fact map.
- Limit pre-sufficiency exploration turns to one or two brief reflections plus one question and at most 120 Chinese characters; prohibit long analysis, advice, red/blue-team framing, multi-year paths and multi-option plans unless the user requests a stage summary.
- Require high-debt and collection scenarios to check mandatory 7—30 day financial or legal risks before psychological or identity explanations, while preserving career coaching and professional-boundary referral.
- Require concrete events to include the demand made, user action, outcome and current state; require one key attempt to include action, expected change, actual result, interpretation, unresolved issue and continuation/adjustment/stop reason.
- Separate preference-testing hypotheticals from real opportunities and market evidence; a hypothetical high salary cannot become a plan without current job-search action and feedback.
- Keep work-plus-startup as a conditional candidate until time, energy, contract, partnership, industry, family, execution and organizational-consent constraints are checked.
- Require the user to state how the problem changed before AI summary, and close with exactly one seven-day experiment containing one hypothesis, action, observable result, decision rule and review time.
- Add a high-debt entrepreneurship-versus-employment regression case based on a real user test.
- Keep lifecycle at Observation pending independent regression and renewed live multi-turn evidence.

## 1.4.0 - 2026-07-30

- Add an explicit chaotic-input entry that helps users begin without first organizing a complete narrative.
- Require each decisive prior attempt to be traced through action, observable result, user interpretation, subsequent choice and remaining problem.
- Define the 15-minute micro-consultation deliverable as an initial map, provisional hypothesis and one validation action; prohibit root-cause claims.
- Define the approximately 60-minute long-consultation deliverable as a working conclusion and testable plan for one relatively focused issue; route complex problems to multiple sessions.
- Require current reliable occupational or labor-market evidence when a career recommendation depends on external facts, otherwise mark it `待核实`.
- Add explicit AI limitation disclosure and complexity-based recommendations for Aren's formal one-to-one consultation without outcome promises, pressure or fabricated booking details.
- Add four regression cases covering chaotic input, action-without-effect evidence, unrealistic one-hour expectations and career-market verification.
- Constrain time-boundary explanations to one or two sentences and prohibit interpreting a user's wish for a root cause before evidence is collected.
- Remove the unsupported `api` product value from `agents/openai.yaml` after Codex 0.133.0 rejected the interface metadata.
- Keep lifecycle at Observation pending independent behavior tests and real multi-turn consultation evidence.

## 1.3.0 - 2026-07-30

- Add separate micro-consultation and long-consultation depth modes; keep consultation depth independent from coaching versus limited-advisor intervention style.
- Add an optional privacy-minimized pre-consultation intake for long-form work.
- Require long consultation to complete the four-quadrant map with recent trigger, historical pattern, counterexample and success evidence; require micro-consultation to focus on one issue and decision-critical variables.
- Add boundaries for consultant self-disclosure and experience sharing so they remain brief, relevant and user-centered.
- Adopt the three-stage and thirteen-action quality skeleton from the career-consultation process self-check: opening and contracting; exploration, hypothesis, insight, consensus, decision and action; intentional closing and evaluation.
- Add explicit user-insight, stage-consensus, temporary-decision and closing-evaluation gates.
- Add long-consultation and micro-consultation test cases and expand scoring to include consultation-process completeness.
- Keep lifecycle at Observation pending Aren's additional good-consultation criteria and renewed real-case validation.

## 1.2.0 - 2026-07-30

- Add expression-support rules that use brief reflection, smaller questions, permission for incomplete answers and user-language mirroring to encourage fuller disclosure without creating interrogation pressure.
- Replace the single-story transition with an exploration-sufficiency gate covering trigger versus pattern, structural facts, repair attempts, stakes and decision stage.
- Require a map recap and user correction before candidate explanations.
- Treat “so what” and similar responses as relevance or task-shift signals rather than automatic inability to organize.
- Reframe coaching from decision discovery to cost, boundary, responsibility or execution design when the user has already made the decision.
- Add sparse multi-turn, low-disclosure and already-decided test cases; expand scoring to include exploration sufficiency, expression support and reframing accuracy.
- Keep lifecycle at Observation pending renewed real-case validation.

## 1.1.0 - 2026-07-30

- Preserve the v1.0 coaching framework, references and OpenAI interface metadata.
- Define one shared canonical package for Codex, Hermes and OpenClaw.
- Remove implicit dependence on platform-specific tool names, absolute paths, networking, memory and file persistence.
- Require explicit user authorization and real runtime support before external writes, messaging or persistence claims.
- Add conservative fallback behavior when bundled references cannot be read.
- Clarify that platform safety policy governs crisis handling.
- Prevent direct-answer pressure from bypassing the concrete-story evidence gate.
- Install the validated package as the Codex user-level canonical copy and enter Observation; no coaching behavior changed during installation.

## 1.0.0 - 2026-07-30

- Import the user-provided multi-file Skill as the source baseline.
