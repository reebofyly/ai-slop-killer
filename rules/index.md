# Tell index — compact triage layer

Load this FIRST. It is the whole catalogue in ~1.5k tokens.
Load the full rule (signals, false_positives, diagnostic_questions, remediation,
avoid, validation) from `rules/tells.yaml` **only for the categories you are actually
working in**. Never load the whole YAML upfront.

`W` = weak tell: never counts alone, only inside a cluster.

## Before using this table

> **This is an observation catalogue, not a list of things to delete.**

A row firing means *look here*, never *fix this*. Every hit must pass:

```text
observation → diagnosis → context validation → false positive?
→ disposition (KEEP / STRENGTHEN / MODIFY / REMOVE) → decision
```

`KEEP` and `STRENGTHEN` are normal, frequent outcomes on real projects.
Never `REMOVE` on low confidence. See `SKILL.md` §2–§3 (normative).

| id | sev | name | fires when |
|---|---|---|---|
| `color-01` | P0 | default-purple-indigo-gradient | gradient hue appears in no owned asset or named token |
| `color-02` | P1 | gradient-clipped-headline-text | gradient clipped onto heading text, not systematised |
| `color-03` | P0 | reflex-dark-mode | dark-only theme, no product reason, untuned neutrals |
| `color-04` | P1 | neon-on-dark-glow | glow/neon on non-interactive surfaces |
| `color-05` | P1 | untouched-framework-palette | framework default palette never overridden anywhere |
| `type-01` | P0 | single-neutral-sans-everywhere | one family everywhere AND no real scale |
| `type-02` | P1 | flat-type-scale-and-weight | evenly-multiplied sizes, 2 weights, uniform leading |
| `type-03` | P1 | one-word-styled-differently-in-headline | one heading word styled differently, no rule behind it |
| `layout-01` | P0 | templated-centered-hero | badge + centered H1 + subhead + 2 CTAs template |
| `layout-02` | P0 | exactly-three-equal-feature-cards | exactly 3 equal-weight feature cards |
| `layout-03` | P2 W | numbered-three-step-row | 1·2·3 numbered step row echoing another triptych |
| `layout-04` | P2 W | three-tier-pricing-middle-highlighted | 3 pricing tiers, middle ringed/scaled/badged |
| `layout-05` | P1 | total-symmetry-no-tension | every section same width, padding, alignment |
| `layout-06` | P2 | generic-four-column-footer | generic 4-col footer, dead or "#" links |
| `comp-01` | P1 | uniform-radius-and-shadow-on-every-surface | one radius + one shadow value across all surfaces |
| `comp-02` | P1 | cardocalypse | text-only blocks wrapped in cards; nested cards |
| `comp-03` | P2 W | reflex-glassmorphism | blur applied where nothing is behind it |
| `comp-04` | P1 | uniform-1px-border-or-colored-left-strip | identical 1px border everywhere, or decorative left strip |
| `comp-05` | P2 | icon-in-pastel-rounded-square | same pastel icon container on every feature |
| `comp-06` | P2 | default-icon-semantics | sparkle=AI, zap=fast, arrow welded to every CTA |
| `comp-07` | P2 | oversized-centered-section-icon | same circled icon above every section heading |
| `comp-08` | P1 | inconsistent-system-logic | mixed radii with no scale, hardcoded colors beside tokens |
| `space-01` | P2 | flat-uniform-spacing | one gap/padding value app-wide, no grouping |
| `space-02` | P2 W | arbitrary-off-scale-values | off-scale magic numbers beside scale values |
| `img-01` | P1 | placeholder-and-generated-imagery | gradient block where a screenshot belongs; auto-avatars |
| `img-02` | P2 | plastic-3d-blobs-and-isometric-illustration | floating 3D blobs / plastic isometrics, no referent |
| `img-03` | P1 | fabricated-product-mockup | fake dashboard with invented round metrics |
| `img-04` | P0 | generated-image-artifacts | warped text in image, incoherent shadows/reflections |
| `img-05` | P1 | greyed-blurred-logo-wall | "Trusted by" logos, no links, no case studies |
| `img-06` | P1 | generic-testimonials | 3 identical-length 5-star quotes, generated avatars |
| `content-01` | P1 | confident-empty-copy | cannot name what the product does after the hero |
| `content-02` | P2 | default-tier-and-faq-boilerplate | Starter/Pro/Business at round default prices |
| `content-03` | P0 | leftover-placeholders-and-metadata | lorem ipsum, default <title>, no OG, default favicon |
| `identity-01` | P0 | brother-test-failure | META. Logo hidden → could be any other product |
| `identity-02` | P1 | no-visual-leitmotif | nothing recurs that belongs to this product |
| `identity-03` | P1 | the-2026-tasteful-default | cream + editorial serif + sage adopted wholesale |
| `motion-01` | P0 | identical-fade-in-up-everywhere | same fade-in-up on everything, one curve, one distance |
| `motion-02` | P2 | linear-stagger-delays | stagger = index * constant |
| `motion-03` | P0 | page-load-triggered-instead-of-scroll | below-fold animations fire on page load |
| `motion-04` | P2 W | single-entrance-direction | everything enters from the same direction |
| `motion-05` | P1 | bounce-elastic-easing-on-ui-chrome | overshoot/elastic easing on modals, menus, cards |
| `motion-06` | P1 | fake-live-status-pulse | status dot pulses with no data source behind it |
| `motion-07` | P2 W | decorative-blinking-caret | fake caret / typewriter in marketing copy |
| `motion-08` | P1 | infinite-logo-marquee | infinite logo marquee, no controls, no pause |
| `motion-09` | P2 W | gratuitous-image-hover-transform | scale/rotate hover on non-interactive images |
| `motion-10` | P1 | hover-opacity-only-or-no-states | hover = opacity only; no :active; buttons snap |
| `motion-11` | P1 | layout-property-animation | transition on width/height/margin/padding |
| `motion-12` | P1 | reduced-motion-ignored-and-no-page-transition | no prefers-reduced-motion anywhere |
| `a11y-01` | P0 | insufficient-contrast | informational text below contrast threshold, unmeasured |
| `a11y-02` | P0 | missing-focus-states | outline:none with no replacement; focus invisible |
| `a11y-03` | P1 | missing-error-empty-loading-states | no empty / error / loading / disabled states |
| `a11y-04` | P1 | hover-only-information | info reachable only on hover |
| `resp-01` | P0 | mobile-never-reviewed | horizontal overflow, broken nav at small widths |
| `resp-02` | P1 | unscaled-typography-and-collapsing-grids | desktop type on mobile; unbounded measure on wide |

## Loading protocol

```text
1. Read this index (you are here).
2. Inspect the project (workflows/audit.md §1).
3. Note which ids plausibly fire.
4. Load ONLY those categories from rules/tells.yaml.
5. Load the matching references/<category>.md only when remediating it.
```

Grep a single rule without loading the file:

```bash
awk '/^  - id: comp-01$/,/^  - id: /' rules/tells.yaml | head -n -1
```

## Never evidence on their own

Tailwind · React · Next.js · shadcn · Lucide · Inter · rounded corners · dark mode ·
purple · gradients · glassmorphism · bento grids · mesh/aurora backgrounds.
