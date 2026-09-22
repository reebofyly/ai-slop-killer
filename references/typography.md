# Typography

Rules: `type-01`, `type-02`, `type-03`.

## The actual problem

> **"Inter is banned" is the wrong reading of the research.**

The research identifies **one family doing every job with no hierarchy** — display at
64px and legal text at 11px indistinguishable apart from size. Inter with a strong
scale is fine. Inter with no scale is the problem.

**Never automatically replace Inter, Roboto, Geist, Poppins or system-ui.** Forcing an
editorial serif is tell `identity-03` — the 2026 default, one cliché for another.

## Treat these as separate concerns

Audit each independently; they fail independently.

| Concern | Failure mode | Fix direction |
|---|---|---|
| font family | one family everywhere by default | decide it; pairing optional |
| font pairing | none, or a trendy pairing copied | only if it serves the content |
| font size | evenly-multiplied steps | contrast in the scale |
| font weight | only 400/600 | weights with assigned roles |
| line height | identical everywhere | tighter for display, looser for body |
| letter spacing | untouched | tighten display, open small caps/labels |
| display hierarchy | H1/H2/H3 nearly identical | clear jumps between levels |
| body hierarchy | lead vs body vs small undifferentiated | define each role |
| labels | styled as small body text | own treatment (size, weight, tracking, colour) |
| metadata | same as body | de-emphasised deliberately, still legible |

## Abstraction

```text
DISPLAY_FONT   headings, hero, numerals if featured
BODY_FONT      running text, UI
```

They may be the same family. What matters is that the **roles exist and differ visibly**.

## Diagnostic

1. Screenshot a page, blur it. Can you still find the most important element?
   If everything is the same grey mass → no hierarchy.
2. Are there more than two weights, and does each have a job?
3. Does line-height differ between a 48px heading and 16px body? It must.
4. Is there a documented scale, or are sizes ad hoc per component?

## False positives

- A deliberate single-typeface system with a rigorous scale — a legitimate and
  demanding direction (Swiss/neo-grotesque). Executed well, it is not slop.
- The brand typeface happens to be a neutral sans.
- Performance budgets limiting font payload — a real engineering constraint.
- A dense data product where uniformity aids scanning.

## Remediation order

1. **Establish the scale first.** Hierarchy before family. This alone resolves most cases.
2. Assign roles: display / lead / body / label / metadata / code.
3. Tune leading and tracking per role.
4. **Only then**, if the content genuinely calls for it, consider a second face.

A pairing is optional. Hierarchy is not.

## Do not

- swap the family because it is popular
- add a display serif to signal taste
- introduce a font dependency to solve a hierarchy problem
- adopt the current fashionable pairing wholesale

## Validation

- [ ] Documented type scale with named roles
- [ ] Display and body visually distinguishable beyond size
- [ ] Line-height and tracking differ by role
- [ ] Blur test: the page's most important element still reads
- [ ] No family change made without a stated content reason
