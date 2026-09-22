# Test scenarios

Seven conceptual scenarios. The skill must **detect real problems AND not "correct"
intentional choices**.

> Six of the seven scenarios must produce **no or minimal** changes. Only scenario 1
> warrants substantial remediation. A skill that "fixes" scenarios 2–7 is broken —
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
- **Zero colour changes**
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
  serves depth and focus
- Skill recalls that glassmorphism is a **weak tell explicitly cleared by the research**
  as standalone evidence
- Contrast of text over translucent surfaces **is** verified — that is the real risk

**Fails if** glassmorphism is removed on principle or replaced with grain/another trend.

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
