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
- **No lesson ends without updating this file** (checkbox + date + one-line handover note).

---

## 3. Curriculum & progress

Legend: `[ ]` not started · `[~]` in progress · `[x]` done (with date)

### Module 0 — Orientation
- [x] L0. Exam overview: format, scoring, 5 domains, 8 scenarios — 2026-09-16

### Module 1 — Claude API Fundamentals (Guide Ch.1–2)
- [ ] L1. API request structure, message roles, `stop_reason`
- [ ] L2. System prompt & the context window (lost-in-the-middle, tool-result bloat)
- [ ] L3. Tools & `tool_use` — what it is, writing good tool descriptions
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

- **Last completed:** L0 — Orientation (exam format, domains, scenarios).
- **Next up:** L1 — API request structure, message roles, `stop_reason`.
- **Learner notes so far:** none yet — first real lesson hasn't happened.
- **Known weak spots to revisit before the exam:** none identified yet.
- **Continue by saying:** "Let's pick up at L1" (or just say "continue") and teaching it per
  the style contract in section 2 — analogy, then mechanism, then a small hands-on check.

---

## 5. Log

| Date | Lesson(s) | Notes |
|---|---|---|
| 2026-09-16 | L0 | Tracker created. Repo explored: guide_en.md (~2600 lines) is the canonical English study guide with Part I (13 theory chapters), Part II (5 exam domains), worked questions, and a practice test. Plan of 36 bite-sized lessons drafted above. |
