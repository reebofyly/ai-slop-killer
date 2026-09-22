# Imagery

Rules: `img-01` … `img-06`.

## The governing principle

> **Prefer the project's real assets. If none exist, show less rather than fake more.**

Most imagery tells are **trust problems before aesthetic problems**. A fabricated
dashboard, an unverifiable logo wall and invented testimonials are claims, not styling.
Restyling them while leaving the claim false is the wrong fix.

## Always check first

Search the repository before concluding anything is missing:

```text
public/ static/ assets/ src/assets/ media/ images/ .storybook/
brand/ design/ press/ docs/ README screenshots
```

Real screenshots, logos and photography frequently exist and simply are not used on the
page being audited. **Never replace a real brand identity with generic artwork.**

## Per-rule notes

- **`img-01` placeholders & generated imagery** (P1) — gradient blocks where a
  screenshot belongs, auto-generated vector avatars, interchangeable stock. Legitimate
  when: illustration is a deliberate owned part of the brand, or stock is consistently
  art-directed.
- **`img-02` 3D blobs & plastic isometrics** (P2) — floating iridescent shapes and
  too-smooth isometric scenes with no referent. Legitimate as an owned, consistent
  illustration system.
- **`img-03` fabricated product mockup** (P1) — a glassy fake dashboard with invented
  round metrics instead of the real UI. Use a real screenshot, or present the feature
  without fabricated proof. **Do not regenerate a nicer fake.**
- **`img-04` generated-image artifacts** (P0) — see below.
- **`img-05` logo wall** (P1) — desaturated logos, no links, no case studies. Verify
  the customers are real. Muted styling is a normal convention and not itself a tell.
- **`img-06` testimonials** (P1) — exactly three, identical length, uniform five stars,
  auto-generated avatars, no company or link. Use real attributed quotes or remove.

## Detecting generated imagery in 2026 (`img-04`)

**Fingers are no longer reliable.** Current models render hands correctly most of the
time. What still fails:

| Check | What to look for |
|---|---|
| **Text inside the image** | Warped letters in signage, badges, mocked UI, product labels. Still the strongest single tell. |
| **Light coherence** | Shadows pointing in different directions; an object with no shadow beside one with a firm shadow. |
| **Reflections** | Glass, mirrors, sunglasses showing something that does not match the scene. |
| **Focal plane** | Blur by subject *importance* rather than by depth. |
| **Texture repetition** | Tiling foliage, duplicate faces in crowds, the same defect twice. |
| **Uncanny correctness** | No boring areas — hyper-detail everywhere at once, pores and grain all equally sharp. |
| **Provenance** | C2PA / Content Credentials, SynthID, EXIF. Presence is evidence; **absence proves nothing** (metadata is stripped by screenshots, resizing and uploads). |

**Critical constraint:** report these as *artifacts observed*, never as
"this image is AI-generated". Origin is not provable from pixels. And if you did not
actually open and inspect the image, mark it `not-assessed`.

Generated imagery is also perfectly legitimate when it is **disclosed and intentional**
— a deliberate part of the product's visual identity.

## Where real assets matter most

Anywhere the image supports a **trust claim**: people (team, testimonials), the product
itself (screenshots, demos), and proof (customers, results, certifications). Decorative
background imagery carries far lower stakes.

## Do not

- generate replacement AI illustrations
- add decorative blobs, grain or abstract shapes to fill space
- replace an existing brand illustration system with something more fashionable
- restyle an unverifiable claim instead of resolving it
- assert an image's origin as fact

## Validation

- [ ] Real project assets used wherever they exist
- [ ] Product visuals correspond to the actual UI, or are removed/labelled
- [ ] Trust claims (logos, testimonials) are attributable or removed
- [ ] No fabricated proof introduced
- [ ] No new generic artwork added
