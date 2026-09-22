# Remediation — mapping concepts to the actual stack

This file exists so the **diagnosis stays identical across stacks while the
implementation stays native to each**. That is the skill's final acceptance criterion.

## The abstraction layer

Always diagnose in these concepts. Never in framework class names.

```text
PRIMARY_COLOR   SECONDARY_COLOR   ACCENT_COLOR
SURFACE         TEXT_PRIMARY      TEXT_SECONDARY   BORDER
DISPLAY_FONT    BODY_FONT
RADIUS          SHADOW            SPACING          MOTION
```

## Mapping table

| Stack | Where tokens live | How to change them |
|---|---|---|
| **Tailwind** | theme config / `@theme` block | Edit theme tokens, then use semantic utilities. Do not scatter arbitrary bracket values. |
| **Plain CSS / SCSS** | CSS custom properties on `:root` | Define/extend variables; keep the existing naming convention. |
| **CSS Modules** | shared variables file + local declarations | Shared tokens centrally, component specifics locally. |
| **styled-components / emotion** | the theme object | Extend the theme; components consume via props. Never hard-code. |
| **Vue (SFC)** | existing style system + CSS vars | Respect `scoped`; put tokens where the project already puts them. |
| **Svelte** | existing style system + CSS vars | Same; use `:global` only where the project already does. |
| **Web components** | `:host` custom properties | Expose tokens as custom properties for consumers. |
| **Flutter** | `ThemeData`, `ColorScheme`, `TextTheme` | Change the theme, not individual widgets. |
| **SwiftUI** | environment values / asset catalogue | Colour sets and a typography extension, not per-view literals. |
| **Design-token pipeline** | the token source (JSON/YAML) | Change the source and rebuild. Never edit generated output. |

**If the project has a token layer, change the tokens. If it does not, create the
smallest one the project's conventions allow — in the technology already present.**

## Same diagnosis, different implementation — worked example

Diagnosis (identical for both developers):

```text
identity-01  Brother Test failure          P0
type-01      single family, no hierarchy   P0
comp-01      uniform radius and elevation  P1
motion-01    blanket fade-in-up            P0
```

| | Developer A — React + Tailwind + shadcn | Developer B — Vue + CSS Modules |
|---|---|---|
| `type-01` | Extend the type scale in theme config; assign role-based utilities | Add scale variables to the shared stylesheet; role classes in modules |
| `comp-01` | Radius/shadow scale in theme; vary per surface level in component variants | Radius/shadow variables; apply per level in each module |
| `motion-01` | Remove the shared entrance wrapper; keep one authored moment | Same removal in the existing transition components |
| `identity-01` | Document direction + motif in `DESIGN.md`; apply via the existing component layer | Identical document; apply via the existing component layer |

Neither developer changes framework, styling system or component library.

## Order of operations

1. **Tokens first.** Most P0 identity/hierarchy issues resolve at the token layer and
   propagate everywhere for very little code.
2. **Then shared components.** A radius hierarchy applied in the card and button
   components fixes hundreds of usages.
3. **Then page-level composition.** Hero, rhythm, section weight.
4. **Then local polish.**

This order maximises effect per line changed, which is the point of the
**minimum necessary change** principle.

## Minimum necessary change

> **Change as little code as necessary to achieve a meaningful visual improvement.**

- Do not refactor the whole app if tokens plus a few components suffice.
- Do not change technical architecture without reason.
- Do not migrate framework.
- Do not swap component libraries to obtain a different aesthetic.
- Do not add a dependency to solve an aesthetic problem.
- Do not reformat files you did not need to touch — it destroys the diff's readability.

## Each change needs a recorded reason

Every modification carries a one-line justification in the report:

```text
file — what changed — design reason
```

If the reason reads "looks less AI-generated", **the change is not justified**. Revert
it and find the design reason, or drop it.

## Before/after self-check

Run these against every batch of changes:

- Did I replace a default with another default? (`identity-03`)
- Did I change something popular purely because it was popular?
- Did I preserve every existing brand element?
- Did I add anything decorative that carries no meaning?
- Could I have achieved this with fewer changes?
- Does the result look like *this product*, or like the current template?
