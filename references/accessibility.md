# Accessibility

Rules: `a11y-01` … `a11y-04`, plus `motion-12` (reduced motion) and `resp-01` (overflow).

## Position in this skill

> **Accessibility is not a final step. It is part of the design.**

Two of the four rules are P0. Research presented at CHI 2025 showed AI assistants
systematically generate inaccessible markup, and a December 2025 analysis of 470 real
pull requests found AI-generated code carried 1.7× more issues than human code. These
are the most reliably *verifiable* problems in the whole catalogue — and unlike taste,
they have almost no legitimate false positives.

## What to check

| Area | Rule | Failure |
|---|---|---|
| Contrast | `a11y-01` P0 | Light grey on white, thin text over gradients, unmeasured |
| Focus states | `a11y-02` P0 | Outline removed with no replacement, invisible keyboard focus |
| Keyboard interaction | `a11y-02` | Custom controls unreachable or untraversable |
| Reduced motion | `motion-12` | Query absent entirely |
| Hover-only information | `a11y-04` P1 | Tooltips as sole carrier; unreachable on touch/keyboard |
| Error states | `a11y-03` P1 | Never designed |
| Empty states | `a11y-03` | Never designed |
| Loading states | `a11y-03` | Spinner only |
| Responsive overflow | `resp-01` P0 | Horizontal scroll on mobile |
| Text readability | `a11y-01` | Measure too long, size too small, tracking too tight |

## Contrast

**Measure it; do not eyeball it.** Eyeballing fails hardest exactly where generated
UIs live: dark themes and thin type. Use whatever measurement is available in the
environment — a perceptual model (APCA) is more accurate on dark backgrounds and thin
weights than the legacy ratio, but any measurement beats none.

Common misses: placeholder text, helper text, disabled states, text over gradients and
images (needs a scrim), low-contrast borders on dark themes.

Fix precisely. Do not darken everything indiscriminately — that destroys the hierarchy
you are trying to build.

## Focus states (`a11y-02`)

**This rule has no false positives.** Removing the outline with no replacement is never
acceptable on an interactive element.

Test: traverse the entire page with the keyboard alone. Every stop must be visible.
Then integrate the indicator into the design system rather than only restoring a
browser default.

## The states nobody designed (`a11y-03`)

Generated output covers the happy path. Ask of every screen:

- What does this look like with **no data**?
- With a **failed request**?
- While **loading**?
- With **one** item? With **five hundred**?
- With **very long** content — a 60-character name, a 500-word description?

These are the states the product will actually spend time in. Note that adding a
decorative empty-state illustration is not a solution by itself.

## Do not

- treat accessibility as a post-remediation checklist
- add ARIA attributes to paper over incorrect semantics
- darken all text uniformly to pass contrast
- remove tooltips instead of making their content reachable
- claim conformance you have not measured

## Validation

- [ ] Contrast measured and passing for all informational text, in every theme
- [ ] Visible focus indicator at every keyboard stop, integrated into the system
- [ ] Full keyboard operability
- [ ] `prefers-reduced-motion` honoured
- [ ] No information available only on hover
- [ ] Empty, error, loading, disabled states exist and are consistent
- [ ] No horizontal overflow at any tested width
