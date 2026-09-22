# Workflow — Verification (phases 8–10)

Covers: Render → Compare → Verify. Then produce the report.

---

## §1 — Render

Rebuild and run the project using whatever the environment actually provides.

| Available | Do |
|---|---|
| Browser automation | Screenshot the same pages/states as the audit, at the same widths |
| Dev server only | Load pages, check console for errors, verify the build |
| Build only | Confirm the build succeeds and tests pass |
| Nothing | State it plainly; verification is static only |

> **Never claim to have rendered or screenshotted anything you did not.** If you could
> not render, the report must say so and mark the visual checks `not-verified`.

---

## §2 — Compare

If before/after screenshots exist, compare them directly. Otherwise reason over the
diff and state that limitation.

### Comparison questions

- Is the **hierarchy** stronger? Blur the before and after — does the most important
  element now emerge?
- Is the **identity** stronger? Re-run the Brother Test with the logo masked.
- Are repeated patterns now **justified**, or merely different?
- **Did we accidentally replace one AI cliché with another?** (`identity-03`)
- Does it look like *this product*, or like the current fashionable template?
- Is anything decorative that carries no meaning?

Re-running the Brother Test is the single most valuable check here. If the interface is
still interchangeable with a CRM, a fintech and a dev tool, the P0 was not resolved —
and restyling components did not fix it.

---

## §3 — Verify

Run the full checklist. Anything unverifiable is reported as unverified, not assumed.

```text
Does the new design have stronger hierarchy?
Does it have stronger identity?
Are repeated patterns still justified?
Did we accidentally replace one AI cliché with another?
Are existing brand elements preserved?
Are components internally consistent?
Is responsive behavior intact?
Are focus/error/empty states preserved?
Is reduced motion respected?
Did we introduce unnecessary dependencies?
Did we break functionality?
```

### Concrete checks

**Responsive** — mobile · tablet · desktop · wide. No horizontal overflow, navigation
works, measure comfortable, CTAs intact.

**Accessibility** — contrast measured in every theme; visible focus at every keyboard
stop; full keyboard traversal; no hover-only information; empty/error/loading/disabled
states still present.

**Interaction** — hover, focus, active, disabled on every interactive element;
forms still submit; nothing became unreachable.

**Motion** — `prefers-reduced-motion` honoured; no animation implies data that does not
exist; only `transform`/`opacity` on the main path; no jank.

**Technical** — build succeeds; tests pass; no new dependencies; no console errors;
lint/type checks clean; diff contains no unrelated churn.

### Regression guard

Confirm explicitly that you did **not**:

- modify a cleared false positive
- remove a brand element
- break a component state
- introduce a dependency
- reformat unrelated files
- change framework, styling system or component library

---

## §4 — Report

**This is the normative report skeleton.** `SKILL.md` §22 summarises it.

```text
PROJECT CONTEXT
  stack · styling system · design system · brand assets found

EVIDENCE LEVEL
  [ ] source only  [ ] static + rendered  [ ] browser + screenshots
  Scope audited: ...        Not audited: ...
  (If nothing could be rendered:
   "Visual evidence unavailable. Assessment limited to static/source analysis.")

OBSERVATIONS
  - signal / evidence / confidence / category
    false-positive check / diagnosis / disposition

  Signal concentration: N confirmed
  (diagnostic heuristic only — never a claim about how the design was produced)

ART DIRECTION
  existing strengths · design hypothesis · principles · proposed changes
  explicitly rejected alternatives

IMPLEMENTATION
  files · components · tokens · assets · motion      (each with its design reason)

VERIFICATION
  desktop / tablet / mobile · accessibility · responsive
  build / typecheck / lint · baseline · rollback point

INTENTIONAL PRESERVATIONS
  what was deliberately NOT changed, and why        ← mandatory, must not be empty

REMAINING SIGNALS
  which signals remain and why they are justified

STOP CONDITION
  why further modification is or is not justified
```

### No aesthetic score

Never emit `AI Slop Score: 23/100`, a letter grade, or a percentage. Aesthetic quality
is not quantifiable and a number invites optimising against the metric. The five
questions in `SKILL.md` §13 are the deliverable.

### Report rules

- **Never give a bare score.** Explain decisions.
- **Never state or imply the design was AI-generated.** Report patterns and the absence
  of intentional decisions; origin is not knowable.
- The "False positives" section is not optional — it is evidence the skill exercised
  judgement rather than pattern-matching.
- List uncertain signals as open questions rather than silently acting on them.

---

## §5 — Sufficiency check (phase 14)

The skill stops at **sufficiency**, not perfection. After each
implement → render → verify cycle, answer:

```text
Is the design now coherent?
Is the hierarchy clear?
Is the product identity stronger?
Are the remaining signals justified?
```

**All yes → STOP.** Write the STOP CONDITION section and finish.

Do not run another cycle merely because more rules could still fire. Remaining P2s are
a legitimate outcome; so is "the rest is churn". Endless optimisation is a failure mode,
and each additional cycle adds regression risk for diminishing visual return.

Continue only if a **P0 or P1 remains materially unresolved** and the fix is within the
approved scope. Anything outside that scope goes to the report as an open question, not
into the diff.

---

## Failure conditions

The remediation **failed**, regardless of how it looks, if:

- the output resembles the current fashionable template (`identity-03`)
- an intentional choice was "corrected"
- a brand element was replaced
- a dependency was added for aesthetics
- functionality broke
- accessibility regressed
- the diff is far larger than the problems warranted

In any of these cases, revert and state what happened.
