# Motion

Rules: `motion-01` … `motion-12`. The largest single category.

## The governing rule

```text
Motion should communicate state, not simulate life.
```

A model can write the *syntax* of an animation but cannot *calibrate* it. The result is
movement with no intent — detectable in a single scroll. The measured difference between
generated and authored motion is entirely in **curves, durations and amplitudes**, at
identical technical implementation.

## The counter-principle

> **One authored moment, not scattered identical entrances.**

The opposite of slop motion is **not more animation**. It is usually less animation,
placed where it carries information.

## The two failure poles

Generated frontends fail at one of two extremes, and both appear in the catalogue:

| Over-animation | Under-animation |
|---|---|
| `motion-01` same fade-in-up on everything | `motion-10` hover changes opacity only |
| `motion-05` bounce on modals and cards | `motion-10` no active/pressed state |
| `motion-06` fake status pulse | `motion-12` no page transition at all |
| `motion-08` infinite logo marquee | missing focus transitions |
| `motion-09` gratuitous image zoom | buttons that snap |

Diagnose which pole the project sits at before remediating — the fixes are opposite.

## The four places motion fails

1. **Page load** — default is all-at-once (`motion-01`, `motion-02`). Hierarchy, not uniformity.
2. **Scroll** — default fires below-fold animations on load, so they finish unseen
   (`motion-03`). Trigger on viewport entry, slightly early.
3. **Hover/press** — default is opacity, or nothing (`motion-09`, `motion-10`).
   Real states carry information about what will happen.
4. **Navigation** — default is nothing, or a wrapper fade through blank (`motion-12`).

## Fake life (`motion-06`, `motion-07`, `motion-08`)

A distinct and serious sub-family: animation that **implies data that does not exist**.
A pulsing "all systems operational" dot on a static export claims live telemetry.
A blinking caret claims a terminal. An infinite marquee claims activity. These are
honesty problems as much as taste problems.

## Technique (`motion-11`)

- Animate **`transform` and `opacity`**. These composite on the GPU.
- Animating `width`, `height`, `padding`, `margin` causes reflow and visible jank —
  a performance defect, not only a taste issue.
- Height changes have modern performant techniques; use the one native to the stack.

## Accessibility (`motion-12`)

**Always honour `prefers-reduced-motion`** (or the platform equivalent). It is a few
lines and it is non-negotiable. Marquees and autoplaying motion must stop under it.

## False positives

- A deliberate minimal motion system with one documented entrance, restrained
- Spring physics on genuinely **draggable or gesture-driven** elements — correct there
- A real ticker for genuinely live data, with controls
- Gallery/product hover zoom that previews an action
- Touch-first products where hover is irrelevant — **but active states must still exist**
- Regular stagger on data-driven or virtualised lists

## Do not

- swap `fade-in-up` for a different universal animation
- add motion to appear intentional
- add cinematic page transitions as a fix
- introduce a motion library the project does not already use
- randomise stagger delays programmatically
- remove all easing and make motion instant

## Remediation order

1. Fix accessibility: `prefers-reduced-motion`, focus transitions (`motion-12`, `motion-10`)
2. Fix honesty: fake pulses, carets, marquees (`motion-06`, `motion-07`, `motion-08`)
3. Fix technique: layout-property animation (`motion-11`)
4. Fix intent: reduce blanket entrances to one authored moment (`motion-01`, `motion-03`)
5. Polish: stagger rhythm, direction, easing curves (`motion-02`, `motion-04`, `motion-05`)

## Validation

- [ ] `prefers-reduced-motion` honoured globally
- [ ] Entrance motion reduced to where it carries meaning
- [ ] Below-fold motion triggers on scroll, without a new dependency
- [ ] No animation implies data that does not exist
- [ ] Only `transform`/`opacity` on the main path; no jank
- [ ] Every interactive element has hover, focus, active, disabled
- [ ] Springs only on physical/gesture-driven elements
