# Layout & composition

Rules: `layout-01` … `layout-06`, plus `space-01`, `space-02`, `resp-01`, `resp-02`.

## The actual problem

Composition that follows a **template** rather than the content. The generated page
shell: pill badge → centered H1 → subhead → two CTAs → exactly three feature cards →
1·2·3 steps → three pricing tiers → four-column footer.

Each block can be right. All of them together, in that order, with equal weight
throughout, means the grid decided rather than the content.

## The governing question

> **Is this composition a decision suited to this content?**

Not "is it centered". Centering a short manifesto is correct. Centering a dense
comparison table is not.

## What to examine

### Hero (`layout-01`)
- Does the badge carry real information, or is it decoration?
- Do the two CTAs have genuinely distinct jobs, or is the second one filler?
- Does the subhead add information, or restate the headline?
- Is centering right for this message?

### Feature blocks (`layout-02`)
- Are the three items genuinely equal in importance? Real features rarely are.
- Does the count follow the content, or the grid?
- Is there one item that deserves more room, a screenshot, or its own section?

### Rhythm (`layout-05`)
The most under-detected problem. Every section the same width, same padding, same
alignment produces a monotone scroll with no peaks. Vary density and spacing according
to importance — that is what "tension" means here, not tilted decoration.

### Footer (`layout-06`)
Check that links resolve before restyling anything. Dead links are a completion
failure, not an aesthetic one.

## Spacing

- `space-01` — one gap value everywhere means space is not expressing grouping.
  Proximity is the cheapest hierarchy tool available; use it before borders and cards.
- `space-02` — off-scale magic numbers beside scale values reveal eyeballing.
  **But** genuine optical corrections are legitimate — keep them and comment them.

## Responsive (`resp-01`, `resp-02`)

Check four widths minimum: **mobile · tablet · desktop · wide desktop**.

Look for: horizontal overflow, fixed widths, components too wide, CTAs breaking,
desktop type sizes unchanged on mobile, grids that collapse absurdly, broken
navigation, animations misbehaving, unbounded measure on wide screens.

`resp-01` is P0 because it is **broken function**, not taste. Fix breakage before any
aesthetic work. Never hide content on mobile to make a layout work.

## False positives

- Centered composition suited to a short, single message
- Rigorous grid systems where regularity is the point (documentation, data UI, forms)
- Three items that genuinely are three items
- A conversion-tested layout with actual evidence behind it
- Desktop-only tools with a documented minimum width

## Do not

- force asymmetry
- convert card rows into bento grids mechanically
- decentre a hero because centered reads as generic
- add tilts, overlaps or floating decoration to manufacture tension
- change the item count for visual reasons

## Validation

- [ ] Composition justified by content, not by template
- [ ] Hierarchy visible between sections and between items within a section
- [ ] Vertical rhythm varies with importance
- [ ] Spacing scale exists and expresses grouping
- [ ] Four breakpoints checked, no horizontal overflow, measure comfortable
- [ ] All footer/nav links resolve
