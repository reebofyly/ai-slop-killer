# Components & surfaces

Rules: `comp-01` … `comp-08`.

## The actual problem

The research is precise: the issue is **the same radius and the same shadow on every
surface**. Card, button, input, image all share one pillow treatment, so nothing
signals importance and nothing signals interactivity. Everything floats identically.

The tell is not "rounded corners". It is **no rule governing which elements get what**.

## Build a surface hierarchy

This is the central remediation of the category. Define levels, then let radius,
border, background and elevation **differ across them**:

```text
page          the base canvas
section       a major region, often just a background shift
surface       a grouped container (card, panel, sheet)
interactive   something that responds (clickable card, list row)
control       button, input, select, toggle
```

Not every level needs the same treatment — that is the entire point. A control and a
page-level container having identical rounding is what flattens the interface.

## Separation ladder (`comp-02`)

Reach for these **in order**, and stop as soon as the grouping reads:

1. **whitespace** — free, always try first
2. **background shift** — a few percent of lightness
3. **elevation** — soft, reserved for genuine layering
4. **border** — only if all three failed

"Cardocalypse" is wrapping text-only blocks in bordered boxes that needed only space.
Nested cards are always a smell.

## Per-rule notes

- **`comp-01` uniform radius/shadow** — P1. Establish radius and elevation scales with
  stated roles. Do not globally sharpen corners or delete all shadows.
- **`comp-03` glassmorphism** — **weak tell**, explicitly cleared by the research as
  standalone evidence. Legitimate over genuinely layered content: sticky navbars over
  scrolling content, modal scrims, media overlays. Suspicious only when applied to
  surfaces with nothing behind them.
- **`comp-04` borders / left strips** — reserve the coloured left strip for real
  semantic state (info/warning/error). Decorative strips on every card are the tell.
- **`comp-05` / `comp-07` icon containers** — the same pastel rounded square on every
  feature, and the oversized circled icon above every section heading. Ask whether the
  container adds meaning.
- **`comp-06` icon semantics** — sparkle=AI, zap=fast, shield=secure, arrow on every
  CTA. Icons chosen by statistical frequency rather than meaning. **The library is
  irrelevant** — never swap Lucide for another set. Remove decorative icons; keep
  clarifying ones.
- **`comp-08` system incoherence** — mixed radius values with no scale, hard-coded
  colours beside tokens, stacked CTAs of differing widths. Consistency is the deliverable.

## False positives

- A documented design system deliberately using one radius, with hierarchy carried by
  colour, weight or spacing instead
- Dashboards and feeds where cards are the correct affordance
- Glass over real layered content
- The coloured strip used semantically
- An established icon-container component used consistently as a system
- Legacy areas mid-migration, with documented exceptions

## Do not

- ban any component library
- swap icon sets
- globally change rounded to sharp
- remove all shadows or all borders dogmatically
- rewrite a working design system
- convert every card into a bento tile

## Validation

- [ ] Radius and elevation scales exist with stated roles per surface level
- [ ] Interactive elements are visually distinguishable from static ones
- [ ] No nested cards; containers only where they group
- [ ] Coloured strips are semantic
- [ ] Every icon has a reason; decorative ones removed
- [ ] Tokens used consistently; sibling controls aligned
