---
type: zone
summary: "The evidence base: 10 independent research reports plus an advisor synthesis, ~19,800 words and ~200 cited sources across English, Chinese, and Tibetan."
tags: [research, evidence, provenance]
status: seeded
created: 2026-08-28
updated: 2026-08-28
verifiedAt: unverified
owns:
  routes: []
  testids: []
  globs: ["research/**"]
  tools: []
depends: []
invariants:
  - rule: "every material claim carries a source URL and a [FACT]/[CLAIM]/[SPECULATION] tag"
    enforcedBy: ["research/00-SYNTHESIS.md"]
  - rule: "reports are frozen evidence, not living docs — corrections go in new notes"
    enforcedBy: ["research/00-SYNTHESIS.md"]
skills: []
advances: []
related: [[not-a-sakya-project]], [[unreadable-manuscript-benchmark]], [[tengyur-triage]]
sources: []
---

## What this is

Ten research reports produced 2026-08-27 by independent Grok-4.6 agents running at `xhigh`
effort in isolated git worktrees, each answering one slice of the question "is there a real
open-source project here," plus an advisor synthesis reconciling them.

Every agent was instructed that a truthful negative finding is a successful result. Nine of
ten returned one.

| File | Slice | What it settles |
|---|---|---|
| `00-SYNTHESIS.md` | Advisor reconciliation | The verdict and the three options |
| `01-claim-provenance.md` | Where 84,000 and 95% come from | Traces both to 2003 Xinhua and to nothing, respectively |
| `02-holdings-catalogue.md` | What Sakya actually holds | Composition, unicum estimate, Sanskrit palm-leaf reality |
| `03-sakyalibrary-com.md` | The website | Different institution, 784 etexts, already mirrored |
| `04-digitization-landscape.md` | Who has scanned what | BDRC backbone; Sakya wall public images ≈ zero |
| `05-translation-orgs.md` | Human translation ecosystem | 84000 at 50% Kangyur; Tengyur target 2110 |
| `06-ai-mt-state.md` | Can AI translate classical Tibetan | Useful for triage; fluent-wrong on unknown text |
| `07-ocr-pipeline.md` | Image → text | Uchen solved, umê collapses, gold-on-dark unmeasured |
| `08-github-oss-survey.md` | Existing open source | Every layer occupied; named gaps listed |
| `09-access-law-politics.md` | Rights, permits, ethics, risk | Unreachable; lineage restrictions; human risk |
| `10-frontier-and-demand.md` | Real unknowns and real users | Drepung precedent; segmented demand; failure modes |

## Anchors

`research/` — eleven markdown files. Frozen as of 2026-08-27.

## Invariants

Reports are evidence, not documentation. They record what was true and citable on their
research date. Corrections and updates belong in new vault notes that link back, not in edits
to the reports — the provenance is the point.

## Lineage

Commissioned to answer one question: is an open-source project for translating unknown
manuscripts a real need, or already solved? Answer recorded in [[not-a-sakya-project]];
surviving directions in [[unreadable-manuscript-benchmark]] and [[tengyur-triage]].
