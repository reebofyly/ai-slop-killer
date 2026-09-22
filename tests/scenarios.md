# Test scenarios

Ten conceptual scenarios. The skill must **detect real problems AND not "correct"
intentional choices**.

> Eight of the ten scenarios must produce **no or minimal** changes. Only scenarios 1
> and 10 warrant substantial remediation. A skill that "fixes" scenarios 2–9 is broken —
> false positives are the dominant failure mode, not missed tells.

Run a scenario by describing the project to the agent and comparing its behaviour to
the expectations below.

---

## 1. AI-sloppy SaaS landing page

**Setup** — Generated marketing page. Indigo→violet gradient appearing in no owned
asset; Inter at every size with no scale; pill badge + centered H1 + two CTAs; exactly
three equal feature cards with sparkle/zap/shield icons; 1·2·3 step row; Starter/Pro/
Business at $0/$29/$99; four-column footer with `href="#"`; identical `fade-in-up` on
everything at page load; pulsing "all systems operational" dot on a static export;
infinite logo marquee; DiceBear testimonial avatars; gradient block instead of a product
screenshot; `<title>My App</title>`; no `prefers-reduced-motion`; horizontal overflow at
375px.

**Expected — this is the positive case.**

- Confirmed signals across colour, typography, layout, components, imagery, content,
  identity, motion, a11y, responsive → "significant concentration"
- **Dispositions must be mixed**, not all REMOVE. Expect e.g. REMOVE for the fake
  status pulse and the decorative gradient; MODIFY for the uniform three cards;
  STRENGTHEN for anything brand-adjacent that exists; KEEP for the icon set.
- Brother Test fires; art-direction workflow mandatory
- Fix order: overflow + dead links + placeholders + focus → tokens → components →
  composition → motion → imagery
- Must **not** produce cream + editorial serif + sage (`identity-03`)
- Must **not** swap Lucide, ban Tailwind, or force asymmetry

**Fails if** it outputs the 2026 tasteful template, or performs a mechanical
purple→sage / Inter→serif substitution.

---

## 2. Intentionally purple branded product

**Setup** — Purple is the brand colour: it is in the logo, favicon, OG image and a
`--brand-violet` named token; brand guidelines exist in `DESIGN.md`; the gradient recurs
as a documented system with a stated rule for where the accent appears.

**Expected**

- `color-01` raised as a raw signal, then **CLEARED** in phase 5
- Reported under "False positives — ignored intentionally: purple is the documented
  brand colour (logo, favicon, named token, DESIGN.md)"
- **Zero colour changes**; disposition `KEEP`
- If the purple is under-exploited, the correct disposition is `STRENGTHEN`, never a
  replacement
- Any genuinely separate issues (e.g. missing focus states) still reported

**Fails if** purple is changed, softened, or a second accent is introduced.

---

## 3. Minimalist editorial website

**Setup** — Deliberate editorial direction: serif display paired with a text face, warm
off-white background, generous measure, almost no motion, rigorous symmetric grid,
strong type scale, a documented style guide.

**Expected**

- Few or no confirmed signals
- `layout-05` (symmetry) raised then **CLEARED** — rigour is the direction
- Near-absence of motion recognised as a decision, not `motion-10`
- Direction found to already exist → **preserve and reinforce**; possibly minor
  consistency notes only

**Fails if** the skill adds motion, breaks the grid, adds an accent colour, or treats
restraint as absence of design.

---

## 4. Dashboard using shadcn intentionally

**Setup** — Internal analytics tool deliberately built on shadcn/ui with its default
neutral ramp; cards everywhere because the content is genuinely card-shaped; dense,
utilitarian; team documented the decision to use the library defaults for velocity.

**Expected**

- `color-05`, `comp-01`, `comp-02` raised then **CLEARED** — documented decision,
  cards are the correct affordance for a dashboard, uniformity aids scanning
- `identity-01` **CLEARED** — internal tool, neutrality is legitimate
  (`workflows/art-direction.md §7`)
- Output: "neutral by requirement — improve hierarchy/consistency/accessibility only"
- Genuine issues still reported: contrast, focus states, empty/error/loading states,
  wide-screen measure

**Fails if** it proposes replacing shadcn, adds brand identity to an internal tool, or
de-cards a dashboard.

---

## 5. Tailwind application with strong art direction

**Setup** — Tailwind, but the theme is fully customised: named semantic tokens, a
deliberate type scale, a radius hierarchy that differs by surface level, a distinctive
recurring corner treatment as motif, purposeful motion on three interactions only.

**Expected**

- **Tailwind is never treated as evidence**
- Very few confirmed signals
- Brother Test **passes** — the motif is identified and named
- Recommendation: preserve; at most extend the existing system where inconsistently applied

**Fails if** the skill flags the project merely for using Tailwind, or proposes
migrating away from utilities.

---

## 6. Dark-mode developer tool

**Setup** — Terminal-adjacent dev tool, dark by default, monospace throughout, neon-ish
syntax accent colours, a real streaming status indicator driven by an actual websocket,
a genuine embedded terminal with a real caret.

**Expected**

- `color-03` **CLEARED** — dark mode is right for the usage context
- `color-04` **CLEARED** — syntax colours are functional and systematic
- `motion-06` **CLEARED** — the pulse is driven by real data
- `motion-07` **CLEARED** — it is an actual terminal input
- `type-01` **CLEARED** if monospace has a real scale; **confirmed** if one size everywhere
- Still checks: contrast on dark (where eyeballing fails most), focus visibility

**Fails if** it forces a light theme, removes the status pulse, or removes a real caret.

---

## 7. Website with legitimate glassmorphism

**Setup** — Media/streaming product. Translucent blurred navbar over scrolling video,
glass controls over media, modal scrims. Layering is real and consistent.

**Expected**

- `comp-03` raised then **CLEARED** — glass sits over genuinely layered content and
  serves depth and focus; disposition `KEEP`
- Skill recalls that glassmorphism is a **weak tell explicitly cleared by the research**
  as standalone evidence
- Contrast of text over translucent surfaces **is** verified — that is the real risk

**Fails if** glassmorphism is removed on principle or replaced with grain/another trend.

---

## 8. Clean project, nothing to do

**Setup** — A well-art-directed product with a documented design system, one
inconsistency (a single off-scale spacing value) and nothing else.

**Expected**

- 0–1 confirmed signals → "probably coincidence"
- Skill **stops** and reports rather than inventing work
- No art direction proposed; the existing one is recognised
- Output is a short note, not a refactor

**Fails if** the skill manufactures findings to justify itself, proposes a new
direction, or opens a remediation pass. This is the anti-overreach test and it is as
important as scenario 1.

---

---

## 9. Repetitive design system with excellent hierarchy

**Setup** — A product with heavy component repetition: one radius everywhere, one
spacing scale, one button style, one card family. But hierarchy is excellent — scale,
density, colour and placement clearly signal what matters, and sections have distinct
rhythm and weight.

**Expected**

- `comp-01`, `space-01` raised as raw signals then **CLEARED**
- Skill explicitly invokes the repetition doctrine: this is **design-system
  repetition**, not **compositional monotony**
- Disposition `KEEP` on the component system
- Report states that repetition is the system working as intended

**Fails if** the skill introduces variation "for visual interest", breaks the radius
scale, or treats consistency as monotony.

---

## 10. Mixed dispositions — the four-outcome test

**Setup** — One project containing, simultaneously:

```text
- Lucide icons, used consistently and semantically
- a documented brand colour that appears only once, in the footer
- five card sections of identical visual weight but differing importance
- a decorative hero gradient matching no brand token and serving no function
```

**Expected — all four dispositions must appear in one report:**

```text
KEEP        Lucide icons          — consistent and semantic already
STRENGTHEN  brand colour          — right colour, badly distributed; amplify it
MODIFY      uniform card weight   — keep the card language, add hierarchy
REMOVE      decorative gradient   — no function, no brand relationship
```

**This is the single most important regression test in the suite.** It proves the
skill does not convert every detection into a deletion.

**Fails if** the report contains only REMOVE dispositions, if the brand colour is
replaced rather than amplified, if the cards are deleted rather than re-weighted, or
if the icon set is swapped.

---

## Cross-cutting assertions

Check on every scenario:

| # | Assertion |
|---|---|
| 1 | No score of the form "X % AI-generated" is produced |
| 2 | No claim about the design's origin |
| 3 | Severities match `tells.yaml`; weak tells never reported alone |
| 4 | "False positives" section present and substantive |
| 5 | No framework/library migration proposed |
| 6 | No new dependency introduced |
| 7 | Output is not cream + editorial serif + sage (`identity-03`) |
| 8 | Every change carries a design reason that is not "looks less AI" |
| 9 | Visual analysis claimed only if screenshots were genuinely observed |
| 10 | Uncertain signals reported as open questions, not silently changed |
| 11 | Loaded `rules/index.md`, not the full `tells.yaml`, for a scoped task |
| 12 | Stopped after art direction and asked before editing (unless exempt) |
| 13 | Checked working tree / branch before the first edit |
| 14 | Stated audit scope: what was sampled and what was not |
| 15 | On a clean project, produced "mostly fine + 3 notes" rather than manufacturing work |
| 16 | Every confirmed observation carries a disposition, not just a severity |
| 17 | Dispositions are mixed; the report is not uniformly REMOVE |
| 18 | `INTENTIONAL PRESERVATIONS` section present and non-empty |
| 19 | `EVIDENCE LEVEL` declared; "Visual evidence unavailable" used when nothing was rendered |
| 20 | No global aesthetic score of any kind |
| 21 | Repetition doctrine applied: system repetition distinguished from compositional monotony |
| 22 | Nothing added solely to be distinctive (Uniqueness ≠ Quality) |
| 23 | Direction name used as a label; decisions trace to the hypothesis, not the label |
| 24 | STOP CONDITION stated; skill halted at sufficiency rather than optimising on |
| 25 | No REMOVE issued on a low-confidence observation |

---

## The portability test

Give the identical skill two developers:

```text
Developer A — React + Tailwind + shadcn
Developer B — Vue + CSS Modules + custom components
```

with conceptually equivalent sloppy projects. The **diagnosis must match**:

```text
- generic hero
- weak typography hierarchy
- excessive card uniformity
- no visual identity
- generic motion
```

The **implementation must differ** and stay native to each stack (theme tokens and
component variants for A; shared CSS variables and module classes for B). Neither is
told to adopt the other's technology.

If diagnoses diverge, the abstraction layer leaked framework specifics — fix the
reference files, not the rules.
