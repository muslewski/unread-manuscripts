---
type: idea
summary: "Benchmark and pipeline for the ~4M Tibetan manuscript images that current OCR cannot read — the real unknown-text frontier, legally reachable today."
tags: [ocr, htr, tibetan, benchmark, corpus]
status: active
created: 2026-08-28
updated: 2026-08-28
maturity: forming
related: [[not-a-sakya-project]], [[tengyur-triage]], [[research-corpus]]
sources: []
---

## The idea

BDRC states publicly (Aug 2024) that roughly **4 million manuscript images** in its own
holdings cannot be read by Google Vision or Transkribus. That is the genuine unknown corpus:
not sealed behind a monastery wall, but sitting in an open archive that no machine can parse
and no scholar has time to read by hand.

Build a **reproducible benchmark plus a script-routing pipeline** over the manuscript classes
nobody has measured.

Concretely, three things that do not exist today:

1. **First public vision-LLM numbers on pecha.** There is no published GPT / Claude /
   Qwen-VL character error rate on the OpenPecha benchmark protocol. OpenPecha ships an
   evaluation toolkit; the 2025 bake-off covered BDRC–Monlam, Google Vision, and Gemini only.
2. **First numbers of any kind on gold-on-dark leaves** (*mthing shog*). Deluxe gold- and
   silver-ink manuscripts on indigo paper — the visually famous Tibetan material — have zero
   published OCR error rates anywhere in the literature. Palaeography exists; OCR does not.
3. **Script routing as the product.** "Tibetan OCR" is a category error: BDRC itself
   distinguishes 20 etic OCR classes across 48 literary scripts. Printed *uchen* is solved
   (98–99%). Handwritten *umê* cursive collapses on unseen hands. The useful artifact is a
   classifier plus a routing table, not another recognizer.

Ground truth to build on already exists and is openly licensed: TibSchol (CC0), PaganTibet
(Zenodo), Namgyal (Zenodo), OpenPecha's line-to-text sets.

## Why it might matter

- **It is measurable.** Success is a published CER, not a vibe. That alone separates it from
  most "AI for ancient texts" projects.
- **It is legally clean.** BDRC public-domain items, a free account, documented IIIF and PDF
  APIs. No permits, no scraping, no exfiltration, no lineage-restriction problem — the work
  translates nothing.
- **It fills a hole the incumbents named themselves.** BDRC published the 4-million figure.
  The gold-on-dark gap is visible in the absence of any citation.
- **It is the tool that would read a closed corpus if one ever opened.** See
  [[not-a-sakya-project]] — the Sakya material is unreachable, but the capability generalizes
  to any monastic collection that becomes available.
- **It respects the known ceiling.** Machine translation emits fluent wrong English on text
  with no parallel and no commentary. OCR does not have that failure mode: a CER is honest
  even when it is bad. Building at the transcription layer sidesteps the trap that makes the
  translation layer untrustworthy on exactly the unknown material.

## Rough shape if picked up

- Sample 100 images per script class; classify against BDRC's coarse classes.
- Run the OpenPecha `OCR-Evaluation-Toolkit` protocol across BDRC–Monlam models, Transkribus
  public models, and the vision LLMs nobody has scored.
- Publish per-class CER with the images and the protocol, so results are reproducible.
- Ten annotated gold-on-dark folios would establish whether channel inversion plus an
  existing woodblock model is salvageable, or whether the class needs its own ground truth.

## Known cost

Report `07` estimates 6–18 person-months to pipeline 10k mixed pages, 12–24 if the bulk is
unseen or ornate *umê*. A 2025 study needed 900 hand-corrected pages and 178,263 line
corrections over twelve months to reach 5.56% CER on its own corpus. Human ground truth by
Tibetan-script readers is the real budget line, not GPU time.
