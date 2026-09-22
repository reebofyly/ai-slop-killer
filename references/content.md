# Content

Rules: `content-01`, `content-02`, `content-03`.

Copy is in scope because the research treats it as a visual-system signal: empty copy
produces layouts with nothing to give hierarchy to, and leftover placeholders are the
most objectively verifiable tells in the entire catalogue.

## `content-01` — confident empty copy (P1)

"Transform your workflow." "Built for modern teams." "Unlock your potential."
Grammatically clean, written toward the average of all marketing copy, and describing
no product.

**The test:** after reading the hero, can you name what the product actually does?
If not, the copy was generated to *sound like* a landing page rather than to describe one.

Signals: uplift verbs with no object; no product noun in the headline; a subhead that
restates the headline; no specific, falsifiable claim anywhere.

**False positives** — deliberately broad positioning for a genuine platform; brand voice
validated by the team; copy under legal review constraints.

**Remediation** — say what the product is and who it is for, in specific language.
Do not rewrite into a different generic register, and do not add buzzwords. If you do
not know the product well enough to write specifically, that is an open question for
the team, not a licence to invent.

## `content-02` — default tiers and FAQ boilerplate (P2)

Starter / Pro / Business at round default prices, plus an FAQ whose answers paraphrase
the marketing copy twice.

**False positive** — those genuinely are the plan names and prices. Check before touching.

**Remediation** — reflect the real commercial offer; FAQs should answer questions users
actually ask. Never rename tiers for aesthetic reasons.

## `content-03` — leftover placeholders and metadata (P0)

Lorem ipsum, `your@email.com`, 555 phone numbers, "Company Name", `<title>My App</title>`,
missing Open Graph image, default framework favicon.

This is P0 because it is a **completion failure, not a taste judgement** — and it is the
one category with near-zero ambiguity. Fix it before any aesthetic work
(`workflows/remediation.md` §1, override 1).

Quick check: share the URL in a chat client. No preview card means metadata was never
filled in. Look at the browser tab: a default favicon or generic title is the same signal.

**Remediation** — fill in the real content and metadata. **Never invent plausible fake
content to fill the gaps** — that converts a visible gap into an invisible lie.

## Validation

- [ ] A reader can state what the product does after reading the hero
- [ ] Tiers, prices and FAQ match commercial reality
- [ ] No placeholders anywhere
- [ ] Title, description, OG image and favicon set
- [ ] Nothing was fabricated to fill a gap
