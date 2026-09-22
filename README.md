# ai-slop-killer

A stack-agnostic agent skill that audits an existing frontend for **arbitrary, generic,
repetitive or interchangeable visual choices**, then rebuilds an intentional, coherent
art direction using the technologies the project already uses.

## What it is not

It is **not** a tool to make sites "stop looking AI-generated". That framing produces
mechanical substitutions and a new cliché. It never claims a design was AI-generated —
origin is not knowable from pixels.

## Core rule

```text
Do not replace AI slop with another form of AI slop.

A visual choice is not bad because it is popular.
A visual choice becomes suspicious when it is arbitrary, repetitive,
unjustified, interchangeable, disconnected from the product, applied
uniformly without hierarchy, or used because it is a default rather
than a deliberate decision.
```

## Install

Copy the folder into your agent's skills directory:

```bash
# Claude Code / compatible agents
cp -r ai-slop-killer ~/.claude/skills/

# project-scoped
cp -r ai-slop-killer .claude/skills/
```

For other agents, point them at `SKILL.md` — it is self-contained Markdown with
YAML frontmatter and no runtime dependencies.

## Structure

```text
ai-slop-killer/
├── SKILL.md                  entry point: rules, phases, prohibitions
├── rules/tells.yaml          54 structured rules (the 47 research signs)
├── references/               11 domain guides, loaded on demand
│   ├── visual-tells.md       overview, severity, clustering
│   ├── color.md  typography.md  layout.md  components.md
│   ├── imagery.md  content.md  motion.md  accessibility.md
│   ├── identity.md           Brother Test, motif, the 2026 trap
│   └── remediation.md        concept → stack mapping
├── workflows/                audit → art-direction → remediation → verification
├── tests/scenarios.md        7 scenarios; 6 must produce no/minimal change
└── scripts/README.md         why there are deliberately no scripts
```

## The ten phases

```text
1. Inspect   2. Detect   3. Classify   4. Validate false positives
5. Art direction   6. Prioritize   7. Modify
8. Render    9. Compare   10. Verify
```

No style may be edited before phase 5 is complete.

## Signals, not scores

```text
P0 critical · P1 important · P2 cosmetic

0–1 validated signal  → probably coincidence
2–3 validated signals → several signals present
4+  validated signals → significant concentration
```

A diagnostic heuristic only. Never "this site is 87 % AI-generated".

## Source

Built from the research **"47 signes visuels qu'un site web a été généré par une IA"**
(`signes-visuels-site-IA.html`), preserving its distinctions: weak tells stay weak,
bento grids / glassmorphism / mesh backgrounds / Tailwind / rounded corners / a chosen
purple are explicitly **not evidence**, and the 2026 "tasteful default"
(cream + editorial serif + sage) is itself catalogued as a tell.
