---
type: decision
summary: "This repo is not about Sakya Monastery. The viral 84,000/95% claim is false, the corpus is unreachable, and the real frontier is elsewhere."
tags: [scope, provenance, sakya]
status: active
created: 2026-08-28
updated: 2026-08-28
decided: 2026-08-28
supersededBy: ""
zones: [[research-corpus]]
related: [[unreadable-manuscript-benchmark]], [[tengyur-triage]]
sources: []
---

## Context

The repo started from a viral X post (27 Aug 2026, ~1.5M views) claiming that "roughly 95% of
the 84,000 ancient manuscripts hidden in the Sakya Monastery library in Tibet remain
untranslated into modern global languages." Ten independent research agents were dispatched to
verify the claim, map the corpus, the digitization landscape, the AI state of the art, the
legal situation, and the existing open-source ecosystem. Full reports live in `research/`.

## Decision

**The project is not about Sakya Monastery, and the repo says so on its front page.**

Scope is: manuscripts that are genuinely unread — by machines first, by scholars second — and
the tools that would make them readable. Sakya is the origin story, not the target.

## Why

**The claim does not survive tracing.**

- "84,000" comes from a Xinhua report of 12 Nov 2003 in which monks and local relics experts
  *estimated* "about 84,000 *juan*". A same-week Chinese report says the wall "**legendarily**
  stores the complete 84,000 volumes" — 84,000 is the Buddhist stock number for dharma gates.
  84000.co's own FAQ states there has never been mention of 84,000 actual texts.
- Real counts: the 2005 physical move (first in ~700 years) surveyed **>20,000 works /
  >80,000 fascicles**. The monastery committee stated in Feb 2022: **>50,000 volumes**, 21
  Sanskrit palm-leaf manuscripts, internal cataloguing **finished in 2020**, ~20% leaf-scanned.
- "95%" has **no source before the tweet itself**. Searched independently in English and
  Chinese by three agents. No person, paper, or organization computed it.
- "Hidden / sealed / discovered in 2003" is a 2007 Wikipedia mutation of "piled up in a wall."
  It is an open floor-to-ceiling bookcase. Sarat Chandra Das described it in **1902**.
- The same library previously generated a "10,000-year-old records" variant that Africa Check
  and AAP debunked in 2020.

**The contents are mostly not unknown.** Named holdings are handwritten Kangyur and Tengyur
copies, deluxe gold-ink Prajñāpāramitā, Sakya Kabum, Lamdré, biographies, medicine, history.
Multiple hand copies of canons that already exist in print and in public-domain Unicode etext.
Estimate from report `02`: ~1–8% of volumes are plausibly unicum *works*; ~10–30% are unique
*witnesses* of known works. The second number has real philological value. Neither is a lost
literature.

**The material is unreachable regardless.** TAR entry requires a permit, licensed agency,
guide, and fixed itinerary; interior photography of the Great Scripture Hall is prohibited.
The scans sit on monastery-local systems — and the official running the scanning was still
petitioning Beijing in **March 2026** for a national digitization project, which is proof it
is not published. Public Sakya-wall images downloadable today: approximately zero.

**There is human risk.** A librarian at Kirti Monastery was sentenced in 2024 to three years
for importing Buddhist philosophy books from India. Recruiting or naming collaborators inside
the TAR endangers them, not us.

**`sakyalibrary.com` is a different institution.** International Buddhist Academy, Kathmandu —
784 Tibetan Unicode etexts, not scans, frozen since 2015, CC BY-NC-SA with an extra no-edit
clause, already mirrored to Internet Archive and HuggingFace. Viral articles paste its CC
licence onto the Tibet monastery. That conflation is the engine the meme runs on.

**The precedent already happened elsewhere.** Drepung's gNas bcu lha khang is the true
analogue: Paltsek catalogued it (2,483 pp., 2004), then published the residue as the
120-volume *bKa' gdams gsung 'bum* — 533 items, 160+ thinkers, previously known only from
rumour. One recovered text survives in a single manuscript and now anchors a subfield. The
sequence was catalogue → Tibetan facsimile → specialist edition. English came last, or never.

## Standing constraints this decision carries

- Never publish AI English of Lamdré or Hevajra practice texts. Sakya lineage authorities gate
  them; BDRC blocks sealed works; Wisdom requires initiation to purchase. Not negotiable by an
  outside repo.
- Honour upstream licences: 84000 TEI is CC BY-NC-ND, Dharmamitra's ToS forbids populating
  third-party apps, sakyalibrary.com is NC-SA plus no-edit. Nothing gets relicensed to MIT or
  CC0 on the way through.
- Do not scrape PRC heritage platforms as a "Sakya dump."
- If the repo cannot name an existing consumer — BDRC, Dharmamitra, Monlam, a working
  Tibetologist — it is shouting into a void. Predecessors that died (ACIP, THL, CompassionAI,
  the frozen USAID digitization program) died of encoding lock-in, grant sprawl, single-donor
  dependence, and having no user.
