# Workflow — Audit (phases 1–4)

Covers: Inspect → Detect → Classify → Validate false positives.
**No file may be modified during this workflow.**

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

Always possible. Walk `rules/tells.yaml` and collect **raw signals with evidence**.
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

## §3 — Detect: Level 2, visual analysis

**Only if the environment genuinely allows running the project and capturing output.**

Tool-availability ladder — use the highest rung actually available:

| Rung | Capability | What becomes assessable |
|---|---|---|
| 4 | Browser automation + screenshots | Everything, including motion and responsive |
| 3 | Dev server, no screenshots | Console errors, computed styles if inspectable |
| 2 | Static render of markup/CSS | Layout structure, contrast arithmetic |
| 1 | Source only | Static tells only |

If Level 2 runs, examine: homepage · main pages · responsive (mobile, tablet, desktop,
wide) · component states · interactions · motion.

> **Never claim a visual analysis was performed if no image or screenshot was actually
> observed.** Mark visual-only tells `not-assessed` and say so in the report. Never
> simulate the output of a tool that does not exist.

Visual-only tells: `img-04`, `resp-01`, `resp-02`, `a11y-01` (measured), most `motion-*`
behaviour, `identity-01` (properly run).

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

## Exit criteria

- [ ] All 15 inspection items recorded (or marked `unknown`)
- [ ] Every signal has concrete evidence
- [ ] Every signal has been through false-positive validation
- [ ] Severities taken from `tells.yaml`, not inflated
- [ ] Analysis level honestly stated; unassessed tells marked as such
- [ ] Zero files modified

→ Proceed to `workflows/art-direction.md`.
