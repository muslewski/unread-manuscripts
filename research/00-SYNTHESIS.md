# Synthesis: is there a real open-source project here?

Advisor synthesis over 10 independent Grok-4.6/xhigh research reports (`01`–`10`),
run 2026-08-27. Each child searched independently; overlaps below are *convergent*,
not copied.

---

## 1. The claim that started this is false

| Claim | Reality |
|---|---|
| "84,000 manuscripts" | Xinhua, 12 Nov 2003: monks and local relics experts **estimated** "about 84,000 *juan*". A same-week Chinese report says the wall "**legendarily** stores the complete 84,000 volumes" — 84,000 is the Buddhist stock number for *dharma gates*, not an inventory. 84000.co's own FAQ: "there has never been mention of 84,000 actual texts." |
| "hidden / sealed / discovered in 2003" | A 2007 Wikipedia mutation. The wall is an open floor-to-ceiling bookcase in the Lhakhang Chenmo that worshippers walk past. Sarat Chandra Das described it in **1902**. |
| Actual counts | 2005 physical move (first in ~700 yrs): **>20,000 works / >80,000 fascicles**. Monastery committee, Feb 2022: **>50,000 volumes**, 21 Sanskrit palm-leaf MSS, internal cataloguing **finished 2020**, ~20% leaf-scanned. |
| "95% untranslated" | **No source exists before the 27 Aug 2026 tweet itself.** Three children searched EN + ZH independently; none found a person, paper, or org that computed it. |
| "no real will to translate" | 84000 has spent >US$8.5M across 165+ grants and has the Kangyur at **50% published / ~80% translated**. |

The 2020 fact-check lineage is already public: the same library produced a "10,000-year-old
records" variant that Africa Check and AAP debunked in 2020. This is a meme with a five-year
mutation history, now wearing a Himalayan flood as a hook (the Aug 2026 Gyirong glacier
collapse is hundreds of km from Sa'gya County — Sakya was never in the inundation zone).

## 2. The content is mostly not unknown

Named contents of the wall: handwritten Kangyur, Tengyur, deluxe gold-ink Prajñāpāramitā,
Lamdré, *Tshad ma rigs gter*, *Sa skya bka' 'bum*, throne-holder biographies, medicine,
history, law, calendar. **Multiple handwritten copies of canons that already exist in print,
in Unicode etext (ACIP/Esukhia, public domain), and increasingly in English.**

Independent estimate from report 02: **~1–8% of volumes** are plausibly unicum *works*;
**~10–30%** are unique *witnesses* of known works. The second number is real value — it
changes critical editions — but it is philology, not a lost literature.

Calibration: Drepung's gNas bcu lha khang is the true analogue, and it already happened.
Paltsek catalogued it (2,483 pp., 2004), then published the residue as the 120-volume
*bKa' gdams gsung 'bum* (2006–2015): 533 items, 160+ thinkers, most previously known only
from rumour. Phya pa's *Tshad ma yid kyi mun sel* survives in **one** Drepung manuscript and
now anchors a subfield. That is what "unknown text discovered" actually looks like — and the
sequence was **catalogue → Tibetan facsimile → specialist edition**. English came last, or never.

## 3. You cannot get the Sakya material

- TAR requires a permit, a licensed agency, a guide, a fixed itinerary. Interior photography
  of the Great Scripture Hall is prohibited. No 2020–2026 first-hand account of a foreign
  scholar *working* in the Sakya holdings was found.
- The scans exist on monastery-local systems. The official who runs the scanning
  (洛卓加措) was **still petitioning Beijing in March 2026** for a national digitization
  project — which is proof the material is not published.
- Public Sakya-wall / palm-leaf images downloadable today: **≈ zero**.
- The TAR Sanskrit corpus is the precedent: surveyed 2006–11 (~1,000 bundles, ~60,000
  folios), published as **61 portfolio volumes in about five copies**. Steinkellner: "still
  out of bounds for scholars, both within China and beyond."
- **Human risk is real.** Lobsang Thapkhey, librarian of Kirti Monastery, was sentenced in
  2024 to three years for importing Buddhist philosophy books from India. Recruiting or
  naming TAR monastic collaborators endangers them.

`sakyalibrary.com` is a different institution entirely: International Buddhist Academy,
Kathmandu, funded by the Khenchen Appey Foundation. **784 Tibetan Unicode etexts** (not
scans), frozen since 2015, CC BY-NC-SA with an extra no-edit clause, and **already mirrored**
to Internet Archive (1,622 items) and HuggingFace (783 rows). Viral articles paste its CC
licence onto the Tibet monastery. That conflation is how the meme survives.

## 4. Everyone is already doing it

| Layer | Incumbent | State |
|---|---|---|
| Scans | **BDRC** | ~35M pages, 25M Tibetan; IIIF + API; PD items free |
| OCR | **BDRC + Monlam AI** | Open weights, desktop app, 26M pages processed; PD datasets shipping to HuggingFace through 2027 (Khyentse grant) |
| Etext infra | **OpenPecha** | Botok tokenizer, OPF/STAM, 539 repos, 9,531 data repos |
| MT | **Dharmamitra / MITRA** | MITRA-QWEN 9B is **#1 on Tibetan→English** (Elo 1876), beats Claude/GPT/Gemini; open weights |
| Canon translation | **84000** | Kangyur 50% published, 2035 target; Tengyur claimed through **2110** |
| Recovered MSS | **Paltsek** | Industrial publisher of Central Tibetan manuscript recoveries since 2002 |

A greenfield "Tibetan NLP + AI translation" repo duplicates every layer.

## 5. The finding that actually decides it

**AI is worst exactly where the material is most unknown.**

MITRA is genuinely useful — for triage, search, and first-pass on prose that *resembles
existing bitext*. The 2023 twenty-translator study: errors must be corrected, but it is "a
great point of departure," and veterans saw productivity gains.

But on text with no parallel in the 2M-pair training corpus, no commentary, tantric coding,
verse, or oral-lineage dependency, **MT emits fluent wrong English** — worse than a blank
page, because it looks like an answer. A polysemous term like *gnas* renders 75 different
Sanskrit words in Negi; models "consistently misinterpreted" its rare uses.

Same shape at the OCR layer: printed *uchen* is solved (98–99%). Handwritten *umê* cursive
collapses on unseen hands — a 2025 study needed **900 hand-corrected pages and 178,263 line
corrections over 12 months** to reach 5.56% CER on its own corpus, and reported that existing
models "perform poorly" off-the-shelf. Gold-on-dark deluxe leaves — exactly the famous Sakya
Yuan-dynasty manuscripts — have **zero published OCR numbers anywhere**.

So: the unknown-ness that makes the material exciting is the same property that makes the
AI pipeline unreliable on it. Any project must plan around that, not past it.

## 6. What is genuinely open

1. **Tengyur.** 0.7% published in English. ~95% not started. 84000's own target is **2110**.
   ~161,800 pages. The Tibetan etext is already public domain (ACIP / Esukhia / Derge).
2. **~25 million Tibetan pages on BDRC**, overwhelmingly untranslated — 600+ masters'
   collected works, not a wall in Shigatse.
3. **~4 million manuscript images BDRC holds that Google Vision and Transkribus cannot
   read** (BDRC's own words, Aug 2024). This is the real inaccessible corpus, and it is
   already legally in reach.
4. Named, specific, checkable holes:
   - `github.com/dharmamitra/dharmanexus-tibetan` is advertised in their docs and **404s**.
   - OpenPecha-Data: 9,531 repos, a **10 MB README-as-catalogue**, no index, no LICENSE.
   - BDRC OCR app (67★, most-starred Tibetan tool) has live tickets: CLI/API (#22),
     train-your-own-model (#44), mixed Chinese/Tibetan (#29).
   - **No public GPT/Claude/Qwen-VL pecha CER** on the OpenPecha benchmark protocol.
   - Gold-on-dark ink: unmeasured by anyone.

## 7. Hard constraints on any version of this

- **Do not publish AI English of Lamdré / Hevajra practice texts.** Sakya lineage gates them;
  Wisdom sells them requiring initiation; BDRC blocks "sealed" works; Lotsawa House and
  Khyentse Vision both keep restricted buckets. This is not negotiable by an outside repo.
- **84000 forbids AI first drafts** of canonical literature. Tsadra, KVP, and Monlam all
  want AI as *assistive tooling*. An open dump of raw LLM English fights every incumbent.
- **Honour the licences.** 84000 TEI is CC BY-NC-ND. Dharmamitra's ToS forbids using their
  API to populate third-party apps. sakyalibrary.com is NC-SA plus no-edit. Do not
  relicense any of it as MIT/CC0.
- **Failure modes that killed predecessors:** ACIP (encoding lock-in, site rot, founder-tied),
  THL (grant sprawl, migration loss), CompassionAI (prototype, no institution), USAID
  digitization (single-donor politics, frozen 2025). If the repo cannot name an existing
  consumer — BDRC, Dharmamitra, Monlam, a working Tibetologist — it is the void.

## 8. Options

**A — Drop it.** The question was "is this already solved or still unknown." Answer
delivered: the Sakya framing is a meme, the corpus is unreachable, the ecosystem is staffed.
That is a complete result.

**B — Tengyur triage.** Build on ACIP/Esukhia public-domain Derge etext (no permission
needed, already Unicode). Run MITRA + retrieval over the ~95% of Tengyur nobody will publish
before 2110. Ship a browsable machine-draft index — explicitly labelled draft, with retrieved
human parallels shown alongside every segment. Real gap, legal corpus, honest framing.
Risk: 84000 owns the space socially even where it has no output.

**C — The unreadable-manuscript benchmark. ← recommended**
BDRC says ~4 million manuscript images defeat current OCR. Gold-on-dark and ornate *umê*
have literally no published error rates. Public ground truth exists (TibSchol CC0,
PaganTibet, Namgyal on Zenodo) and OpenPecha ships an evaluation toolkit.

Build: a reproducible benchmark + script-routing pipeline over the manuscript classes nobody
has measured — including the first public GPT/Claude/Qwen-VL numbers on the OpenPecha
protocol, and the first numbers of any kind on gold-on-dark.

Why this one: it is the *actual* unknown frontier rather than the rumoured one; the material
is legally reachable today; it is measurable, so success is a published CER rather than a
vibe; it fills a hole the incumbents named themselves; and it does not require translating
anything, which sidesteps both the lineage-restriction problem and the fluent-wrong-English
problem. If a Sakya-specific corpus ever opens, this is the tool that would read it.

---

*Method: `armory fleet grok-xhigh`, 10 children, isolated worktrees, ~19,800 words, ~200
cited sources across English, Chinese, and Tibetan. Every child was instructed that a
truthful negative finding is a successful result. Nine of ten returned one.*
