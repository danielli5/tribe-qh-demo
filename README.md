# Tribe x Kaiser Permanente Demo — Cardiology Care Gaps Worklist

An interactive, single-page mockup of the clinician-facing **Population Health worklist** Tribe AI proposes for Kaiser Permanente: a SMART on FHIR app rendered inside Epic Hyperspace, surfacing cardiology care gaps that Claude found in free text (echo reports, discharge summaries, clinic notes) and that KP's coded-data registries cannot see. Built by **Tribe AI** to make the end product tangible during a GM panel presentation.

> **Demo mockup with synthetic data only. Not an Epic or Kaiser Permanente product.**
> Epic, Hyperspace, Healthy Planet, In Basket and related marks are trademarks of Epic Systems Corporation. All patient names, MRNs, dates, and clinical details are fictional. No backend, no real product code, no real patient information.

## Live demo

**https://danielli5.github.io/tribe-qh-demo/**

No install needed. Open the link in any modern browser (desktop, 1280px+ wide). Refresh the page to reset all approvals and dismissals before presenting.

## What it shows

- **Hyperspace-styled worklist** with 16 synthetic patients (heart failure and valvular disease) ranked by risk tier (High / Medium / Watch), with filters and search
- **Patient detail drawer** per patient:
  1. **Why this patient was flagged**: the deterministic, clinician-authored Healthy Planet criterion that fired (e.g. `CG-HF-12: EF <= 40% AND guideline medication held at discharge with a documented restart plan AND no restart order or fill since`)
  2. **AI clinical synthesis**, clearly labeled as model-generated ("AI reads and drafts; it does not decide")
  3. **Evidence trail**: every extracted fact with its verbatim source quote, document, date, provisional SmartData element ID, and a "View source" modal
  4. **Current vs guideline-directed therapy** table
  5. **Actions**: Approve (routes via In Basket, marks SmartData clinician-verified) or Dismiss (reason required, feeds criterion tuning)
- **Governance chrome throughout**: KP Responsible AI badge, model chip (Claude under BAA, zero retention), provisional-vs-verified two-plane write model, audit-trail toasts on every action

## The 60-second demo script

1. Open on the worklist: *"3.4 million adults screened continuously. 51,247 gaps counted in 12 months. Here are the 47 flags for this clinic."*
2. Click **Rosa Gonzalez** (rank 2, High): *"Heart-failure admission in May. Her carvedilol was held for low blood pressure, restart planned at a follow-up that was cancelled twice. Zero fills since. Her med list still shows the drug as active, so every coded query says she is covered. The hold was a click, so it is coded. The restart instruction was a sentence, so it never was."*
3. Click a **"View source"** quote to show the discharge summary passage.
4. **Approve** → route via In Basket → toast: *"SmartData marked clinician-verified, logged to the audit trail."*
5. Point at **Samuel Adeyemi**'s dismissal: *"When the AI is wrong, the dismissal reason feeds back into criterion tuning. Clinician decides, always."*

## Notes on the data

- The synthetic patients are defined in the `P` array near the top of the `<script>` block in `index.html`
- Everything (CSS, JS, data) is embedded in the one file. No build step, no dependencies. State is in-memory only
- Designed desktop-first at 1440px, usable at 1280

---

Built by Tribe AI for illustration.
