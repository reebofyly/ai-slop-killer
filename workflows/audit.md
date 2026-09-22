# Workflow — Audit (phases 1–4)

Covers: Inspect → Detect → Classify → Validate false positives.
**No file may be modified during this workflow.**

---

## §0 — Scope the audit before starting

Real projects are too large to read exhaustively. Decide the surface first:

| Project size | Audit surface |
|---|---|
| < 20 components | Everything |
| 20–100 components | Token layer + shared primitives + 3–5 representative pages |
| Large app / monorepo | Token layer + design-system package + the single highest-traffic surface |
| Monorepo, many apps | **Ask which app.** Never audit several at once. |

Pick pages that differ **structurally**, not topically: a marketing page, a dense data
view, a form, an empty state. Five varied pages reveal more than twenty similar ones.

Token-layer and shared-component findings generalise across the app. Page-level
findings do not — never extrapolate one page to the whole product.

Record what you sampled and what you skipped; it goes in the report. An audit of 5 of
80 pages is useful **only if its scope is stated**.

---

## §1 — Inspect (blocking)

Determine and record all fifteen. Mark `unknown` rather than guessing.

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
10. Shadow/elevation system
11. Icon system
12. Animation/motion system
13. Existing assets
14. Brand identity
15. Existing screenshots/pages
```

### Where to look

- **Manifests** — `package.json`, `pubspec.yaml`, `Gemfile`, `composer.json`,
  `*.csproj`, `go.mod`, `requirements.txt`
- **Config** — styling/theme config, build config, framework config
- **Tokens** — theme files, `:root` variables, token JSON/YAML, asset catalogues
- **Docs** — `README`, `DESIGN.md`, `CONTRIBUTING.md`, style guide, Storybook, Figma links
- **Brand** — logo, favicon, OG image, `public/`, `static/`, `assets/`, `brand/`, `press/`
- **History** — `git log` on style files shows whether design was iterated deliberately

### Hard rules

- Read the existing code **before** changing anything.
- Follow conventions that already exist.
- **Never introduce a new technology to solve an aesthetic problem.**

---

## §2 — Detect: Level 1, static analysis

Always possible. Walk `rules/index.md` (the compact triage table) to decide which
rules plausibly fire, then pull **only those categories** from `rules/tells.yaml`.
Collect **raw signals with evidence**.
Every signal needs a `file:line` or a concrete quotation. No evidence → not a signal.

Targets: code · CSS · tokens · components · structure · animations · assets ·
typography · icons.

### Efficient sweep order

1. **Token layer** — is there one? Is it used, or bypassed by hard-coded values?
   (`color-05`, `comp-08`, `space-02`)
2. **Global styles** — count distinct radius, shadow, gap values. One of each across
   the whole app is the `comp-01` / `space-01` signal.
3. **Typography** — count families and weights; look for a scale. (`type-01`, `type-02`)
4. **Shared components** — card, button, section header, icon container.
   (`comp-02`, `comp-04`, `comp-05`, `comp-07`)
5. **Landing/entry page markup** — hero structure, feature count, pricing, footer.
   (`layout-01` … `layout-06`)
6. **Motion** — search for transitions, keyframes, animation utilities, motion library
   usage, and for a reduced-motion query. (`motion-*`)
7. **Content** — grep placeholders, metadata, dead links. (`content-03`, `layout-06`)
8. **Accessibility** — `outline:none`, focus styles, state components. (`a11y-*`)
9. **Assets** — inventory what exists versus what the pages actually use. (`img-*`)

---

## §3 — Run the application and audit visually (first-order)

**When the environment allows running the project, this phase is required.** It is not
an optional enhancement to the static audit.

Tool-availability ladder — use the highest rung actually available:

| Rung | Capability | What becomes assessable |
|---|---|---|
| 4 | Browser automation + screenshots | Everything, including motion and responsive |
| 3 | Dev server, no screenshots | Console errors, computed styles if inspectable |
| 2 | Static render of markup/CSS | Layout structure, contrast arithmetic |
| 1 | Source only | Static tells only |

If rung 3+ is available, run the project and observe: homepage · main pages ·
responsive (mobile, tablet, desktop, wide) · component states · interactions · motion.

### What only the rendering can tell you

These cannot be derived reliably from source, and guessing at them from CSS is the
most common way an audit goes wrong:

```text
visual density        perceived hierarchy     real contrast
balance               rhythm                  typographic rendering
image quality         composition             responsive behaviour
overall coherence
```

### The honesty rule

> Never claim a visual analysis was performed if no image or screenshot was actually
> observed. If you could not render, write exactly:
>
> ```text
> Visual evidence unavailable.
> Assessment limited to static/source analysis.
> ```

Mark visual-only tells `not-assessed`. Never write "the page visually feels…" without
having observed it. Never simulate the output of a tool that does not exist.

Visual-only tells: `img-04`, `resp-01`, `resp-02`, `a11y-01` (measured), most
`motion-*` behaviour, `identity-01` (properly run).

---

## §3b — Cross-check source against rendering

When both a static audit and a rendering exist, reconcile them before classifying.
Each direction of mismatch means something different:

| Situation | Reading |
|---|---|
| Source suggests a problem, rendering looks fine | Likely a **false positive**. The token exists but is overridden, scoped, or visually inconsequential. Downgrade or clear. |
| Rendering shows a problem, source looked clean | A **composition or emergent** problem. Often the most valuable finding — monotony, density, balance. |
| Both agree | **High confidence.** Record as such. |
| Cannot render | Static only; cap confidence at medium for anything visual. |

Record a `confidence` value (high / medium / low) per observation. It is carried into
the report and it constrains how aggressively a disposition may be applied:
**never REMOVE on low confidence.**

---

## §4 — Classify

For each raw signal record:

```text
id | name | severity (from tells.yaml, never inflated) | evidence | scope
```

`scope` = global (token-level) / component / page / single instance. Global-scope
signals matter far more than isolated instances.

Do not promote a `weak` tell to P0 because several instances exist. Weak tells
(`comp-03`, `layout-03`, `layout-04`, `space-02`, `motion-04`, `motion-07`, `motion-09`)
count only inside a cluster, never alone.

---

## §5 — Validate false positives (critical)

**This phase decides the quality of the whole skill.** For every raw signal, run the
rule's `diagnostic_questions` and hunt for the contextual justification.

### Evidence that clears a tell

- brand guidelines, style guide, `DESIGN.md`, Figma link
- a **named** design token (a named token is a decision; an inline hex is not)
- the value appears in an owned asset — logo, favicon, OG image, illustration
- git history showing deliberate iteration
- consistent semantic usage across the codebase
- documented product context (dark mode for a developer tool; neutrality for a
  white-label or internal product)
- a comment explaining an optical correction

### Outcome per signal

```text
CONFIRMED  → no justification found → counts, and is eligible for remediation
CLEARED    → justification found    → reported under "False positives", untouched
UNCERTAIN  → ambiguous              → report, ask the user, do NOT modify
```

**Default to CLEARED when genuinely ambiguous.** A wrongly "fixed" intentional choice
is a worse failure than a missed tell — it is the exact behaviour the skill must avoid.

### Then cluster

Count **confirmed signals only**:

```text
0–1 → probably coincidence
2–3 → several signals present
4+  → significant concentration of signals
```

Present as a diagnostic heuristic. **Never state or imply a design was AI-generated.**

### Finally, the Brother Test

Run `identity-01` last, as a whole-interface judgement — see `references/identity.md`.
If it fires and is not cleared, `workflows/art-direction.md` becomes mandatory.

---

## §6 — Assign a disposition (phase 7)

> **Detect ≠ Fix.** A detected signal never by itself authorises a modification.

Triage answered *is this signal real?* Disposition answers *what should happen to it?*
**Every CONFIRMED observation gets exactly one.** This is the step that stops detection
collapsing into deletion.

```text
KEEP        intentional, coherent, sufficiently justified  → change nothing
STRENGTHEN  right choice, weak or under-exploited expression → improve it
MODIFY      sound principle, problematic current form       → change the form
REMOVE      unjustified / incoherent / plainly generic      → remove it
```

### How to choose

Ask in this order and stop at the first yes:

1. **Is the choice itself defensible for this product?**
   No → `REMOVE`.
2. **Is the principle right but the current form causing the problem?**
   Yes → `MODIFY`. (Most repetition and hierarchy findings land here.)
3. **Is the choice right but expressed too timidly or inconsistently?**
   Yes → `STRENGTHEN`.
4. Otherwise → `KEEP`.

### Constraints

- **Never REMOVE on low confidence.** Downgrade to MODIFY, or report as UNCERTAIN.
- `REMOVE` is for genuinely unjustifiable artefacts: decorative gradient with no
  function, fake status pulse, fake caret, generic stock imagery, decoration unrelated
  to the product.
- A plan that is nearly all `REMOVE` has skipped the diagnosis step. Re-check it.
- `KEEP` observations are **not** discarded — they go into INTENTIONAL PRESERVATIONS
  in the report. Showing what you deliberately did not touch is part of the deliverable.

### Worked example

```text
OBSERVATION       five sections share the same rounded card treatment
EVIDENCE          src/sections/*.vue, shared Card component
CONFIDENCE        high (source + rendering agree)
FP CHECK          card system is intentional and reused across the app
DIAGNOSIS         repetition is fine; identical visual WEIGHT is not, because the
                  five sections differ in semantic importance
DISPOSITION       MODIFY
DECISION          keep the card language; introduce hierarchy via surface treatment,
                  scale, spacing and content density
```

Not: "rounded cards detected → remove rounded cards → use sharp corners."

---

## Exit criteria

- [ ] All 15 inspection items recorded (or marked `unknown`)
- [ ] Every signal has concrete evidence
- [ ] Every signal has been through false-positive validation
- [ ] Severities taken from `tells.yaml`, not inflated
- [ ] Analysis level honestly stated; unassessed tells marked as such
- [ ] Audit scope recorded (what was sampled, what was skipped)
- [ ] Evidence level declared; visual audit run if the environment allowed it
- [ ] Confidence recorded per observation
- [ ] Every CONFIRMED observation carries a disposition
- [ ] KEEP items captured for INTENTIONAL PRESERVATIONS
- [ ] Zero files modified

→ Proceed to `workflows/art-direction.md`.
