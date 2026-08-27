# Getting from manuscript image to Tibetan text: OCR/HTR reality check

## Verdict

- [FACT] Image-to-text is **not unsolved**; it is **script-stratified**. Computer-font and clean woodblock *uchen* (*dbu can*) are production-grade. Handwritten *umê* (*dbu med*) is usable **in-domain** after hundreds of GT pages and collapses on unseen hands. Gold-on-dark deluxe leaves have **no published OCR numbers**.
- [FACT] Tools that work on pecha today: the **BDRC/Monlam AI desktop app** (14 Mar 2025, [bdrc.io](https://www.bdrc.io/blog/2025/03/14/bdrc-announces-the-release-of-ocr-app-for-tibetan/), [github.com/buda-base/tibetan-ocr-app](https://github.com/buda-base/tibetan-ocr-app)) and **Transkribus public models** (TibSchol, Divergent Discourses, PaganTibet). Namsel is a 2016 **machine-print** engine. Tesseract `bod` is weak. **No public Kraken/eScriptorium Tibetan model** found.
- [FACT] Gemini 2.5 **lost** a 2025 pecha bake-off to BDRC–Monlam (zero-shot weighted CER **195.8**). Gemini 2.0 Flash **38.9** is still not scholarly. GPT/Claude pecha CER: **not published**.
- [FACT] Public GT is huge for printed uchen (millions of lines) and thin for manuscript umê (tens of thousands; OpenPecha Drutsa *eval* = **595 lines**). In-domain umê CERs of 1.4–3.6% **do not transfer** (JOHD 2025: existing models “perform poorly”; own model **5.56%** after 900 pages).
- [SPECULATION] Given 10,000 unpublished Sakya images tomorrow: **do not build a new OCR engine**. Wrap BDRC + Transkribus, route by script, fine-tune umê. Scholarly-usable (CER ≲5%) off the shelf: **~20–50%** of a mixed monastic corpus, almost entirely a function of xylograph-uchen share. Effort: **6–18 person-months** to pipeline 10k pages; **12–24** if the bulk is unseen/ornate umê.
- [FACT] The gate is **image access + umê/layout/gold-ink**, not missing OCR. A greenfield recogniser duplicates BDRC, Monlam, TibSchol, and Esukhia.

## Findings

### 1. Tibetan OCR tooling and measured error rates

**Namsel (2016).** [FACT] Rowinski & Keutzer, *Himalayan Linguistics* 15(1) ([paper](https://escholarship.org/uc/item/6d5781k5)): isolated-character **99.6%**; segmented pages **95–99%**; Pedurma **>99%**; PRC press **98–99%**; recent pecha publications **97–99%**. ~45k training characters; **1.5 million pages**. They estimated only **~25% of then-TBRC images were machine-printed**. Machine-print uchen only. Code: [github.com/max-lancaster/namsel](https://github.com/max-lancaster/namsel) (Ubuntu 14.04-era).

**Google / BDRC.** [FACT] From ~2020 BDRC ran Google Vision on **~3 million pages** ([2024 talk](https://www.youtube.com/watch?v=4JKdUKC7K7I)). Luo et al. (arXiv:2304.03427): Google CER **~25% → 12.26%** with a Transformer + confidence-score corrector. Norbu Ketaka (2022–23) claimed **80–90% further error reduction** via vision cleanup + Tibetan BERT ([Fairbank](https://fairbank.fas.harvard.edu/research/blog/norbu-ketaka-tibetan-manuscripts/)). [FACT] BDRC 28 Aug 2024: Google Vision and Transkribus **cannot read most unique manuscripts** (~**4 million** MS images): [bdrc.io/blog/2024/08/28](https://www.bdrc.io/blog/2024/08/28/transforming-tibetan-text-digitization-bdrcs-groundbreaking-ocr-project/). Digital Tibetan (Mar 2023) rated Google Drive **4/5** vs Tesseract **2/5** on woodblock pecha.

**BDRC OCR app (2025).** [FACT] Free offline app, ~15 s/page, PageXML, **one model per style** ([github.com/buda-base/tibetan-ocr-app](https://github.com/buda-base/tibetan-ocr-app)). Best on uchen font/woodblock; also two major umê scripts. HuggingFace: layout **Photi / PhotiLines**; uchen **LhasaKanjur, LithangKanjur, DergeTenjur, Woodblock, BigUCHAN, GoogleBooks_*, Norbuketaka_***; umê **Drutsa-A, CombinedBetsug_***; HTR-Base; script classifier ([forum](https://forum.openpecha.org/t/the-current-state-of-tibetan-ocr-bdrc-and-monlam-ai/146); [huggingface.co/BDRC](https://huggingface.co/BDRC)). [CLAIM] A 2025 Japanese project reports Woodblock **line detection >95%** and **char accuracy 90–95%** ([tech.ldas.jp](https://tech.ldas.jp/en/posts/bac0870d56a3c3/)) — not BDRC’s official table. Feb 2026 BDRC: **>26 million** images processed, claimed **~10% accuracy gain**, **~35k** aligned MS/woodblock images ([bdrc.io/blog/2026/02/28](https://www.bdrc.io/blog/2026/02/28/bdrc-launches-major-initiative-to-build-open-buddhist-datasets-for-ai/)).

**OpenPecha bake-off (13 Aug 2025).** [FACT] Page CER on 15 wild pecha sets. **BDRC–MonlamAI won 11**, Google Vision 3, Gemini 2.0 Flash 1. Weighted Gemini CER: 2.5 Flash **195.8 → 84.2** few-shot; 2.5 Lite **577.2**; 2.0 Flash **38.9**. High variance. Old umê and damaged Mongolian prints stay hard; clean Derge/Narthang uchen fare better ([forum](https://forum.openpecha.org/t/report-ocr-benchmark/429); [sheet](https://docs.google.com/spreadsheets/d/1x3E57F2JnNoKs--WYAIIUP5anghfXVYX67v4HU_xqiM)). Dharmamitra’s better Gemini-2.5-Lite numbers **were not reproduced**. [FACT] No public GPT/Claude pecha CER. [SPECULATION] A VLM can draft a cropped line; it is not a 10k-folio pipeline.

**Transkribus.** [FACT] TibSchol (ÖAW/ERC): layout “Tibetan Pecha” ID 54306, **1,699 folios**, **6.64% loss**, horizontal baselines only ([model card](https://www.transkribus.org/models/tibetan-pecha)); Drutsa ID 54525 **CER 1.40%** (422/44 folios); Betsug ID 54935 **CER 3.6%** on 93 folios ([HTR tools PDF](https://www.oeaw.ac.at/fileadmin/Institute/IKGA/project_tibschol/PDFs/Online_documents/TibSchol_HTR_tools_v2_1.pdf)). **In-domain validation.** Divergent Discourses: TMP 4.3 **3.87%** (440/37 pages, modern print); TibNewsOne4All **2.52%** (500 newspaper pages); Tibetan Generic 0.1 **3.58%** (1,380/153 pages, mixed uchen+umê, 18th–20th c.). Namgyal/TMPV (RET 79, 2025): PyLaia **1.9%** on early uchen MSS; BDRC BigUchan **CER 0.069** off-the-shelf, **0.05** after fine-tune ([RET 79 PDF](https://d1i1jdw69xsqx0.cloudfront.net/digitalhimalaya/collections/journals/ret/pdf/ret_79_03.pdf); [Zenodo 14247731](https://zenodo.org/records/14247731)). [FACT] Models **cannot be downloaded** (JOHD 2025); recognition burns credits.

**eScriptorium/Kraken.** [FACT] Named as alternatives in JOHD 2025; authors still used Transkribus. No public Kraken Tibetan `.mlmodel` found. Not off-the-shelf for Sakya pecha.

**Tesseract.** [FACT] `bod` pack exists; 2023 pecha demo is garbled (2/5). TibOCR-Bench (2025) CharAcc **84.50** is a **printed/modern** table, not historical pecha. No Tesseract CER on Sakya-class MSS.

### 2. The script problem

| Material | Status | Best published numbers | Caveat |
|---|---|---|---|
| Computer-font uchen | **Solved** | Namsel 98–99%; Google usable; BDRC GoogleBooks/Norbuketaka | Google raw ~25% CER on mixed BDRC still needs cleanup |
| Clean xylograph uchen | **Mostly solved** | OpenPecha: BDRC–Monlam wins Derge/Narthang; BigUchan ~5–7% | Damaged/Mongolian prints fail |
| Handwritten uchen | **Partial** | Namgyal PyLaia 1.9% in-domain; BDRC HTR-Base | Domain = that collection |
| Umê drutsa / betsug | **Partial, in-domain** | TibSchol 1.40% / 3.6%; PaganTibet Ume-2 **5.56%** after 900 pp. | Off-the-shelf “performs poorly” on a new corpus |
| Gold-on-indigo (*mthing shog*) | **Unsolved in OCR lit.** | Palaeography exists; **zero** OCR CERs found | — |

[FACT] Meelen & Griffiths, JOHD 11:54 (3 Nov 2025, [doi.org/10.5334/johd.388](https://doi.org/10.5334/johd.388)): on ~100k mixed umê pages, TibSchol Drutsa and the BDRC app **lost** a 10-page held-out test to a corpus-trained model (490 pp. → **6.99%** CER; 900 pp. → **5.56%**). **178,263 line corrections in 12 months** with specialist monk annotators. That is the real cost of “ancient manuscript” umê. [FACT] BDRC (2024) lists **20 etic OCR classes / 48 literary scripts / 108 sampled scripts**. “Tibetan OCR” as one model is a category error.

### 3. Layout

[FACT] Pecha (long folio, *yig mgo*, side titles, optional interlinear *mchan*) is a first-class problem.

Namsel has `page_type=pecha|book`. TibSchol “Tibetan Pecha” (1,699 folios) detects **horizontal baselines only** — not columns, not gold-on-dark. BDRC **Photi** labels background/image/line/margin/caption; PhotiLines masks lines (Dunhuang, Matho, Tabo). Esukhia 2019 Derge line-masks: U-Net “unsatisfactory” ([Zenodo 3245757](https://zenodo.org/records/3245757)). PKLAD: **212** Peking Kangyur pages, SOLOv2 ([IEEE](https://ieeexplore.ieee.org/document/9615155/)). OpenPecha polygon set: Transkribus-derived, 10k–100k scale. Namgyal: 100 pages with lines/images/captions/marginalia. JOHD 2025: TibSchol layout failed on colour, drawings, tables, borders; fine-tune 900 → 7,212 → **15,006** pages (Transkribus layout “mAP” 7.43→4.8→5.43, *lower=better* in their UI). Newspaper HTR (Erhard, RET 74) needed specialised field models.

[FACT] **No evaluated pipeline** for gold/silver on dark *mthing shog*. Interlinear small script is only weakly covered as extra baselines. Illustrated/multi-column folios still need per-collection GT.

### 4. Training data

HuggingFace viewer totals unless noted. Printed uchen is data-rich; public umê is **~100× smaller**, and umê *test* splits are tiny.

| Dataset | Size | What | Licence (as published) |
|---|---|---|---|
| [OCR-Norbuketaka](https://huggingface.co/datasets/openpecha/OCR-Norbuketaka) | **2.24M** lines | Modern typeset | Images via BDRC/Monlam S3 |
| [OCR-Google_Books](https://huggingface.co/datasets/openpecha/OCR-Google_Books) | **751k** | Google Books; **not for handwriting** | Model [GoogleBooks_C_v1](https://huggingface.co/BDRC/GoogleBooks_C_v1) **cc-by-4.0** |
| [OCR-Lhasakanjur](https://huggingface.co/datasets/openpecha/OCR-Lhasakanjur) | **161k** | Woodblock | BDRC-associated |
| Lithang / Derge (BDRC 2024 blog) | ~500k / ~800k claimed | Xylograph | Partial HF |
| Unified uchen (same blog) | **4.4M** samples | Mixed uchen | Internal + partial HF |
| [OCR-Drutsa](https://huggingface.co/datasets/openpecha/OCR-Drutsa) | **32,364** (10 MSS) | Handwritten drutsa | **odc-by** |
| [OCR-Betsug](https://huggingface.co/datasets/openpecha/OCR-Betsug) | **28.3k** | Betsug | Card incomplete |
| [OCR-Handwritten_Tibetan_Cursive](https://huggingface.co/datasets/openpecha/OCR-Handwritten_Tibetan_Cursive) | **70,528** | Cursive | Empty YAML card |
| [line-to-text benchmark](https://huggingface.co/datasets/openpecha/OCR-Tibetan_line_to_text_benchmark) | **422k** eval | **Drutsa 595 / Betsug 1,220** | Test-only |
| TibSchol GT | 466+93 **folios of text** | Wylie | **CC0-1.0; images not included** |
| TMUP 0.1 | 522 pages | Modern uchen print | [doi.org/10.48796/20240313-000](https://doi.org/10.48796/20240313-000) |
| PaganTibet Ume GT | ~900 pages | Umê | [Zenodo 17275724](https://doi.org/10.5281/zenodo.17275724) |
| Namgyal | line pairs + PageXML | Early uchen MSS | Zenodo 14247731 |

[FACT] Scan copyright often stays with BDRC/libraries even when labels are ODC-By or CC-BY.

### 5. Ten thousand unpublished Sakya images

Sakya xylograph/MS mix unknown.

**Mostly clean uchen woodblock:** BDRC app + PhotiLines; no new engine. Large fraction searchable; editions still need a human pass. **~3–6 person-months** for pipeline, QC sampling, post-correction.

**Mixed monastery pile:** classify with BDRC’s script net; uchen xylograph → Woodblock/BigUchan; umê → Drutsa/Betsug **then fine-tune**. [SPECULATION] Scholarly-usable off-the-shelf (CER ≲5%): **20–50%**. JOHD calibration: 900 triple-checked pages to 5.56% on *their* umê, plus 15k layout pages.

**Ornate umê / gold-on-dark / heavy *mchan*:** off-the-shelf conversion **near zero**. PaganTibet-class work: specialist readers, diplomatic conventions, year-scale annotation.

**Build (not a new recogniser):** intake/deskew; script routing; pecha layout incl. interlinear; 500–2,000 Sakya umê GT pages if umê matters; fine-tune BDRC or Transkribus; LM post-correct that does **not** silently classicalise; human QA. **6–18 person-months** mixed; **12–24** hard umê. Reusing BDRC weights is the difference between those numbers and a multi-year OCR lab.

## Sources

| URL | What it is | Lang. | Reliability |
|---|---|---|---|
| https://escholarship.org/uc/item/6d5781k5 | Namsel 2016, primary CER | EN | high |
| https://github.com/max-lancaster/namsel | Namsel code | EN | high |
| https://www.bdrc.io/blog/2024/08/28/transforming-tibetan-text-digitization-bdrcs-groundbreaking-ocr-project/ | BDRC OCR programme, dataset sizes | EN | high |
| https://www.bdrc.io/blog/2025/03/14/bdrc-announces-the-release-of-ocr-app-for-tibetan/ | App release | EN | high |
| https://github.com/buda-base/tibetan-ocr-app | Open OCR app | EN | high |
| https://huggingface.co/BDRC | Models (Photi, Woodblock, Drutsa…) | EN | high |
| https://forum.openpecha.org/t/the-current-state-of-tibetan-ocr-bdrc-and-monlam-ai/146 | Model/data inventory | EN/BO | high |
| https://forum.openpecha.org/t/report-ocr-benchmark/429 | 2025 pecha bake-off | EN | high |
| https://arxiv.org/html/2304.03427v2 | Google OCR 25%→12.26% CER | EN | high |
| https://fairbank.fas.harvard.edu/research/blog/norbu-ketaka-tibetan-manuscripts/ | Norbu Ketaka | EN | high |
| https://www.oeaw.ac.at/fileadmin/Institute/IKGA/project_tibschol/PDFs/Online_documents/TibSchol_HTR_tools_v2_1.pdf | TibSchol IDs + CERs | EN | high |
| https://www.transkribus.org/models/tibetan-pecha | Pecha layout model | EN | high |
| https://doi.org/10.5334/johd.388 | JOHD 2025 umê transfer + 5.56% | EN | high |
| https://d1i1jdw69xsqx0.cloudfront.net/digitalhimalaya/collections/journals/ret/pdf/ret_79_03.pdf | Namgyal/TMPV CERs | EN | high |
| https://zenodo.org/records/14247731 | Namgyal data/models | EN | high |
| https://huggingface.co/datasets/openpecha/OCR-Norbuketaka | 2.24M modern lines | EN/BO | high |
| https://huggingface.co/datasets/openpecha/OCR-Google_Books | 751k Google Books lines | EN | high |
| https://huggingface.co/datasets/openpecha/OCR-Lhasakanjur | 161k xylograph lines | EN/BO | high |
| https://huggingface.co/datasets/openpecha/OCR-Drutsa | 32k drutsa, odc-by | EN/BO | high |
| https://huggingface.co/datasets/openpecha/OCR-Betsug | 28k betsug | EN/BO | med |
| https://huggingface.co/datasets/openpecha/OCR-Handwritten_Tibetan_Cursive | 70.5k cursive | EN/BO | med |
| https://huggingface.co/datasets/openpecha/OCR-Tibetan_line_to_text_benchmark | 422k eval; tiny umê tests | EN | high |
| https://github.com/ERC-TibSchol/Tibetan-cursive-GT | TibSchol GT, CC0, no images | EN | high |
| https://digitaltibetan.github.io/DigitalTibetan/docs/tibetan_ocr.html | Tesseract vs Google (2023) | EN | med |
| https://ieeexplore.ieee.org/document/9615155/ | PKLAD layout, 212 pp. | EN | high |
| https://zenodo.org/records/3245757 | Esukhia 2019 pecha masks | EN | med |
| https://www.bdrc.io/blog/2026/02/28/bdrc-launches-major-initiative-to-build-open-buddhist-datasets-for-ai/ | 26M pages processed | EN | high |
| https://tech.ldas.jp/en/posts/bac0870d56a3c3/ | 90–95% woodblock acc. | EN/JA | med |
| https://doi.org/10.3724/2096-7004.di.2025.0140 | TibOCR-Bench / Tesseract 84.5 | ZH/EN | med |

## Gaps and what would settle them

- OpenPecha bake-off **per-dataset BDRC CER** lives in a spreadsheet, not the forum post. Quote Derge vs TibSchol-umê rows.
- **No GPT/Claude/Qwen-VL pecha CER** on the OpenPecha protocol. Run [OCR-Evaluation-Toolkit](https://github.com/OpenPecha/OCR-Evaluation-Toolkit) once.
- **Gold-on-dark:** ten annotated deluxe folios would show whether inversion + Woodblock is salvageable.
- **Sakya script mix** is unknown here. A 100-image sample into BDRC’s eight coarse classes turns 20–50% into a measurement.
- Public umê tests are tiny. **Fifty held-out Sakya umê folios** would beat every published transfer number.
- Image licences behind OpenPecha S3: labels may be open while scans are not redistributable. Ask BDRC in writing.

## Implication for the open-source project

- **AGAINST a new OCR/HTR engine.** BDRC+Monlam (open weights, desktop app), TibSchol/PaganTibet on Transkribus, and millions of uchen lines already exist.
- **FOR a thin pipeline that calls those tools:** ingest → Photi layout → script classifier → BDRC zoo → optional Transkribus umê → diplomatic LM post-correct → CER dashboard on a Sakya GT sample.
- **Design:** **script routing is the product**, not one model. Xylograph uchen and umê cursive are different paths.
- **Design:** budget **human GT by Tibetan-script readers** if unpublished Sakya material is umê. Plan from JOHD’s 900 pages / 5.56% CER, not TibSchol’s 1.4%.
- **NEUTRAL-to-FOR layout work** only if scans have interlinear commentary, tables, or deluxe dark-paper leaves — those pixels are still unsolved.
- **Do not bet on Gemini/GPT reading pecha.** Specialised OCR wins; VLMs hallucinate.
