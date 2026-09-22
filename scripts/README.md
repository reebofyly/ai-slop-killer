# scripts/

**This directory intentionally contains no executable scripts.**

## Why

The skill is stack-agnostic and must not assume the agent has React, Tailwind,
Playwright, Chrome, a local server, a screenshot tool or any particular library
(`SKILL.md` §30 portability requirement).

Any script shipped here would either:

1. assume a runtime (Node, Python, a headless browser) that may not exist, or
2. encode framework-specific patterns (Tailwind class names, React component shapes),
   which would break the abstraction layer that makes the same diagnosis possible
   across stacks, or
3. produce a numeric "slop score" — which the skill explicitly must not do.

Detection here is **judgement applied to evidence**, not regex matching. A grep for
`linear-gradient` with purple stops cannot tell whether the hue is the brand colour;
only phase 5 false-positive validation can, and that requires reading brand assets,
tokens and docs in context.

## What to do instead

Use whatever the environment actually provides, following the tool-availability ladder
in `workflows/audit.md` §3:

| Available | Use it for |
|---|---|
| Shell + grep/ripgrep | Counting distinct radius/shadow/gap values, finding placeholders, `outline:none`, missing reduced-motion queries |
| Package manager / build | Confirming the build still succeeds, running tests |
| Dev server | Loading pages, reading console errors |
| Browser automation | Screenshots at four widths, state and motion inspection |
| Contrast tooling | Measuring rather than eyeballing (`a11y-01`) |
| Existing project linters | Accessibility and style checks already configured |

**Never simulate the output of a tool that does not exist.** If a capability is
unavailable, mark the corresponding tells `not-assessed` in the report and say so.

## Useful ad-hoc probes

These are illustrative one-liners to adapt, not a supported toolchain. Adjust paths and
patterns to the project's actual stack.

```bash
# How many distinct radius / shadow values exist? One of each = comp-01 signal.
rg -o 'border-radius:[^;]+' -r '$0' --no-filename | sort -u | wc -l

# Is reduced motion handled at all? (motion-12)
rg -l 'prefers-reduced-motion'

# Focus states removed with no replacement? (a11y-02)
rg -n 'outline:\s*(none|0)'

# Leftover placeholders and default metadata. (content-03)
rg -in 'lorem ipsum|your@email|555-01|<title>(My App|Create Next App|Vite)'

# Dead links. (layout-06)
rg -n 'href="#"'

# Layout-property animation. (motion-11)
rg -n 'transition:[^;]*\b(width|height|margin|padding)\b'
```

Every hit is a **raw signal only**. It must still pass phase 5 before it counts.
