---
name: ai-slop-killer
description: >
  Audits an existing frontend for arbitrary, generic, repetitive or interchangeable
  visual choices ("AI slop"), then rebuilds an intentional, coherent art direction
  using the technologies the project already uses. Stack-agnostic. Use when asked to
  remove AI slop, make a UI less generic / more distinctive / more premium, review an
  AI-generated frontend, run a design audit, or refactor an interface visually.
version: 1.0.0
license: MIT
---

# ai-slop-killer

## 0. What this skill is actually for

This skill does **not** exist to make a site "stop looking AI-generated". That framing
leads to mechanically swapping one default for another and produces a new cliché.

The real objective:

> **Identify visual choices that appear arbitrary, generic, repetitive or interchangeable,
> then rebuild an intentional and coherent visual direction — without needlessly changing
> the project's technology.**

You improve: identity, hierarchy, typography, composition, palette, components,
spacing, imagery, motion, accessibility, and design-system consistency.

You never conclude "this was made by AI". You report **suspicious patterns**, never origin.

---

## 1. The core rule — read before anything else

```text
Do not replace AI slop with another form of AI slop.

Do not automatically replace:
- purple with beige
- sans-serif with serif
- cards with bento grids
- gradients with grain
- rounded corners with sharp corners
- Lucide icons with another trendy icon set

A visual choice is not bad because it is popular.

A visual choice becomes suspicious when it is:
- arbitrary
- repetitive
- unjustified
- interchangeable
- disconnected from the product
- applied uniformly without hierarchy
- used because it is a default rather than a deliberate decision
```

The 2026 "tasteful default" (cream background + editorial serif + sage green + grain)
is itself catalogued as tell `identity-03`. Swapping into it resets the clock.

### The axioms

```text
Detect ≠ Fix
Generic ≠ Bad
Repetition ≠ Bad
Popular ≠ Bad
Unusual ≠ Good
Unique ≠ Good
AI-generated ≠ Automatically Bad
Human-made ≠ Automatically Good

Intentionality > novelty.
Coherence    > decoration.
Context      > heuristics.
Evidence     > assumptions.
Design decisions > style recipes.
```

> **AI Slop Killer does not fight AI aesthetics. It fights unintentional design.**

---

## 2. Detect ≠ Fix — the reasoning chain

**A detected signal never by itself authorises a modification.**

The rule catalogue is a **system of observation and diagnosis**, not a list of things
to delete. Never reason:

```text
tell detected → element is bad → remove it        ❌
```

Always reason:

```text
signal detected
  → observation        what is literally there
  → diagnosis          what problem, if any, it actually causes
  → context validation brand, design system, product, history
  → false positive?    → CLEARED, stop here
  → disposition        KEEP / STRENGTHEN / MODIFY / REMOVE
  → design decision    what we do and why
  → implementation     natively in this project's stack
  → verification       did it work, did we break anything
```

### Worked example — the same signal, four possible endings

```text
Signal: Inter used everywhere.

❌ → replace Inter.

✓  → examine the typographic hierarchy
   → is Inter coherent with the brand?
   → is it genuinely causing a problem?
   → KEEP (brand face, hierarchy strong) | STRENGTHEN (scale too timid)
   | MODIFY (keep face, build the scale) | rarely REMOVE (with a content reason)
```

The same discipline applies without exception to: purple · gradients · rounded cards ·
bento · glassmorphism · Lucide · Tailwind · dark mode · serif · asymmetry · animation ·
spacing · borders. **None of these is bad in itself.**

---

## 3. The disposition layer

After false-positive validation, every **CONFIRMED** observation receives exactly one
disposition. This is the mechanism that stops detection collapsing into deletion.

| Disposition | When | Action |
|---|---|---|
| **KEEP** | The choice is intentional, coherent and sufficiently justified | Change nothing. Record it as a preservation. |
| **STRENGTHEN** | The choice is right but its expression is weak or under-exploited | Improve the existing choice. Do not replace it. |
| **MODIFY** | The principle is sound but its current form causes a problem | Change the form, keep the principle. |
| **REMOVE** | No sufficient justification; creates incoherence; a plainly generic artefact | Remove it. |

### STRENGTHEN — the disposition that is usually missing

Most real projects need this one more than REMOVE:
*good brand colour poorly distributed · good typeface with weak hierarchy · good motif
used timidly · good photography inconsistently treated.*
**Improve the existing choice; do not substitute a new one.**

### MODIFY — change the form, keep the principle

*Five sections share one card treatment → the repetition is fine, the identical visual
weight is not.* Keep the card language, introduce hierarchy through surface treatment,
scale, spacing and density. Not: "remove the cards, use sharp corners."

### REMOVE — only genuinely unjustifiable artefacts

Decorative gradient with no function · fake status pulse · fake caret · generic stock
imagery · decoration unrelated to the product.

Selection procedure and a full worked example: `workflows/audit.md` §6 (operational).

### Distribution sanity check

A remediation plan where nearly everything is REMOVE has almost certainly skipped the
diagnosis step. Expect a healthy mix, and expect KEEP to be common on real projects.

---

## 4. Repetition doctrine

```text
Repetition is not the problem.
Unjustified repetition is the problem.
```

A design system is **necessarily** repetitive. That is what makes it a system.
Repetition only becomes a signal when it combines with other factors:

```text
repetition
+ lack of hierarchy
+ lack of semantic reason
+ lack of meaningful variation
```

The skill must distinguish two different things:

| **Design-system repetition** — legitimate | **Compositional monotony** — a signal |
|---|---|
| same radius across components | every section has the same composition |
| same spacing scale | every card has the same visual weight |
| same button style | every element has the same density |
| same treatment for cards of one family | every section has the same rhythm |
| same typographic system | nothing signals what matters most |

The left column is consistency and should be **KEEP** or **STRENGTHEN**.
The right column is absence of hierarchy and is usually **MODIFY** — rarely REMOVE.

Before flagging repetition, ask: *is this one system applied consistently, or one
composition applied thoughtlessly?*

---

## 5. Uniqueness ≠ Quality

An unusual interface is not automatically a better interface. **Novelty must be a
consequence of a justified design decision, never an objective in itself.**

Explicitly forbidden "corrections":

```text
adding asymmetry only to be different
adding unusual typography only to be different
adding a strange shape only to be different
adding motion only to give "personality"
adding unexpected colours only to avoid looking generic
```

If the only justification for a change is *"this would be more distinctive"*, the
change is not justified. Find the design reason or drop it.

Conversely: a project using very common conventions but possessing a coherent,
specific identity is **fine**. Do not manufacture uniqueness.

---

## 6. When to use

Trigger when the user asks to:

- remove AI slop / "de-slop" a UI
- make an interface more distinctive, less generic, more premium, more intentional
- improve a design that was generated by AI
- improve or establish art direction
- review a frontend that "looks generated"
- run a design audit
- visually refactor an interface

## 7. When NOT to use

Do **not** trigger merely because the project uses:

Tailwind · React · Next.js · shadcn/ui · Lucide · Inter · rounded corners ·
dark mode · purple · gradients · glassmorphism · bento grids · Framer Motion.

Every one of these can be entirely legitimate. Stack is never evidence.

---

## 8. Progressive loading — read this before opening any other file

This skill is larger than any one task needs. **Never load it all.**

```text
ALWAYS:        SKILL.md + rules/index.md              (~4.5k tokens)
PER CATEGORY:  the matching block of rules/tells.yaml (~250 tokens each)
WHEN FIXING:   references/<category>.md               (~800 tokens each)
PER PHASE:     the one workflow file you are in       (~1.3k tokens each)
```

`rules/index.md` is the complete 54-rule catalogue compressed to a triage table.
It is enough to decide **which** rules plausibly fire. Only then pull the full rule.

Extract one rule without reading the whole YAML:

```bash
awk '/^  - id: comp-01$/,/^  - id: /' rules/tells.yaml | head -n -1
```

Loading `rules/tells.yaml` in full (~13.5k tokens) is a mistake in all but the rarest
whole-codebase audits.

---

## 9. Mandatory phase order

Never skip ahead. Each phase gates the next.

```text
 1. STATIC AUDIT      → workflows/audit.md §1–2   inspect stack, collect signals
 2. RUN APPLICATION   → workflows/audit.md §3     if the environment allows it
 3. VISUAL AUDIT      → workflows/audit.md §3     observe the actual rendering
 4. CROSS-CHECK       → workflows/audit.md §3b    reconcile source vs rendering
 5. CLASSIFY          → workflows/audit.md §4     P0/P1/P2, cluster
 6. VALIDATE FPs      → workflows/audit.md §5     CLEARED / CONFIRMED / UNCERTAIN
 7. DISPOSITION       → workflows/audit.md §6     KEEP/STRENGTHEN/MODIFY/REMOVE
 8. ART DIRECTION     → workflows/art-direction.md
──────────────── ⛔ STOP. PRESENT TO USER. WAIT FOR APPROVAL. ────────────────
 9. PRIORITIZE        → workflows/remediation.md §1
10. IMPLEMENT         → workflows/remediation.md §2
11. RENDER            → workflows/verification.md §1
12. BEFORE / AFTER    → workflows/verification.md §2
13. VERIFY            → workflows/verification.md §3
14. SUFFICIENCY       → workflows/verification.md §5   stop, or one more cycle
```

**You may not edit a single style before phases 1–8 are complete AND approved.**

Steps 2–4 are **first-order, not optional extras**. When a rendering can be obtained,
skipping it is a defect in the audit, not a shortcut — see §12.

### STOP EARLY

Do not keep modifying simply because more rules could still fire. After each
implement → render → verify cycle, answer:

```text
Is the design now coherent?
Is the hierarchy clear?
Is the product identity stronger?
Are the remaining signals justified?
```

If yes → **STOP**. Report what remains and why it is intentionally left.
Endless optimisation is itself a failure mode.

### The approval gate (between phase 5 and 6)

Art direction is pure judgement. If the direction is wrong, everything downstream is
wrong — and the user finds out after forty files changed. So stop and present:

```text
## Audit summary
N confirmed signals (P0: x, P1: y, P2: z) — top 5 listed
M signals cleared as intentional — with justifications

## Proposed art direction
Direction: <name>   (existing, preserved | newly proposed)
Motif · type hierarchy · colour system · density · motion intent
Do not introduce: ...

## Planned changes
~N files, scoped to: <token layer / components / pages>
Highest-impact first: ...

Proceed? Adjust the direction? Narrow the scope?
```

Then **wait**. Do not begin editing on the same turn.

Two exceptions where you may proceed without asking:
- The user explicitly said to go ahead without check-ins.
- The only changes are **broken-function fixes** (mobile overflow, missing focus
  states, leftover placeholders, dead links). These are completion, not taste.

---

## 10. Phase 1 — inspect the project first (blocking)

Before any modification, determine and write down:

```text
1.  Framework
2.  Language
3.  Styling system
4.  Component system
5.  Design system
6.  Typography
7.  Color tokens
8.  Spacing tokens
9.  Radius tokens
10. Shadow / elevation system
11. Icon system
12. Animation / motion system
13. Existing assets
14. Brand identity
15. Existing screenshots / pages
```

Rules:
- Read the existing code before changing anything.
- Look for conventions that already exist and follow them.
- **Never introduce a new technology to solve an aesthetic problem.**

If an item cannot be determined, record it as `unknown` — do not guess.

---

## 11. The abstraction layer (this is what makes the skill portable)

Diagnose in **design concepts**, never in framework-specific class names:

```text
PRIMARY_COLOR   SECONDARY_COLOR   ACCENT_COLOR
SURFACE         TEXT_PRIMARY      TEXT_SECONDARY   BORDER
DISPLAY_FONT    BODY_FONT
RADIUS          SHADOW            SPACING          MOTION
```

Then map concepts to the stack actually in use:

```text
Tailwind           → theme tokens in config, then utility classes
Plain CSS / SCSS   → CSS custom properties
CSS Modules        → local declarations + shared variables
styled-components  → the theme object
Vue / Svelte       → the existing component & style system
Flutter            → ThemeData / design tokens
SwiftUI            → environment / theme tokens
Web components     → :host custom properties
```

Never force a migration. The *diagnosis* must be identical across stacks;
the *implementation* must be native to each.

---

## 12. Evidence levels and visual audit

Every report opens by declaring its evidence level. This is not a formality — it
bounds what the skill is entitled to claim.

```text
EVIDENCE LEVEL
  [ ] source only          static analysis of code, CSS, tokens, assets
  [ ] static + rendered    the app was run; output observed indirectly
  [ ] browser + screenshots images actually captured and examined
```

### Visual analysis is first-order

When the environment allows running the project, **the visual audit is required**, not
a bonus. These cannot be derived from source: visual density · perceived hierarchy ·
real contrast · balance · rhythm · typographic rendering · image quality · composition ·
responsive behaviour · overall coherence.

A stylesheet tells you a radius is `12px`. It does not tell you the page reads as a
flat undifferentiated field.

### The honesty rule

> If no browser, screenshot or rendering is genuinely available, write exactly:
>
> ```text
> Visual evidence unavailable.
> Assessment limited to static/source analysis.
> ```

**Never write "the page visually feels…" without having observed the rendering.**
Mark visual-only tells `not-assessed`. Never simulate the output of a tool that does
not exist. Downgrading your own confidence is always correct; inflating it is not.

See `workflows/audit.md` §3 for the tool-availability ladder and §3b for cross-checking.

---

## 13. Signals, not scores — and the sufficiency threshold

Never output "this site is 87% AI-generated". Produce a **weighted signal inventory**.

```text
P0 = critical signal      (identity, hierarchy, structure, major motion)
P1 = important signal     (components, imagery, spacing, interaction)
P2 = cosmetic signal      (polish, micro-animation, details)
```

Clustering heuristic from the research:

```text
0–1 confirmed signal  → probably coincidence
2–3 confirmed signals → several signals present
4+  confirmed signals → significant concentration of signals
```

Present this as a **diagnostic heuristic only** — never as proof of AI generation.
Only signals that survived false-positive validation are counted.

### No aesthetic score

Never invent a global quality number:

```text
AI Slop Score: 23/100        ❌
Design quality: B+           ❌
87% AI-generated             ❌
```

Aesthetic quality is not quantifiable and a number invites mechanical optimisation
against it. Answer these five questions instead — they are the real deliverable:

```text
What problems are materially affecting the design?
Which are justified?
Which need intervention?
What changed?
What remains intentionally unchanged?
```

### The sufficiency threshold

The skill stops at **sufficiency**, not at perfection. Work is complete when the
design is coherent, the hierarchy is clear, the identity is stronger and every
remaining signal is justified and reported. Remaining P2s are a legitimate outcome.

---

## 14. False positives are the heart of the skill

For every tell, actively look for the contextual justification before touching anything:

```text
Inter         → may be a deliberate typographic decision
Purple        → may be the brand colour
Dark mode     → may be right for the product
Glassmorphism → may have a coherent visual function
Rounded cards → may belong to the design system
Lucide        → may be the deliberate icon choice
Bento grid    → may be entirely appropriate (weak tell)
Gradient      → may be part of the identity
Tailwind      → is never evidence of AI slop
```

Evidence that clears a tell: brand guidelines, a design-system file, a documented
token, a `DESIGN.md`, a git history showing deliberate iteration, a logo or existing
asset that shares the colour, consistent semantic usage across the codebase.

A tell with a justification is **cleared** and reported under "False positives —
ignored intentionally", not fixed.

---

## 15. The Brother Test (meta-signal)

```text
Hide the logo/brand.

Could this interface belong to another product
without changing its visual system?

Examples: CRM · fintech · project management tool ·
AI SaaS · developer tool · analytics dashboard

If yes, the interface may lack visual identity.
```

This test must lead to **an identity analysis**, never to adding arbitrary decoration.
Failing it opens `workflows/art-direction.md`; it does not authorise blobs, grain,
or a random accent colour.

### If the site fails the test

```text
do not decorate immediately.
```

Failing the Brother Test is a **diagnosis of missing identity**, not an instruction to
make the design spectacular. Before proposing anything, examine where identity could
legitimately come from:

```text
brand                 what already exists — logo, colours, voice, assets
content               what the product actually says and shows
typography            hierarchy and character already available
composition           rhythm, density, the shape of the page
imagery               real product, real people, real proof
tone                  register of the writing
product-specific info the data, states and objects unique to this product
visual signatures     anything already recurring that could be amplified
```

Then name **what is actually missing**. Very often the answer is not "a new visual
device" but "the identity that already exists is applied timidly" — which is
**STRENGTHEN**, not invention.

Adding decoration to pass the test is the failure mode this section exists to prevent.

---

## 16. Art direction before remediation (mandatory gate)

Before any broad modification, answer — in writing, in the report:

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

- If the project already has a strong identity → **preserve and reinforce it**.
- If identity is absent → you may propose a direction, but it must derive from the
  product, audience, content, brand, context and what already exists.
- A named direction is required ("editorial", "utilitarian-dense", "technical-mono",
  "warm-consumer", "industrial"). "Clean and modern" is not a direction — it is the
  slop default.

### The name is a label, never a recipe

Derive, do not select:

```text
product / context evidence → design hypothesis → principles
→ concrete decisions → coherent visual system
```

Forbidden: `Direction = "Industrial Editorial" → therefore use X, Y, Z.` ❌
That lets a label generate decisions instead of evidence. Every decision must trace
back to the hypothesis.

### Prefer one dominant visual signature

Not "one motif only". Additional identity elements are allowed when they each have
independent semantic justification, form a coherent system, do not compete
unnecessarily, and together reinforce identity — e.g.
`typography + brand colour + a photographic treatment + a small geometric language`
operating as one idea. What fails is unrelated devices bolted on for personality.

---

## 17. Forbidden mechanical substitutions

Never perform these *because they are supposedly "less AI"*:

```text
Inter → Instrument Serif
purple → sage
gradient → grain
cards → bento
rounded-2xl → rounded-md
Lucide → another icon set
fade-in-up → another animation
```

Every modification must answer a design reason, written in the changelog entry.

---

## 18. Minimum necessary change

> **Change as little code as necessary to achieve a meaningful visual improvement.**

- Do not refactor the whole app if tokens plus a few components suffice.
- Do not change technical architecture without reason.
- Do not migrate framework.
- Do not swap component libraries to obtain a different aesthetic.

---

## 19. Hard prohibitions

```text
DO NOT:
- ban Tailwind, React, Next.js, shadcn, Inter, purple, gradients,
  rounded corners, glassmorphism, Lucide
- force serif typography
- force asymmetry
- force bento grids
- add grain everywhere
- add animations everywhere
- add decorative blobs
- add random illustrations
- rewrite the application architecture
- replace a working design system without reason
- claim a design was AI-generated based only on visual patterns
```

---

## 20. Safety and scope control

### Before the first edit

```text
1. Is the working tree clean?  → if not, ask before touching anything.
2. Is this a VCS repo?         → if yes, work on a dedicated branch.
3. Does the build pass NOW?    → capture the baseline; you need it to compare.
4. Are there tests?            → run them now, not only at the end.
```

Use whatever the project actually uses. If it is a git repo:

```bash
git status --porcelain          # must be empty, or stop and ask
git checkout -b design/art-direction
git rev-parse HEAD              # record: this is the rollback point
```

**Never commit on the user's behalf unless asked.** Leave changes staged or in the
working tree so they can be reviewed and reverted with one command.

If there is no VCS, say so explicitly before editing and keep the diff smaller still.

### Commit in reviewable batches

If the user does want commits, one per remediation batch, never one giant commit:

```text
design(tokens): establish semantic colour roles and type scale
design(components): introduce surface elevation hierarchy
design(motion): honour reduced-motion, remove blanket entrance animation
fix(a11y): restore visible focus indicators
```

Each message states the design reason. A reviewer must be able to revert one batch
without unpicking the others.

### Scoping the audit — do not try to read everything

Real projects are too large to audit exhaustively. Sample deliberately:

| Project size | Audit surface |
|---|---|
| < 20 components | Everything |
| 20–100 components | Token layer + shared primitives + 3–5 representative pages |
| Large app / monorepo | Token layer + design-system package + the **single** highest-traffic surface |
| Monorepo, many apps | **Ask which app.** Never audit several at once. |

Choose pages that differ structurally — a marketing page, a dense data view, a form,
an empty state. Five varied pages reveal more than twenty similar ones.

**Token-layer and shared-component findings generalise. Page findings do not.**
Say in the report what you sampled and what you did not — an audit of 5 of 80 pages
is useful, but only if its scope is stated honestly.

### Stop conditions

Stop and report rather than pushing on when:

- the confirmed signals are 0–1 (coincidence — say so, change nothing)
- the project has a strong existing direction and only needs consistency notes
- the direction depends on product knowledge you do not have
- fixing a tell would require architectural change
- you have made the high-impact changes and the rest is churn

**A short, well-argued "this is mostly fine, here are three things" is a valid and
frequently correct output.**

---

## 21. Reference map — load on demand

Read `rules/index.md` first — the compact triage table. Pull full rules from
`rules/tells.yaml` per category. Load a reference file only when remediating that domain.

| File | Use when |
|---|---|
| `rules/index.md` | **Always.** 54-rule triage table, ~1.6k tokens |
| `references/visual-tells.md` | Severity model, clustering, weak tells, traceability |
| `references/color.md` | Palette, gradients, semantic colour roles |
| `references/typography.md` | Families, pairing, scale, hierarchy |
| `references/layout.md` | Hero, grids, rhythm, composition, responsive |
| `references/components.md` | Radius/shadow/border hierarchy, surfaces |
| `references/imagery.md` | Real assets, mockups, avatars, generated visuals |
| `references/content.md` | Empty copy, boilerplate tiers, leftover placeholders |
| `references/motion.md` | The 12 motion tells + state-driven motion |
| `references/accessibility.md` | Contrast, focus, states, reduced motion |
| `references/identity.md` | Brother Test, motif, differentiation |
| `references/remediation.md` | Stack-native mapping recipes |

Workflows: `workflows/audit.md` → `art-direction.md` → `remediation.md` → `verification.md`.
Tests: `tests/scenarios.md` (7 scenarios the skill must pass, incl. 6 that must produce
**no** or **minimal** changes).

---

## 22. Final report format

**Normative full skeleton: `workflows/verification.md` §4** (loaded at reporting time).

Required sections, in order:

```text
PROJECT CONTEXT · EVIDENCE LEVEL · OBSERVATIONS · ART DIRECTION
IMPLEMENTATION · VERIFICATION · INTENTIONAL PRESERVATIONS
REMAINING SIGNALS · STOP CONDITION
```

Each observation carries: signal · evidence · confidence · category ·
false-positive check · diagnosis · **disposition**.

ART DIRECTION must record **existing strengths**, the **design hypothesis**, the
principles, the proposed changes, and the **explicitly rejected alternatives** —
what was considered and deliberately not done, with the reason.

### INTENTIONAL PRESERVATIONS is mandatory

Not optional, and must not be empty on a real project. It is the evidence that the
skill exercised judgement rather than pattern-matching:

```text
- Brand terracotta preserved because it is a documented identity colour.
- Inter preserved because typography hierarchy, not font family, was the actual issue.
- Lucide preserved because icon consistency is already strong.
- Card system preserved; only its uniform visual weight was modified.
```

A report with no preservations means either a genuinely exceptional project, or a
skill that deleted everything it detected. Assume the second and re-check.

### Report rules

- **Never a bare score**, percentage or grade. Explain decisions.
- **Never state or imply the design was AI-generated.** Origin is not knowable.
- Declare the evidence level honestly; mark unassessed tells as such.
- List uncertain signals as open questions rather than acting on them.
