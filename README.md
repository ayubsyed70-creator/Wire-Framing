# Wireframing Practice — Checkmate BA Training (Session 9)

This repo tracks wireframing practice from the "Hands-On Activity" in
Session 9 (Design Wireframing), Checkmate IT Training Institute BA Program.

## Activity tasks
1. **Registration screen** — Web & Mobile, responsive thinking ✅
2. **JRP candidate-facing screens** — Job Search, Job Details, Apply for Job, My Applications, Candidate Profile ✅
3. **Company site wireframes** — Home, About Us, Team, Services, Contact Us — exported to PDF ✅
4. **AI Twist** — generated the Registration screen with an AI design tool, critiqued for contrast/labels/responsiveness/missing states, compared against the hand-built version ✅

## Structure

```
Wire-Framing/
├── README.md
├── registration/
│   ├── registration-web.png       Registration screen — web (1200px)
│   └── registration-mobile.png    Registration screen — mobile (375px)
├── notes/
│   └── registration-responsive-notes.md   What changes web→mobile, and why
├── jrp/
│   ├── 01-job-search.png
│   ├── 02-job-details.png
│   ├── 03-apply-for-job.png
│   ├── 04-my-applications.png
│   ├── 05-candidate-profile.png
│   └── jrp-candidate-screens-overview.md
├── company-site/
│   ├── company-01-home.png
│   ├── company-02-about.png
│   ├── company-03-team.png
│   ├── company-04-services.png
│   ├── company-05-contact.png
│   ├── brightline-company-site-wireframes.pdf
│   └── company-wireframes-overview.md
└── ai-twist/
    ├── ai-registration-web.png
    ├── ai-registration-mobile.png
    └── ai-twist-registration-comparison.md   WCAG contrast ratios, missing states, responsive-restructuring gaps
```

## AI Twist — key findings

- AI-generated button/label/border colors all **failed WCAG AA contrast**
  (measured, not eyeballed — see `ai-twist/ai-twist-registration-comparison.md`
  for exact ratios)
- Field labels were placeholder-only (disappear on typing) — an accessibility miss
- "Mobile" version was the desktop layout scaled down, not restructured
- No error, filled, or success states were generated — only the empty default

## Tools

These wireframes are low-fidelity mockups. For the actual assignment
submission, recreate them in **Penpot** or **Figma** as the brief requires —
this repo is for tracking practice/drafts and version history, not a
replacement for the design-tool file.
