# Visual tells — overview and clustering

Machine-readable catalogue: `rules/tells.yaml`. This file is the human-facing map.

## How to read a tell

A tell is **an unchosen default**, not a banned value. Three questions decide everything:

1. **Is it justified?** Brand, design system, documented decision, product context.
2. **Is it applied with hierarchy?** Or uniformly to everything?
3. **Is it interchangeable?** Would another product use the identical treatment?

If justified → clear it. Report under "False positives", do not touch.

A tell that survives those three questions still does **not** authorise deletion. It
receives a disposition — `KEEP` / `STRENGTHEN` / `MODIFY` / `REMOVE` — per
`workflows/audit.md` §6. Detection and repair are separate decisions.

## Repetition doctrine

```text
Repetition is not the problem. Unjustified repetition is the problem.
```

A design system is necessarily repetitive. Repetition becomes a signal only in
combination: `repetition + no hierarchy + no semantic reason + no meaningful variation`.

| Design-system repetition — legitimate | Compositional monotony — a signal |
|---|---|
| same radius across components | every section has the same composition |
| same spacing scale | every card has the same visual weight |
| same button style | every element has the same density |
| same treatment for one family of cards | every section has the same rhythm |
| same typographic system | nothing signals what matters most |

Left column → usually `KEEP` or `STRENGTHEN`.
Right column → usually `MODIFY`. Rarely `REMOVE`.

This distinction governs `comp-01`, `comp-02`, `comp-05`, `layout-02`, `layout-05`,
`space-01` and `motion-01` in particular — the rules most often misread as
"too much repetition, delete some".

## Severity

| Level | Meaning | Examples |
|---|---|---|
| **P0** | Critical — identity, hierarchy, structure, major motion | `identity-01`, `type-01`, `layout-01`, `motion-01`, `a11y-02`, `resp-01` |
| **P1** | Important — components, imagery, spacing, interaction | `comp-01`, `img-01`, `motion-05`, `a11y-03` |
| **P2** | Cosmetic — polish, micro-animation, detail | `layout-03`, `comp-05`, `motion-02`, `space-02` |

Never inflate severity. The research is explicit that some tells are weak.

## Weak tells — never count alone

`comp-03` glassmorphism · `layout-03` 1·2·3 row · `layout-04` three pricing tiers ·
`space-02` off-scale values · `motion-04` single direction · `motion-07` caret ·
`motion-09` image hover zoom.

**Explicitly cleared by the research as standalone evidence:** bento grids (0.1 % of
complaints and actively defended by designers), mesh/aurora backgrounds (keyword
artifact), glassmorphism, Tailwind, Next.js, rounded corners, a chosen purple.

## Clustering heuristic

```text
0–1 validated signal  → probably coincidence
2–3 validated signals → several signals present
4+  validated signals → significant concentration of signals
```

Only signals that **survived false-positive validation** count. This is a diagnostic
heuristic to direct attention — never a claim about origin.

## The 54 rules by category

| Category | Rules | Core question |
|---|---|---|
| color | 5 | Is the palette semantic and owned? |
| typography | 3 | Is there hierarchy? (not: is the font banned) |
| layout | 6 | Does composition follow content? |
| components | 8 | Is there a surface/elevation hierarchy? |
| spacing | 2 | Does space express grouping and importance? |
| imagery | 6 | Are assets real and related to the product? |
| content | 3 | Is the copy specific and complete? (`references/content.md`) |
| identity | 3 | Would this survive the Brother Test? |
| motion | 12 | Does motion communicate state or simulate life? |
| accessibility | 4 | Is it usable, measured, complete? |
| responsive | 2 | Has it actually been opened at each width? |

## Traceability to the 47 research signs

The 47 signs map to 54 rules. Seven signs bundled two independently detectable and
independently remediable problems and were split (e.g. the "no human proof" sign →
`img-05` logo wall + `img-06` testimonials; "mobile never reviewed" → `resp-01`
breakage + `resp-02` scaling; the accessibility sign → the four `a11y-*` rules).
No sign was dropped. The mapping lives in `meta.traceability` in `tells.yaml`.

## The meta-signal

`identity-01` (Brother Test) subsumes the others. A page can pass every individual
tell and still fail this one — which is the real problem the skill addresses.
