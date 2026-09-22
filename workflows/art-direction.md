# Workflow — Art direction (phase 5)

**Mandatory gate. No broad modification may begin before this is written down.**

Remediating without a direction is how a skill replaces one default with another. The
direction is the thing that makes every later change answerable to something.

---

## §1 — First: does a direction already exist?

Search before proposing anything:

- `DESIGN.md`, style guide, brand guidelines, Figma/brand links in the README
- an existing token layer with **named**, semantic tokens
- a consistent recurring motif across existing screens
- marketing site, app store listing, pitch deck, existing print or social assets
- git history showing deliberate design iteration

**If a direction exists → preserve and reinforce it.** Your job becomes consistency:
apply the existing direction where it was not applied. Do not replace it.

This is the most common correct outcome on real projects with brands.

---

## §2 — The ten questions

Answer all of them in writing. They go into the final report.

```text
What is the product?
Who is it for?
What should the interface feel like?
What should differentiate it visually?
What visual motif belongs specifically to this product?
What typography hierarchy makes sense?
What color system makes sense?
What level of density is appropriate?
What should motion communicate?
What should NOT be introduced?
```

The last question is as important as the others. It is the guardrail that stops the
remediation drifting into decoration, and it must be explicit.

---

## §3 — Name the direction

A direction must be **nameable**. Examples of real directions:

```text
editorial          utilitarian-dense    technical-mono
warm-consumer      industrial           archival/documentary
clinical-precise   playful-geometric    brutalist-functional
```

> **"Clean and modern" is not a direction — it is the slop default.**

The direction must derive from: product · audience · content · brand · context · what
already exists. Not from what currently reads as tasteful.

---

## §4 — Lock the decisions

Express in the abstraction layer, then map to the stack (`references/remediation.md`):

```text
PRIMARY_COLOR / SECONDARY_COLOR / ACCENT_COLOR   + the rule for when the accent is used
SURFACE levels                                    page / section / surface / interactive / control
TEXT_PRIMARY / TEXT_SECONDARY / BORDER
DISPLAY_FONT / BODY_FONT                          may be the same family; roles must differ
RADIUS scale                                      with a role per surface level
SHADOW scale                                      with a role per surface level
SPACING scale                                     and what each step groups
MOTION                                            what it communicates, and where it is absent
MOTIF                                             the one element that belongs to this product
```

### Constraints

- **Cap active hues** at roughly three plus a neutral ramp.
- **One motif is enough.** Several at once is noise, not identity.
- Every token gets a **role**, not just a value. A value without a role is a default.
- Decide where motion is **absent** — that is a decision too.

---

## §5 — Write the "do not introduce" list

Explicit, project-specific, and binding on the remediation phase. Typically:

```text
Do not introduce:
- grain, blobs, tilts, mascots, custom cursors, parallax
- a second motif
- decorative illustration unrelated to the product
- any new dependency
- the cream / editorial-serif / sage template  (identity-03)
- animation that does not communicate state
- a replacement for [existing brand element X]  ← name the real ones
```

---

## §6 — Self-check before proceeding

- [ ] Does this direction come from the product, or from a trend?
- [ ] Would this direction suit a competitor equally well? (If yes, it is not a direction.)
- [ ] Have I preserved every existing brand element?
- [ ] Am I about to produce the 2026 tasteful default? (`identity-03`)
- [ ] Is the motif one element, applied with restraint?
- [ ] Have I written what must **not** be introduced?
- [ ] Can every planned change be justified against this direction?

If the honest answer to the second question is "yes, a competitor could use this
identically" — the direction is not finished. Return to §2.

---

## §7 — When identity is deliberately neutral

Some products must stay neutral: internal tools on a corporate system, white-label
products, platform extensions, government services. Here `identity-01` is a **cleared
false positive**, not a failure.

The direction becomes: *"neutral by requirement — improve hierarchy, consistency and
accessibility; do not add identity."* That is a legitimate and complete outcome.

---

---

## §8 — Present and wait (approval gate)

**This is the end of the read-only half of the skill.** Present before editing:

```text
## Audit summary
N confirmed signals (P0: x, P1: y, P2: z) — top 5 listed with evidence
M cleared as intentional — with the justification found for each
Sampled: <what you actually looked at>   Not assessed: <what you could not>

## Proposed art direction
Direction: <name>   (existing, preserved | newly proposed)
Motif · type hierarchy · colour system · density · motion intent
Do not introduce: ...

## Planned changes
~N files, scoped to: <token layer / shared components / N pages>
Highest-impact first: ...
Left alone: <cleared FPs, and P2s judged not worth the churn>

Proceed? Adjust the direction? Narrow the scope?
```

Then **stop**. Do not start editing in the same turn.

### Why this gate exists

The direction is pure judgement and everything downstream inherits it. A wrong
direction discovered after forty files is far more expensive than one question. It is
also the user's last chance to say "actually purple *is* our brand" before the skill
acts on a misread.

### Proceeding without asking

Only two cases:

- the user explicitly said to go ahead without check-ins
- the only changes are **broken-function fixes** — mobile overflow, missing focus
  states, leftover placeholders, dead links. Completion, not taste. Fix and report.

### If the user adjusts

Rewrite the direction and re-present. Do not carry forward the parts they rejected.

---

## Exit criteria

- [ ] Existing direction found and preserved, **or** a new one proposed with justification
- [ ] All ten questions answered in writing
- [ ] Direction has a name that is not "clean and modern"
- [ ] Tokens and roles defined in the abstraction layer
- [ ] One motif identified
- [ ] "Do not introduce" list written
- [ ] **Presented to the user and approved** (or an exception above applies)
- [ ] Still zero files modified

→ Proceed to `workflows/remediation.md`.
