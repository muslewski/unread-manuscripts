# State of the art in classical Tibetan machine translation

## Verdict

- **Q1.** Monlam AI (Dharamsala, launched 3 Nov 2023) and Dharmamitra/MITRA (Berkeley/Tohoku, from April 2023) are the real players. They share **2 million Tibetan–English sentence pairs**. Open 9B weights exist; web UIs are free; a public unrestricted API does not.
- **Q2.** Dharmamitra has peer-reviewed papers (2022–2026), open parallel data, and a live leaderboard. MITRA-QWEN 9B is currently first on Tibetan→English (Elo 1876). Measured quality is LLM-judge / BLEURT, plus one 20-translator human study from 2023 — not a 2026 Tibetologist MQM panel.
- **Q3.** MLotsawa (T5, BLEU ~4) is a small open baseline. NLLB covers `bod_Tibt` but fails on classical Buddhist text. Google Translate added Tibetan in June 2024; quality on *classical* Tibetan is unpublished. Frontier LLMs are close on BLEURT and lose to the 9B domain model on Tibetan Elo; TLUE shows most LLMs below random on Tibetan understanding.
- **Q4.** Tsheg-syllable segmentation is largely bypassed by byte-level LLMs. Polysemy, verse, tantric code, unmarked quotation, and oral commentary still break MT. RAG helps only when a close parallel exists.
- **Q5 (the decision).** **Yes: useful for triage, indexing, and discovery** of prosaic canonical/commentarial text that resembles existing bitext. **No: not publishable, not citable, not trustworthy on tantra, terse verse, unique manuscripts, or oral-lineage meaning.** That line is already occupied. Do not train another translator.

## Findings

### 1. MITRA / Monlam AI

These are **two collaborating organisations**, often conflated.

**Monlam Tibetan IT Research Centre** (Dharamsala; Geshe Lobsang Monlam) launched Monlam AI on 3 November 2023: bidirectional Tibetan–English MT, OCR, STT, TTS ([CTA](https://staging.tibet.net/sikyong-penpa-tsering-attends-launch-of-first-ever-tibetan-ai-tool-developed-by-monlam-it-research-centre/); [RFA, 15 Nov 2023](https://www.rfa.org/english/news/tibet/translation-software-11152023122728.html)). Public products: [monlam.ai](https://monlam.ai/), Melong.ai. Grand Dictionary (2022): 360,000 headwords, 223 volumes.

**Monlam-MITRA (2023–24).** [FACT] Autumn 2023: NLLB-200 fine-tuned on **>2 million** Tibetan–English pairs collected by Monlam, released on monlam.ai. February 2024: MADLAD-400 successor adding Sanskrit, Chinese, Pāli ([Meelen, Nehrdich & Keutzer, *RET* 72, 2024](https://doi.org/10.17863/CAM.110900)). Those 2M pairs later became 20% of Gemma 2 MITRA pretraining ([arXiv:2601.06400](https://arxiv.org/abs/2601.06400)).

**Monlam Melong.** 9B Tibetan LLM; preview at [TenzinGayche/Monlam_Melong_preview](https://huggingface.co/TenzinGayche/Monlam_Melong_preview), **fine-tuned from `buddhist-nlp/gemma2-mitra-base`**. Card licence: “details to be added” — **[FACT] unspecified**. 2025 Manifest claimed ~24B tokens, 73% on ~1,500 internal questions, 71% on CBSE Class 12 Tibetan, beating Gemini/Claude/DeepSeek ([Tibet Express](https://tibetexpress.net/at-2025-monlam-manifest-centre-declares-melong-outperforms-global-ai-in-tibetan/)). **[CLAIM]** internal scores; no independent replication.

**Availability.** Free web UIs. [MonlamAI FastAPI](https://github.com/MonlamAI/monlamai-API) needs `API_KEY`. Full production weights and the 2M-pair dump are **not** public.

### 2. Dharmamitra (Berkeley / Tohoku)

**[FACT]** Started April 2023 at BAIR under Kurt Keutzer with Sebastian Nehrdich (now Tohoku); Tsadra-funded; BDRC partnership ([H-Net 2025](https://networks.h-net.org/group/announcements/20121238/introducting-dharmamitra-dharmanexus-new-set-digital-tools-buddhist)). Live: MITRATranslate, MITRASearch, MITRA-OCR, DharmaNexus at [dharmamitra.org](https://dharmamitra.org). Web MT is free (18,000-character cap). API is for collaborating institutions, not public scrape ([docs/ToS](https://dharmamitra.github.io/dharmamitra-guides/dharmanexus/)).

**Papers.** SansTib ([LREC 2022](https://aclanthology.org/2022.lrec-1.724/)); MITRA-zh ([NLP4DH 2023](https://aclanthology.org/2023.nlp4dh-1.29/)); Breakthroughs in Tibetan NLP ([*RET* 72, 2024](https://doi.org/10.17863/CAM.110900)); ByT5-Sanskrit ([EMNLP Findings 2024](https://aclanthology.org/2024.findings-emnlp.805/)); MITRA-zh-eval ([NLP4DH 2025](https://aclanthology.org/2025.nlp4dh-1.12/)); MITRA ([arXiv:2601.06400](https://arxiv.org/abs/2601.06400), 10 Jan 2026).

**Gemma 2 MITRA.** [FACT] Gemma 2 9B, 2-epoch CPT on ~4.4B tokens (paper) / 7B (HF card): 2M bo–en (Monlam), 1M sa–en (then unpublished), 41k gold Tibetan↔Chinese (Kumarajiva), ACIP Tibetan. Open: [`gemma2-mitra-base`](https://huggingface.co/buddhist-nlp/gemma2-mitra-base), [`gemma-2-mitra-it`](https://huggingface.co/buddhist-nlp/gemma-2-mitra-it) ([7 Nov 2024](https://x.com/SebastianNehrd2/status/1854651511361749464)). MITRA-parallel v1: 1.74M mined pairs (73% perfect / 16% partial / 11% wrong on n=100); v2: 1,693,730 records ([github.com/dharmamitra/mitra-parallel](https://github.com/dharmamitra/mitra-parallel)). MITRA-zh-eval: 2,662 Buddhist Chinese–English pairs; five specialists rated 182 outputs; **GEMBA tracks humans, BLEU/chrF do not**.

**MITRA-QWEN (July 2026).** [`mitra-qwen35-translate`](https://huggingface.co/buddhist-nlp/mitra-qwen35-translate): Qwen3.5-9B, ~22B-token CPT, filtered SFT, CPO. Closed-book Tibetan Elo **1876** ([leaderboard](https://dharmamitra.github.io/dharmamitra-leaderboard/), Aug 2026, 63 models). Pairwise vs Claude Opus 4 on Tibetan→English: **62%** Gemini-judge / **51%** Claude-judge; GEMBA 84.6. **[FACT]** LLM-as-judge, not Tibetologist ratings. **[FACT]** the leaderboard warns of Gemini-judge bias and that **81% of Tibetan test rows were near-duplicates in the retrieval index** before a 12 June 2026 cleanup — older MITRA-RAG Tibetan scores are likely inflated.

**Human quality (2023).** Twenty translators reviewed Monlam-MITRA: errors must be corrected; still “a great point of departure”; veterans saw productivity gains. Failures: omissions, oscillatory hallucinations ([RET 72](https://www.repository.cam.ac.uk/bitstreams/ef9540b5-cd53-4297-86ce-692ba871f643/download)).

### 3. MLotsawa, NLLB, Google Translate, frontier LLMs

**MLotsawa** ([github.com/billingsmoore/MLotsawa](https://github.com/billingsmoore/MLotsawa); THL/UVA). MIT-licensed T5 [small 60M](https://huggingface.co/billingsmoore/mlotsawa-ground-small) / [base 223M](https://huggingface.co/billingsmoore/mlotsawa-ground-base); 861,417 Buddhist pairs (public + Monlam + THL). BLEU **3.54 / 4.08**, chrF **19.89 / 20.85**, GEMBA ~76 ([Moore & Lauren 2025](https://doi.org/10.21203/rs.3.rs-7409829/v1)). Authors call n-gram scores “exceptionally low”; samples are followable. Offline baseline, not competitive with MITRA-QWEN.

**CompassionAI Lotsawa** ([github.com/CompassionAI/lotsawa](https://github.com/CompassionAI/lotsawa)). NLLB-derived long-text models for Kangyur/Tengyur. **[FACT]** Zero-shot NLLB on the Diamond Cutter yields New-Testament-like loops; tokenizer UNK ~**3%** on Kangyur/Tengyur ([CompassionAI 2022](https://www.compassion-ai.org/results/no-language-left-behind/)). Volunteer work, 2022–23. Not 2026 SOTA.

**NLLB-200.** [FACT] Includes Standard Tibetan (`bod_Tibt`); open weights. FLORES-200 is **modern** news Tibetan, not classical. Distilled NLLB chrF++ on FLORES `bod` ~23–26 ([arXiv:2605.15976](https://arxiv.org/html/2605.15976v1)). Tibetan BLEU is unreliable (no standard word tokenizer).

**Google Translate.** [FACT] Tibetan added **27 June 2024** in the 110-language PaLM 2 expansion ([Google Help](https://support.google.com/translate/answer/15139004?hl=en-IN); [blog](https://blog.google/products/translate/google-translate-new-languages-2024/)). **[GAP]** no published eval on *classical Buddhist* Tibetan.

**Frontier LLMs.**

- Leaderboard Tibetan BLEURT: GPT-5.5 0.573, Claude Opus 4.8 0.574, Grok-4.2 0.560 — behind MITRA live API (0.594) and MITRA-QWEN.
- **TLUE** ([Gao et al., EMNLP 2025](https://aclanthology.org/2025.emnlp-main.1777/)): Ti-MMLU 11,528 items; most LLMs **below 25% random**. Modern/exam Tibetan, not MT — still the only large public LLM eval in Tibetan.
- **Ken McLeod, *Tricycle*, Oct 2023** ([link](https://tricycle.org/magazine/tibetan-ai-translation/)): GPT-4/Bard nonsense on Garab Dorje’s *Three Lines*. Dated, but the failure (cliché emulation, no grip on pith) still describes verse/instruction.
- **Nehrdich, Goodman Lecture 32 (Oct 2025)** ([YouTube](https://www.youtube.com/watch?v=Ezxg9TwRf5g)): practitioner reports Claude 4.x *regressed* vs 3.5 on Tibetan/Sanskrit as labs optimise for math/code. **[CLAIM]** anecdotal; matches “9B domain > frontier” on the leaderboard.
- **DharmaBench** ([IJCNLP 2025](https://aclanthology.org/2025.ijcnlp-long.114.pdf)): first LLM benchmark on *classical* Skt/Tibetan Buddhist texts — classification, not MT.

### 4. Hard problems

**Segmentation.** Tibetan marks syllables (tsheg), not words. [FACT] core bottleneck ([Huang et al. 2025](https://arxiv.org/html/2510.19144v1); Botok/ACTib in [Meelen et al. 2024](https://doi.org/10.17863/CAM.110900)). Byte-level LLMs (Gemma 2, Qwen3.5) largely skip BPE-on-syllable breakage; classical BPE still invents illegal subwords ([Gyatso et al. 2025](https://www.fujipress.jp/jaciii/jc/jacii002900061273/)). MITRA does not need a word-breaker at inference.

**Polysemy.** [FACT] *gnas* translates **75 Sanskrit words** in Negi; Claude/MITRA “consistently misinterpreted” rare uses as “moral support” and often elided the term ([2024 talk](https://www.youtube.com/watch?v=5Dqyc6KtiU8)). RAG helps only if a close parallel is retrieved.

**Honorifics.** No dedicated MT eval. **[GAP]**

**Verse.** CompassionAI saw more pronoun-switching on *Madhyamakāvatāra* poetry than on the Diamond Cutter. **[FACT]** verse is harder. **[GAP]** no verse/prose split published for MITRA-QWEN.

**Tantric code (*sandhyābhāṣā*).** **[GAP]** no published MT eval. **[SPECULATION]** models trained on 84000/Lotsawa House/Kangyur bitext will emit the *exoteric* training gloss, not a lineage-coded sense.

**Sanskrit inside Tibetan.** In-distribution for MITRA (sa–bo parallels, IAST prompts). Still a register error source.

**Unattributed quotation.** A **retrieval** problem. DharmaNexus exists for it. Bare MT treats a quotation as original.

**Oral commentary.** [FACT] many gter-ma, pith, and tantric passages are unintelligible from the written string alone. MT cannot invent an oral gloss that is not in the bitext. **Hard ceiling**, not an engineering lag.

**How much they break MT.** On prose sūtra/śāstra that looks like 84000 / Lotsawa House / Tengyur bitext: degraded but usable (the 20-translator result). On verse, tantra, unique MSS, honorific letters, anything oral: they break it. Dharmamitra’s own UI: “complement human expertise, not replace it” ([dharmamitra.org/translate](https://dharmamitra.org/translate)). Taylor & Francis 2025 ([abstract](https://www.tandfonline.com/doi/full/10.1080/14639947.2025.2562765)): NMT “frequently fall[s] short in capturing… doctrinal subtleties.”

### 5. The line

A Tibetologist in 2026 would **use** MITRATranslate / MITRA-QWEN to first-pass an unknown folio, search across bo/sa/zh, triage genre, and post-edit formulaic prose. They would **not** cite it; not trust it on a unique Sakya manuscript absent from the 2M-pair bitext; not treat tantric or pith output as the meaning of the text. That is already Dharmamitra/Tsadra/Monlam’s documented use-case. Building “an AI translator for Sakya manuscripts” without wrapping these models and putting a scholar in the loop is a 2023 NLLB fine-tune, weaker.

## Sources

| URL | What it is | Lang. | Reliability |
|-----|------------|-------|-------------|
| https://arxiv.org/abs/2601.06400 | MITRA paper: corpus, Gemma 2 MITRA, eval | en | high |
| https://huggingface.co/buddhist-nlp/mitra-qwen35-translate | MITRA-QWEN 9B card + pairwise eval | en | high |
| https://dharmamitra.github.io/dharmamitra-leaderboard/ | Live MT leaderboard, 63 models, Aug 2026 | en | high (caveats on page) |
| https://aclanthology.org/2025.nlp4dh-1.12/ | MITRA-zh-eval: human vs BLEU/chrF/GEMBA | en | high |
| https://aclanthology.org/2023.nlp4dh-1.29/ | MITRA-zh 2023 | en | high |
| https://aclanthology.org/2022.lrec-1.724/ | SansTib parallel corpus | en | high |
| https://doi.org/10.17863/CAM.110900 | *RET* 72; 20-translator study | en | high |
| https://github.com/dharmamitra/mitra-parallel | Open parallel corpus v1/v2 | en | high |
| https://huggingface.co/buddhist-nlp/gemma2-mitra-base | Open 9B CPT base | en | high |
| https://dharmamitra.org | Production translator (free web UI) | en | high |
| https://support.google.com/translate/answer/15139004?hl=en-IN | Google Translate list includes Tibetan | en | high |
| https://arxiv.org/abs/2207.04672 | NLLB-200; FLORES includes `bod_Tibt` | en | high |
| https://www.compassion-ai.org/results/no-language-left-behind/ | Zero-shot NLLB fails on classical Buddhist Tibetan | en | high |
| https://huggingface.co/billingsmoore/mlotsawa-ground-small | MLotsawa T5; BLEU/chrF/samples | en | high |
| https://doi.org/10.21203/rs.3.rs-7409829/v1 | Moore & Lauren 2025 T5 preprint | en | med (preprint) |
| https://aclanthology.org/2025.emnlp-main.1777/ | TLUE: LLMs below random on Tibetan MMLU | en | high |
| https://arxiv.org/html/2510.19144v1 | Survey: Tibetan AI + segmentation | en | high |
| https://tricycle.org/magazine/tibetan-ai-translation/ | McLeod 2023 on GPT-4/Bard | en | med |
| https://www.youtube.com/watch?v=Ezxg9TwRf5g | Nehrdich Goodman Lecture | en | med (talk) |
| https://www.youtube.com/watch?v=5Dqyc6KtiU8 | Polysemy of *gnas* | en | med (talk) |
| https://huggingface.co/TenzinGayche/Monlam_Melong_preview | Melong preview weights | en | med |
| https://tibetexpress.net/at-2025-monlam-manifest-centre-declares-melong-outperforms-global-ai-in-tibetan/ | Melong 2025 internal scores | en | low–med (PR) |
| https://www.rfa.org/english/news/tibet/translation-software-11152023122728.html | Monlam AI 2023 launch | en | med |
| https://aclanthology.org/2025.ijcnlp-long.114.pdf | DharmaBench | en | high |
| https://www.tandfonline.com/doi/full/10.1080/14639947.2025.2562765 | MT misses doctrinal nuance | en | med (paywalled abstract) |

## Gaps and what would settle them

- **No Tibetologist-rated eval of MITRA-QWEN split by genre** (prose / verse / tantra / letters). Next: 200-item MQM panel, three Tibetologists, public items.
- **Google Translate on classical Tibetan unpublished.** Next: run the 4,051-sentence Dharmamitra bo–en set; GEMBA + 50-item human sample.
- **Honorifics, meter, tantric code unmeasured.** Next: three 50-item challenge sets.
- **Melong 73%/71% internal.** Next: run Melong on TLUE and the Dharmamitra bo–en set.
- **2M Monlam pairs not public.** Next: ask for a research dump; without it, independent retraining is blocked.
- **Oral-commentary ceiling unquantified.** Next: 20 passages khenpos call unintelligible without the oral gloss. Expect zero recovery.

## Implication for the open-source project

- **AGAINST training a new Tibetan MT model.** MITRA-QWEN 9B is open, SOTA on the only public classical-Asian MT leaderboard, and already in a free scholar UI. Re-training NLLB/T5 is a 2023 regression.
- **FOR wrapping.** Call [`buddhist-nlp/mitra-qwen35-translate`](https://huggingface.co/buddhist-nlp/mitra-qwen35-translate) (one GPU) or the institutional dharmamitra.org API; RAG over 84000 / Lotsawa House / THL. Retrieval is where Dharmamitra still gains Elo.
- **FOR triage, AGAINST “AI translation” as the product.** Output = machine gloss + retrieved human parallels + OCR-uncertain spans + a human lotsawa’s edit. Label it draft. The 20-translator study is the spec.
- **NEUTRAL-to-AGAINST frontier APIs as the spine.** Close on BLEURT, worse Tibetan Elo than a 9B domain model, expensive, and (per Nehrdich) able to regress unnoticed. Second opinion only.
- **The ceiling is not compute.** Segmentation is mostly solved; polysemy and oral commentary are not. On genuinely unknown text (no parallel, no commentary, tantric), **MT emits fluent wrong English** — worse than a blank page. Project value, if any: sourcing and cataloguing, with MT as a search index, not a translator of last resort.
