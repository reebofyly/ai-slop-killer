# Color

Rules: `color-01` … `color-05`.

## The actual problem

Not "purple is bad". The problem is a palette **nobody decided**: hues that appear in
no owned asset, gradients with no semantic job, framework defaults never overridden,
and an accent applied uniformly so it stops meaning anything.

Origin of the most common case: one framework shipped an indigo default, it became the
statistical median of training data, and it is now what a model reaches for absent
direction. That history explains the frequency — it does not make the colour wrong.

## Before touching anything — clear the false positives

Search the repo for evidence the colour was chosen:

- brand/design-system files, `DESIGN.md`, style guide, Figma links in the README
- logo, favicon, OG image, existing illustrations — do they contain the hue?
- marketing site, app store listing, existing print or social assets
- token definitions with names (a named token is a decision; a hex inline is not)
- git history showing deliberate iteration on colour

**If the hue appears in an owned asset or a named token → cleared.** Report and move on.

## Semantic roles to establish

Diagnose and remediate in concepts, never in class names:

```text
PRIMARY_COLOR     the brand's principal colour
SECONDARY_COLOR   supporting, optional
ACCENT_COLOR      scarce — marks the single most important action
SURFACE           page / raised / sunken levels
TEXT_PRIMARY      body and headings
TEXT_SECONDARY    metadata, labels, helper text
BORDER            separation where whitespace is insufficient
```

Plus state colours only if the product needs them: success / warning / danger / info.

**Scarcity is what makes an accent work.** If everything is accented, nothing is.

## Practical guidance

- Cap active hues at roughly three plus a neutral ramp. More hues, less meaning.
- Tune the neutral ramp. Default greys on a dark theme are the single most common
  "nobody decided" signal, and they are also where contrast quietly fails.
- A gradient must answer: what does the transition express? Depth, state, temperature,
  progress? "It looks nice" is a valid answer only if it recurs as a system.
- `color-02` (gradient-clipped headline text) is the same question applied to type:
  a gradient on one heading word is decoration unless the treatment is systematised
  with a stated rule. Carry emphasis through hierarchy first — scale, weight, space —
  and check contrast if the effect stays.
- Measure contrast; do not eyeball it. Dark themes and thin type are where eyeballing
  fails most (see `references/accessibility.md`).

## Do not

- replace purple with beige, sage, terracotta, or any current "tasteful" palette —
  that is tell `identity-03`, the 2026 default, and it resets the clock
- introduce a random accent because the old one felt generic
- remove gradients as a category
- flatten to grayscale to appear restrained
- pick a palette from a trend gallery rather than from the product

## Validation

- [ ] Every colour is a named token with a stated role
- [ ] Accent usage is scarce and intentional
- [ ] Palette relates to brand or to a documented direction
- [ ] Contrast measured and passing for all informational text
- [ ] The result is not the current fashionable palette adopted wholesale
