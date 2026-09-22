# Workflow — Remediation (phases 6–7)

Covers: Prioritize → Modify. Requires a completed audit, a written art direction,
**and the user's approval of that direction** (`workflows/art-direction.md` §8).

---

## §0 — Safety preflight

Before the first edit:

```text
1. Working tree clean?   → if not, ask before touching anything
2. VCS repo?             → work on a dedicated branch
3. Build passes NOW?     → capture the baseline for comparison
4. Tests exist?          → run them now, not only at the end
```

```bash
git status --porcelain              # empty, or stop and ask
git checkout -b design/art-direction
git rev-parse HEAD                  # rollback point
```

**Never commit on the user's behalf unless asked.** Leave the work reviewable and
revertible in one command. If there is no VCS, say so before editing and keep the diff
smaller still.

If the user does want commits: one per batch, never one giant commit, each message
carrying the design reason.

```text
design(tokens): establish semantic colour roles and type scale
design(components): introduce surface elevation hierarchy
fix(a11y): restore visible focus indicators
```

---

## §1 — Prioritize

Only **confirmed** signals (survived false-positive validation) are eligible.

```text
P0  → identity
    → hierarchy
    → structure
    → major visual signals
    → major motion problems

P1  → components
    → imagery
    → spacing
    → interaction

P2  → cosmetic details
    → micro-animations
    → polish
```

**A structural problem is handled before a small border-radius correction.**

### Two overrides

1. **Broken function first.** `resp-01` (mobile overflow/breakage), `a11y-02` (no focus
   states), `content-03` (leftover placeholders) and dead links are failures of
   completion, not taste. Fix them before any aesthetic work.
2. **Highest leverage first within a tier.** A token-level change that propagates
   everywhere beats twenty local edits. See the order in `references/remediation.md`.

### Stop conditions

Stop and report rather than pushing on when:

- confirmed signals are 0–1 (coincidence — say so, change nothing)
- the project has a strong existing direction and needs only consistency notes
- the direction depends on product knowledge you do not have
- fixing a tell would require architectural change
- the high-impact changes are done and the rest is churn

**"This is mostly fine, here are three things" is a valid and frequently correct output.**

### Do not do everything

Start with high-impact problems. A short, well-justified diff that fixes the P0s is a
better outcome than a sweeping refactor. If the remaining P2s are not worth the churn,
list them as "noted, not changed" in the report.

---

## §2 — Modify

### The four binding constraints

1. **Minimum necessary change** — as little code as necessary for a meaningful
   improvement. No framework migration, no library swap, no architecture rewrite, no
   new dependency, no incidental reformatting.
2. **Native to the stack** — implement through the project's own token layer,
   conventions and component system (`references/remediation.md`).
3. **A design reason per change** — recorded. "Looks less AI-generated" is not a
   reason; if that is the only justification, drop the change.
4. **No mechanical substitutions** — the forbidden list below.

### Forbidden mechanical substitutions

Never perform these *because they are supposedly "less AI"*:

```text
Inter → Instrument Serif
purple → sage
gradient → grain
cards → bento
rounded-2xl → rounded-md
Lucide → another icon set
fade-in-up → another animation
```

### Never

```text
- ban Tailwind, React, Next.js, shadcn, Inter, purple, gradients,
  rounded corners, glassmorphism, Lucide
- force serif typography
- force asymmetry
- force bento grids
- add grain everywhere
- add animations everywhere
- add decorative blobs
- add random illustrations
- rewrite the application architecture
- replace a working design system without reason
- claim a design was AI-generated based only on visual patterns
```

### Recommended sequence

Work in small, reviewable batches; verify between them.

1. **Broken function** — overflow, focus states, placeholders, dead links
2. **Tokens** — colour roles, type scale, radius/shadow/spacing scales
3. **Shared components** — surface hierarchy in card/button/input/section header
4. **Composition** — hero, section rhythm, feature weighting
5. **Motion** — reduced motion, then honesty, then technique, then intent, then polish
   (order in `references/motion.md`)
6. **Imagery** — swap in real assets; remove fabricated proof
7. **Polish** — P2 items, only if they are worth the diff

### Per-change record

```text
file — what changed — design reason
```

Accumulate these; they become the "Changes" section of the report.

### Continuous self-check

After each batch, before moving on:

- Did I replace a default with another default? (`identity-03`)
- Did I add anything decorative that carries no meaning?
- Did I preserve every existing brand element?
- Does this still look like *this product*, rather than the current template?
- Could this have been achieved with fewer changes?
- Did I touch anything the art direction's "do not introduce" list forbids?

If any answer is wrong → revert that change before continuing.

---

## §3 — Things to leave alone

Actively resist changing:

- cleared false positives — even when they still *look* generic to you
- working functionality
- architecture, build setup, dependency graph
- files unrelated to the confirmed signals
- brand assets
- code style and formatting outside the edits themselves

A clean, minimal, reviewable diff is part of the deliverable.

---

## Exit criteria

- [ ] Only confirmed signals were remediated
- [ ] Every change has a recorded design reason
- [ ] No forbidden substitution performed
- [ ] No new dependency, no migration, no architecture change
- [ ] Cleared false positives untouched
- [ ] Changes implemented natively in the project's stack
- [ ] Diff is minimal and readable

→ Proceed to `workflows/verification.md`.
