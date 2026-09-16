# Study Progress Tracker — Claude Certified Architect (Foundations)

This file is the single source of truth for **(a)** how far along the study plan we are,
**(b)** exactly which upstream commit our material was last synced against, and
**(c)** enough teaching-state context that a brand-new session can pick up
mid-lesson with zero re-explaining.

Update this file after every lesson (even partial ones). Keep it small and factual.

---

## 1. Sync anchor (for pulling upstream updates)

| Field | Value |
|---|---|
| Tracked source file | `guide_en.md` |
| Last synced commit (this fork's `main`) | `8452f67` |
| Commit date | 2026-09-16 (session date; commit itself is from repo history) |
| Commit subject | "Update course access information in README" |

**How to use this when you pull new changes:**

```bash
git fetch origin main
git log 8452f67..origin/main --oneline -- guide_en.md   # what actually changed in the guide
git diff 8452f67..origin/main -- guide_en.md             # the actual content diff
```

If that range shows changes to a chapter/domain you've already completed below, flag it —
we'll do a 5-minute "delta review" of just the changed section instead of redoing the whole
lesson. After reviewing, update the "Last synced commit" row above to the new SHA and date.

---

## 2. Teaching style contract (so any session sounds the same)

- **Small chunks.** One concept (or a tight cluster of 2-3 related subsections) per lesson.
  Never dump a whole chapter at once.
- **Analogy first, jargon second.** Every new mechanism gets a real-world analogy before the
  formal definition.
- **Hands-on every lesson where it makes sense.** A tiny exercise, a JSON schema to write, a
  prompt to design, a bug to spot — something the learner produces, not just reads.
- **Check for understanding** with a quick question or micro-quiz before moving on.
- **Full coverage before wrap-up, no exceptions.** Before declaring any lesson done, re-check
  the source guide section(s) it maps to line-by-line and confirm every subsection/detail was
  actually taught — not just the headline mechanism. Do **not** rely on the learner to catch
  missing pieces (happened in L1: the inline `system` role and its placement rules were
  skipped and the learner had to flag it). If in doubt whether something was covered, re-read
  the guide section before wrapping, and cover the gap before marking `[x]`.
- **No lesson ends without updating this file** (checkbox + date + one-line handover note).

---

## 3. Curriculum & progress

Legend: `[ ]` not started · `[~]` in progress · `[x]` done (with date)

### Module 0 — Orientation
- [x] L0. Exam overview: format, scoring, 5 domains, 8 scenarios — 2026-09-16

### Module 1 — Claude API Fundamentals (Guide Ch.1–2)
- [x] L1. API request structure, message roles, `stop_reason` — 2026-09-16
- [x] L2. System prompt & the context window (lost-in-the-middle, tool-result bloat) — 2026-09-16
- [x] L3. Tools & `tool_use` — what it is, writing good tool descriptions — 2026-09-16
- [ ] L4. `tool_choice` + JSON schemas for structured output
- [ ] L5. Syntax vs semantic errors

### Module 2 — Claude Agent SDK (Guide Ch.3)
- [ ] L6. The agentic loop
- [ ] L7. `AgentDefinition` configuration
- [ ] L8. Hub-and-spoke: coordinator + subagents
- [ ] L9. The `Task` tool for spawning subagents (context-passing pitfalls)
- [ ] L10. Hooks in the Agent SDK

### Module 3 — Model Context Protocol / MCP (Guide Ch.4)
- [ ] L11. What is MCP, what is an MCP server
- [ ] L12. Configuring MCP servers
- [ ] L13. The `isError` flag & MCP resources

### Module 4 — Claude Code Configuration & Workflows (Guide Ch.5)
- [ ] L14. `CLAUDE.md` hierarchy & `@path` imports
- [ ] L15. `.claude/rules/` (path-specific conventions)
- [ ] L16. Custom slash commands & Skills
- [ ] L17. Planning mode vs direct execution
- [ ] L18. `/compact` and `/memory`
- [ ] L19. Claude Code in CI/CD
- [ ] L20. `fork_session` & session management

### Module 5 — Prompt Engineering (Guide Ch.6)
- [ ] L21. Few-shot prompting
- [ ] L22. Explicit criteria vs vague instructions
- [ ] L23. Prompt chaining & the "interview" pattern
- [ ] L24. Validation/retry-with-feedback & self-correction

### Module 6 — Batches & Decomposition (Guide Ch.7–8)
- [ ] L25. Message Batches API (when to use vs sync, `custom_id`, SLA)
- [ ] L26. Task decomposition strategies (fixed pipeline vs dynamic vs multi-pass review)

### Module 7 — Reliability & Escalation (Guide Ch.9–10)
- [ ] L27. Escalation & human-in-the-loop patterns
- [ ] L28. Error handling in multi-agent systems

### Module 8 — Context & Provenance (Guide Ch.11–12)
- [ ] L29. Context management in production systems
- [ ] L30. Preserving provenance & handling conflicting data

### Module 9 — Built-in Tools (Guide Ch.13)
- [ ] L31. Claude Code built-in tools (Read/Write/Edit/Bash/Grep/Glob selection)

### Module 10 — Exam Domain Review & Practice
- [ ] L32. Domain-by-domain cross-reference (map lessons → 5 exam domains, close gaps)
- [ ] L33. Worked exam questions (Q1–12 in guide) with reasoning
- [ ] L34. Practice test part 1 (Q1–15, Multi-Agent Research System scenario)
- [ ] L35. Practice test part 2 (Q16–28+, CI scenario)
- [ ] L36. Final mock exam + weak-spot remediation

---

## 4. Handover state (read this first in any new session)

- **Last completed:** L3 — Tools & `tool_use`, writing good tool descriptions.
- **Next up:** L4 — `tool_choice` + JSON schemas for structured output.
- **Learner notes so far:** Learns fast and reasons well from first principles (correctly
  spotted the `"role": "tool"` bug on the first try, and independently reasoned toward *why*
  no `tool` role exists — landed near "keeps conversation flow intact," which is adjacent to
  the real answer about strict two-party turn alternation enabling prompt caching). Comfortable
  with JSON. Keep hands-on exercises code/JSON-based rather than purely conceptual — that's
  where the engagement is highest. **Also actively catches oversimplifications** — pushed back
  when I said "only two roles" and forgot the inline `system` role/placement rules; don't round
  corners on edge cases for this learner, be precise the first time or expect to be checked.
- **Known weak spots to revisit before the exam:** none identified yet.
- **Process correction (2026-09-16):** L1 was initially wrapped up and marked done *before*
  covering the inline `system` role / placement rules from guide section 1.2 — an omission the
  learner caught, not the teacher. The teaching contract in section 2 now hard-requires a
  line-by-line re-check of the source guide section before any lesson is marked `[x]`. Hold
  every future lesson wrap-up to that bar without being asked.
- **L2 outcome:** learner correctly scoped the system-prompt fix to sensitive actions only
  (Part A, no gaps). On Part B, correctly proposed the *mitigation* (surface the key figure
  prominently) but didn't name the underlying problem ("lost-in-the-middle") explicitly — flag
  this pattern: strong practical/solution instincts, but push for precise terminology recall too,
  since exam questions will hinge on naming the right concept, not just describing a fix. Also
  used this lesson to pre-empt a real gap: closed with the "role/constraints/output format"
  purpose-of-system-prompt line that I'd almost skipped again — the full-coverage re-check
  process from the previous correction is working, keep doing it every time before marking `[x]`.
- **L3 outcome:** learner wrote two mutually-exclusive, bidirectional tool descriptions
  unaided (the anti-confusion technique most people miss). Gap: "what it returns" stayed vague
  (said "summary"/"insights" instead of concrete fields like sentiment label + keyword list),
  and no edge cases were included. Pattern: strong on structural/architectural instincts
  (mutual exclusion, sequencing), needs a nudge toward *concrete specificity* in the "returns"
  and "edge cases" checklist items specifically — call this out explicitly each time those two
  checklist items come up again (JSON schema design in L4 will test this same instinct).
- **Continue by saying:** "Let's pick up at L2" (or just say "continue") and teach it per
  the style contract in section 2 — analogy, then mechanism, then a small hands-on check.

---

## 5. Log

| Date | Lesson(s) | Notes |
|---|---|---|
| 2026-09-16 | L0 | Tracker created. Repo explored: guide_en.md (~2600 lines) is the canonical English study guide with Part I (13 theory chapters), Part II (5 exam domains), worked questions, and a practice test. Plan of 36 bite-sized lessons drafted above. |
| 2026-09-16 | L1 | Taught request structure (stateless "actor with amnesia" analogy), message roles, why `tool_result` lives in a `user` message, and `stop_reason` values. Hands-on: learner found the `"role": "tool"` bug in a broken JSON snippet unaided, then reasoned about *why* Anthropic didn't add a `tool` role (close to correct: landed on "keeps the exchange intact" vs. actual answer of strict two-party alternation enabling prompt caching). **Addendum:** learner caught that I'd oversimplified to "only two roles" — corrected to: three roles exist (`user`/`assistant` converse, `system` is a non-conversational instructional overlay, settable top-level or inline-in-`messages` with placement rules, incl. the rule that `system` can never sit between a `tool_use` and its `tool_result`, else 400 error). Learner then correctly identified which of two message sequences violated that rule, unaided. Pattern so far: catches subtleties the teacher glosses over — don't over-simplify roles/edge-cases for this learner, they'll probe them. |
| 2026-09-16 | Q&A (post-L2) | Learner correctly pushed back on the phrase "have the subagent extract the number to a prominent position" — asked how a subagent could know it lost info it never noticed losing. Clarified: lost-in-the-middle is a *reliability* degradation from open-ended summarization/compression, not literal deletion — all tokens remain in context. Real mitigation is upstream: (1) targeted extraction/tool-forced retrieval instead of free-form summarization, (2) chunking so nothing sits deep in a huge window, *then* (3) place the verified fact prominently in the subagent's own output. Style note: for any probabilistic/attention-based failure mode (lost-in-the-middle and similar), always explain the underlying mechanism (is it deletion or reliability?) before giving the mitigation, or it sounds like magic. Add this to how future lessons on context/attention effects are taught. |
| 2026-09-16 | L2 | Taught system-prompt purpose (role/constraints/output format, priority, loaded once) and the "wording creates unintended tool associations" exam gotcha; then the context window as a fixed-size desk, covering all three named problems (lost-in-the-middle, tool-result accumulation, progressive summarization losing precision). Hands-on: learner rewrote a risky system-prompt line to scope verification to sensitive actions only (clean); on the buried-fact scenario, correctly proposed surfacing the key figure but needed the concept name ("lost-in-the-middle") supplied, and got a nuance correction that you fix your own output's placement, not the fixed source document — this foreshadowed Ch.11's "extract facts into a separate block," flagged as a preview only. |
| 2026-09-16 | L3 | Taught `tool_use` mechanism (restaurant/kitchen-order analogy: Claude requests, your code executes) and the four-part checklist for good tool descriptions (what it returns, input format/examples, edge cases, when-to-use-vs-alternatives), plus the built-in-tools-vs-MCP-tools competition problem. Hands-on: learner rewrote `analyze_content`/`analyze_document` descriptions with strong bidirectional mutual-exclusion framing (unaided); feedback given on making "what it returns" and edge cases concrete rather than vague. |
