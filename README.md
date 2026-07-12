# Tribe QH Demo — "Care Census" Worklist Mockup

An interactive, single-page mockup of the clinician-facing **Worklist UI ("cardiology census")** of the [Qualified Health](https://qualifiedhealthai.com) platform, as deployed at UTMB's Sealy Heart and Vascular Institute. Built by **Tribe AI** to make the end product tangible during a GM panel presentation.

> **Demo mockup with synthetic data only. Not a Qualified Health product.**
> All patient names, MRNs, dates, and clinical details are fictional. No backend, no real product code, no real patient information.

## Live demo

**https://danielli5.github.io/tribe-qh-demo/**

No install needed — open the link in any modern browser (desktop, 1280px+ wide). Refresh the page to reset all approvals/dismissals before presenting.

## What it shows

Modeled on the Anthropic case study of Qualified Health at UTMB: cardiologists log in and see a census of patients pre-screened by AI for optimization opportunities in heart-failure and valvular disease, with every AI-surfaced finding traceable back to source data.

- **Census worklist** — 16 synthetic patients (10 heart failure, 6 valvular) ranked by risk tier (High / Medium / Watch), with filters, search, and sorting
- **Patient detail drawer** — six sections per patient:
  1. Patient header (demographics, care team, risk tier)
  2. **Why this patient was flagged** — the deterministic, clinician-authored rule that fired (e.g., `CG-HF-04: EF ≤ 40% AND no beta-blocker AND no contraindication`)
  3. **AI clinical synthesis** — plain-language summary, clearly labeled as model-generated ("AI reads and drafts; it does not decide")
  4. **Evidence trail** — every extracted fact with its verbatim source quote, document name, date, and a "View source" modal
  5. **Current vs. guideline-recommended therapy** — every recommendation is clickable and opens the guideline passage it is based on
  6. **Actions** — Approve (with care-team routing) or Dismiss (reason required); both update live state and fire audit-trail toasts
- **Governance chrome throughout** — "HIPAA · All actions logged" badge, model chip, "AI-extracted" tags, mandatory dismissal reasons, faux audit-log entries on every action

## Running it locally

Use the [live demo link](https://danielli5.github.io/tribe-qh-demo/) above, or open [`index.html`](index.html) directly — no build step, no dependencies:

```
start index.html        # Windows
open index.html         # macOS
```

Everything (CSS, JS, data) is embedded in the one file. Designed desktop-first at 1440px; usable at 1280.

State is in-memory only — refresh the page to reset all approvals/dismissals before presenting.

## The 60-second demo script

1. Open on the census: *"Every patient at UTMB, screened continuously — here are the 312 the rules surfaced, ranked by risk."*
2. Click **Margaret Okafor**: *"The rule that flagged her is deterministic and clinician-authored — EF 28%, no beta-blocker. Claude read her chart and synthesized why she matters — and every fact links to the exact sentence in the source document."*
3. Click a **"View source"** quote to show the highlighted passage.
4. **Approve** → route to cardiology follow-up → toast: *"logged to the audit trail."*
5. Point at **Samuel Adeyemi**'s dismissal: *"And when the AI is wrong, the dismissal reason feeds back into tuning. Clinician decides, always."*

## Notes on the data

- Distribution: 4 High / 7 Medium / 5 Watch; 12 New, 2 In review, 1 Approved, 1 Dismissed
- Guideline references are generic, clinician-authored "appropriateness criteria" excerpts — no real guideline citation numbers are fabricated
- The synthetic patients are defined in the `PATIENTS` array and the guideline excerpts in the `GUIDELINES` object, both near the top of the `<script>` block in `index.html`

---

Built by Tribe AI for illustration.
