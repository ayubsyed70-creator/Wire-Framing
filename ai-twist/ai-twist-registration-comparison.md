# AI Twist — Registration Screen: AI-Generated vs Hand-Built

Per the activity: *"Generate the Registration screen (web + mobile) from a
prompt with an AI design tool, then critique it for responsive behavior and
WCAG basics by hand and compare against your own Penpot version — note where
the AI skipped a state (empty/error) or failed contrast."*

**Prompt used** (plain-English only, no reference to the hand-built version):
*"Design a registration screen for a job portal website, for both web and
mobile. Include fields for name, email, phone, password, confirm password,
and resume upload, with a register button."*

See `ai-registration-web.png` and `ai-registration-mobile.png` for the raw
output. Hand-built versions for comparison: `registration-web.png` /
`registration-mobile.png` (from the earlier task).

---

## 1. Contrast — measured, not eyeballed

Colors were pulled directly from each version and run through the WCAG
relative-luminance formula (contrast ratio = (L1 + 0.05) / (L2 + 0.05)).
WCAG AA requires **4.5:1** for normal text and **3:1** for large text / UI
components (borders, icons).

| Element | AI-generated | Ratio | Result | Hand-built | Ratio | Result |
|---|---|---|---|---|---|---|
| Register button (text on fill) | white `#ffffff` on gray `#cccccc` | **1.61:1** | **FAIL** | white on dark gray `#4a4a4a` | 8.86:1 | PASS |
| Field label / placeholder text | gray `#aaaaaa` on white | **2.32:1** | **FAIL** | gray `#777777` on white | 4.48:1 | PASS |
| Field border | light gray `#dddddd` on white | **1.36:1** | **FAIL** | gray `#555555` on white | 7.46:1 | PASS |

**All three AI-generated elements fail WCAG AA.** The button is the most
serious — white text at 1.61:1 on a light-gray fill is close to invisible for
anyone with low vision, and borderline unreadable even for typical vision in
bright light. This is also a common AI-design-tool default: light gray is
used as a stand-in for "neutral," but neutral gray-on-gray is one of the
easiest ways to fail contrast without noticing.

## 2. Labels vs. placeholders — an accessibility miss, not just a style choice

The AI version put field labels **only inside the input as placeholder text**
("Full name", "Email address"), with nothing above the field. This fails
WCAG 1.3.1 (Info and Relationships) in practice: placeholder text disappears
the moment someone starts typing, so a screen reader or a user who's
partway through the form loses the field's label entirely. The hand-built
version keeps a persistent label above each field and uses the placeholder
area for a lighter secondary hint, if any — the label never disappears.

## 3. Responsive behavior — the AI version didn't actually restructure

This is the biggest functional gap. The AI's "mobile" version is the desktop
layout scaled down, not redesigned:

| | AI-generated mobile | Hand-built mobile |
|---|---|---|
| Nav links | All 4 links kept, crammed into ~340px at ~5.5pt — illegible, not tappable | Collapsed to a single hamburger icon |
| Illustration | Kept, shrunk to a small box that still eats ~180px of vertical space above the fold | Removed entirely — screen space goes to the form |
| Password / Confirm password | Still side-by-side, ~145px wide each — too narrow to see what's typed | Stacked full-width — each field usable |
| Result | Form doesn't fully fit in the frame without scrolling further than necessary; nav is non-functional at this size | Full form visible with normal scrolling; every element is tappable |

This matches a well-known failure pattern in AI design tools: asked for "web
and mobile," they often generate two *sizes* of the same layout rather than
two different *structures*. Responsive design is about what to cut and
restructure, not just scaling — and that's exactly the step the AI skipped.

## 4. Missing states

The AI generated exactly **one state per screen size** — the empty, default
form. It did not produce, and wasn't asked to produce without a follow-up
prompt:
- An **error state** (e.g. "Passwords don't match", invalid email format,
  required field left blank)
- A **filled/in-progress state**
- A **success/confirmation state** after submitting

This matters because the empty state is the easiest state to design — it's
also the least useful one for catching real problems. A password-mismatch
error, for instance, needs a visible error message *and* still needs to pass
the same contrast check (red error text on white is a common second contrast
failure if not checked separately). None of that surfaced here because the
state was never generated in the first place.

## Summary — what to take from this

| Check | Did the AI need a follow-up prompt to fix it? |
|---|---|
| Contrast (button, labels, borders) | Yes — needs explicit "check WCAG AA contrast" instruction, doesn't happen by default |
| Persistent labels vs. placeholder-only | Yes — needs explicit accessibility instruction |
| True mobile restructuring | Yes — needs explicit "redesign the layout for mobile, don't just resize" instruction |
| Error/empty states | Yes — needs a separate, explicit prompt per state |

**Takeaway:** a single plain-English prompt reliably produces a plausible-
looking *happy-path* screen, but reliably skips accessibility and state
coverage unless asked for by name. Treat AI-generated wireframes as a
starting layout to audit, not a finished deliverable.
