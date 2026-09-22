# Identity

Rules: `identity-01` (meta-signal), `identity-02`, `identity-03`.

## The Brother Test

```text
Hide the logo/brand.

Could this interface belong to another product
without changing its visual system?

Examples:
- CRM
- fintech
- project management tool
- AI SaaS
- developer tool
- analytics dashboard

If yes, the interface may lack visual identity.
```

This is the **meta-signal**. A page can pass every individual tell and still fail this
one — which is the real problem the skill exists to address. The design is not ugly;
it is **anonymous**. It does none of the work of building recognition or trust.

## Critical constraint

> **Failing the Brother Test opens an identity analysis. It does not authorise decoration.**

Failing it means running `workflows/art-direction.md`. It does **not** mean adding
grain, blobs, tilts, mascots, a custom cursor, parallax or an unusual accent colour.
Adding visual complexity to escape the "generic" label is the most common mistake —
the result is not distinctive, it is noise.

The most distinctive products are distinctive through **restraint and consistency**:
fewer decisions, each one intentional, held everywhere.

## How to run it properly

1. Take a screenshot (or read the rendered markup) with the logo and product name masked.
2. Ask whether it could plausibly be each of the six example categories.
3. If yes to three or more → the tell fires.
4. **Then check the false positives** before acting.

## False positives — neutrality is sometimes required

- **Internal tools** deliberately using a corporate or platform design system
- **White-label products** that must stay neutral by design
- Products intentionally built on a public design system (a government service, a
  platform extension, an enterprise suite component)
- Early prototypes explicitly not yet branded

In these cases neutrality is the requirement, not the failure. Report as cleared.

## What identity actually is (`identity-02`)

Not a decoration. A **leitmotif**: one recurring element that belongs to this product
and no other. Candidates, in rough order of durability:

```text
a specific corner/edge treatment held consistently
a distinctive button shape or pressed state
a single owned glyph or mark used as a repeating device
a colour applied with a rule nobody else would apply
a typographic device (a numeral style, a label treatment)
a spatial rhythm (unusual density, an unusual measure)
a texture or material, if it relates to the product
```

**Prefer one dominant signature.** Additional identity elements are legitimate when
each has independent semantic justification, they form a coherent system, they do not
compete unnecessarily, and together they reinforce the identity. For example
`typography + brand colour + a photographic treatment + a small geometric language`
is a system, not clutter — provided it reads as one idea. What fails is four unrelated
devices bolted on to manufacture personality.

Test: could someone recognise a screenshot with no logo? That is the target.

## The 2026 trap (`identity-03`)

The anti-slop reaction produced its own default: **cream background, editorial serif,
sage or terracotta accent, light grain**. Adopting it wholesale swaps one unchosen
default for another and resets the clock.

**Check every remediation this skill produces against this rule.** If the output looks
like the current "tasteful" template rather than like the product, the work failed.

The question is never "does this read as not-AI?" It is **"does this read as this
product?"**

## If the Brother Test fails

```text
do not decorate immediately.
```

Examine where identity could legitimately come from — brand, content, typography,
composition, imagery, tone, product-specific information, existing visual signatures —
then name what is actually missing. Most often the honest answer is
*"the identity that already exists is applied timidly"*, which is **STRENGTHEN**,
not invention.

## Do not

- add decorative elements to manufacture personality
- adopt a fashionable aesthetic wholesale
- introduce grain, blobs, tilts or mascots as identity substitutes
- over-design to compensate for genericness
- confuse "distinctive" with "busy"

## Validation

- [ ] A named direction is documented (not "clean and modern")
- [ ] One motif recurs meaningfully across screens
- [ ] The interface is no longer interchangeable with a different product category
- [ ] Existing brand elements were preserved, not replaced
- [ ] The result does not resemble the current fashionable template
- [ ] Nothing decorative was added that carries no meaning
