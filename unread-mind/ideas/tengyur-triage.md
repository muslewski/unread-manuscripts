---
type: idea
summary: "Machine-draft triage index over the ~95% of the Tengyur that has no English translation and no publication date before 2110."
tags: [translation, tengyur, mt, corpus]
status: active
created: 2026-08-28
updated: 2026-08-28
maturity: rough
related: [[unreadable-manuscript-benchmark]], [[not-a-sakya-project]], [[research-corpus]]
sources: []
---

## The idea

The Tengyur — roughly 161,800 pages, 4,093 texts — is **0.7% published in English**.
84000's own stated completion target for it is the year **2110**. About 95% has not been
started.

The Tibetan side is already solved: ACIP and Esukhia have public-domain Unicode etext of the
Derge Tengyur. No permission is needed, nothing must be scanned, nothing must be scraped.

Build a **browsable machine-draft index** over that corpus: MITRA (or its successor) plus
retrieval, with every segment shown next to the human parallels the retriever found. Label it
draft everywhere it appears. The product is triage and discovery — what is this text, what is
it about, where has it been quoted, is it worth a scholar's month — not a translation of
record.

## Why it might matter

- The gap is real and nobody disputes it. A century-long publication horizon is an admission
  that the current pipeline cannot cover the corpus.
- The corpus is legal, already digital, and already tokenized.
- MITRA-QWEN 9B currently leads Tibetan→English and beats frontier models; the modeling work
  is done. The missing artifact is a **usable surface over the untranslated bulk**.

## Why it might not

- 84000 forbids AI first drafts of canonical literature, and Tsadra, Khyentse Vision, and
  Monlam all take the same line: AI as assistive tooling, not translator of record. They own
  this space socially even where they have no output for eighty years.
- Machine translation emits **fluent wrong English** when there is no close parallel in the
  training bitext — which is precisely the condition across most of the untranslated Tengyur.
  A draft index that looks authoritative is worse than an empty shelf.
- The honest framing (draft, unreviewed, retrieval-backed) is also the framing that makes it
  much less exciting to build.

## Verdict for now

Second choice behind [[unreadable-manuscript-benchmark]]. Same curiosity, worse failure mode:
OCR error is honest, translation error is persuasive.
