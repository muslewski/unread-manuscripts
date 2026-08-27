# unread-manuscripts

> **Seed note — parked idea, not an active project.**
> This repo holds research and a direction. No code yet. Picked up when there is time.

Manuscripts that are genuinely unread — by machines first, by scholars second — and the tools
that would make them readable.

---

## How this started

A viral post claimed that *"roughly 95% of the 84,000 ancient manuscripts hidden in the Sakya
Monastery library in Tibet remain untranslated into modern global languages."* The idea of an
unknown text is a good hook. So the first question was the honest one: **is this still
unknown, or already solved?**

Ten independent research agents were dispatched to find out — claim provenance, actual
holdings, digitization landscape, translation ecosystem, AI state of the art, OCR reality,
open-source survey, legal access, and the demand side. ~19,800 words, ~200 cited sources
across English, Chinese, and Tibetan. Everything is in [`research/`](research/), starting with
[the synthesis](research/00-SYNTHESIS.md).

## What the research found

**The claim is false.** "84,000" traces to a Xinhua report of 12 Nov 2003 in which monks
*estimated* the number — and 84,000 is the Buddhist stock figure for dharma gates, not an
inventory. The 2005 physical survey counted >20,000 works. The monastery itself said >50,000
volumes in 2022, catalogued internally since 2020. **"95%" has no source before the tweet.**
"Hidden behind a sealed wall" is a 2007 Wikipedia mutation — Sarat Chandra Das described the
open bookcase in 1902.

**The contents are mostly not unknown** — largely handwritten copies of canons that already
exist in print and in public-domain Unicode etext. Roughly 1–8% of volumes are plausibly
unique *works*; 10–30% are unique *witnesses* with real philological value. That is
scholarship, not a lost library.

**The material is unreachable anyway.** Permits, guides, photography bans, and scans held on
monastery-local systems. The official who runs the scanning was still petitioning Beijing in
March 2026 for a national digitization project — which is proof it is not public.

**The field is staffed.** BDRC (~35M pages), OpenPecha, Monlam AI, Dharmamitra (whose 9B
MITRA-QWEN currently beats frontier models on Tibetan→English), 84000, Paltsek. A greenfield
"Tibetan NLP + AI translation" repo duplicates every layer.

**And the finding that actually decides it:** AI is worst exactly where the material is most
unknown. With no parallel in the training bitext and no commentary, machine translation emits
*fluent wrong English* — worse than a blank page, because it looks like an answer.

## Where the real frontier is

BDRC states that roughly **4 million manuscript images in its own holdings cannot be read** by
current OCR. That is the genuine unknown corpus — not sealed in Shigatse, but sitting in an
open archive that no machine can parse. It is legally reachable today with a free account.

Nobody has measured it. There are **no public GPT / Claude / Qwen-VL error rates on pecha**,
and **no published OCR numbers of any kind on gold-on-dark leaves** — the visually famous
Tibetan manuscripts.

So the direction is a **benchmark and script-routing pipeline over the manuscript classes
nobody has measured**. Success is a published character error rate, not a vibe. It translates
nothing, which sidesteps both the lineage-restriction problem and the fluent-wrong-English
trap. And if a closed corpus ever opens, it is the tool that would read it.

Written up in [`unread-mind/ideas/`](unread-mind/ideas/). The runner-up — a triage index over
the ~95% of the Tengyur with no English translation and no publication date before 2110 — is
there too.

## Layout

```
research/          11 frozen reports — the evidence base
unread-mind/       Memory Atlas vault — the repo's mind
  ideas/           the two surviving directions
  map/decisions/   why this is not a Sakya project
  map/zones/       what the research corpus is
```

The vault runs on [memory-atlas](https://github.com/muslewski/memory-atlas).
`npx atlas search <terms>` to query it, `npx atlas check` to verify it.

## Ground rules, if this ever gets built

- **Never publish AI English of restricted tantric material** (Lamdré, Hevajra). Sakya lineage
  authorities gate it, BDRC blocks sealed texts, publishers require initiation. Not
  negotiable by an outside repo.
- **Honour upstream licences.** 84000 TEI is CC BY-NC-ND. Dharmamitra's ToS forbids populating
  third-party apps. Nothing gets relicensed on the way through.
- **Do not scrape PRC heritage platforms**, and do not recruit or name collaborators inside
  the TAR — a monastery librarian was sentenced to three years in 2024 for importing books.
- **Name a real consumer or don't build it.** Predecessors died of encoding lock-in, grant
  sprawl, single-donor dependence, and having no users.

## Contributing

Open to it — the idea is genuinely better as a shared one. Issues and discussion welcome,
especially from anyone working in Tibetan OCR/HTR or digital philology. Corrections to the
research are particularly welcome: the reports are frozen evidence, so fixes land as new notes
that link back rather than edits in place.

## Licence

Code: [MIT](LICENSE). Research prose in `research/` and `unread-mind/`:
[CC BY 4.0](LICENSE-DOCS) — cite it and it's yours to use.
