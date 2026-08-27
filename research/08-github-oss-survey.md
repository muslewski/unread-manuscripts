# Existing open-source code in Tibetan text/NLP/translation

GitHub stars, licenses, and `pushed_at` dates were read from the GitHub REST API on **2026-08-27**. “Alive” = a push in the last ~12 months.

## Verdict

- **1. The stack already exists.** Tokenization, OCR, etext packaging, parallel corpora, and MT are shipped by OpenPecha, BDRC (`buda-base`), Dharmamitra, 84000, and Monlam AI. A greenfield “Tibetan NLP + AI translation” org would duplicate work. [FACT]
- **2. OpenPecha is the closest “this already exists” answer — and it does not do the imagined job.** Live 539-repo org, ~9,531 data repos, STAM/OPF model, Botok, a 1-star translation workstation. 2025–26 commits are a consumer pivot (WeBuddhist / Sherab), not a factory for uncatalogued manuscripts. [FACT] / [SPECULATION] on product intent
- **3. Gaps are docs, licenses, onboarding, and one missing dump — not missing tokenizers.** `help wanted` is junk; `good first issue` is empty; most key repos lack `CONTRIBUTING.md`; Dharmamitra’s advertised Tibetan GitHub repo 404s. [FACT]
- **4. Outsiders can contribute via Discord/forum/email, not a clean PR ladder.** OpenPecha Discord + forum exist; BDRC and Dharmamitra take issues; 84000 TEI is CC BY-NC-ND. [FACT]
- **5. A new repo should be (b) a thin layer on existing infra.** Another Botok/OCR/MT/catalog is **(a) redundant**. Any remaining hole is corpus access + scholarly QA, not OSS code. [FACT] on duplication; [SPECULATION] on design

## Findings

### 1. Significant orgs and repos

Core living stack:

| Repo | ★ | Last push | License | Role | Alive |
|---|---|---|---|---|---|
| [OpenPecha](https://github.com/OpenPecha) org (539 repos) | — | WeBuddhist 2026-08-27 | mixed | NLP + data + “AI meets Buddhist wisdom” apps | Y |
| [OpenPecha/Botok](https://github.com/OpenPecha/Botok) | 80 | 2026-07-22 | Apache-2.0 | Default Tibetan tokenizer (`pip install botok`) | Y |
| [OpenPecha/pybo](https://github.com/OpenPecha/pybo) | 43 | 2026-04-02 | Apache-2.0 | Older CLI; Botok is the successor | Y |
| [OpenPecha/pyewts](https://github.com/OpenPecha/pyewts) | 33 | 2026-07-27 | Apache-2.0 | Unicode ↔ EWTS/ACIP | Y |
| [OpenPecha/toolkit-v2](https://github.com/OpenPecha/toolkit-v2) | 0 | 2025-10-29 | MIT | STAM/OPF (`pip install openpecha`) | borderline |
| [OpenPecha/Pydurma](https://github.com/OpenPecha/Pydurma) | 2 | 2026-03-26 | MIT | Collation / auto variant selection | Y |
| [OpenPecha/buddhistAI-translation](https://github.com/OpenPecha/buddhistAI-translation) | 1 | 2026-05-01 | none | Translation workstation | Y, unused |
| [OpenPecha/WeBuddhist](https://github.com/OpenPecha/WeBuddhist) | 4 | 2026-08-03 | MIT | Reader/practice app; [pecha.org](https://pecha.org) 301s to [webuddhist.com](https://webuddhist.com/) | Y |
| [OpenPecha-Data](https://github.com/OpenPecha-Data) | 9,531 repos | catalog 2025-04-17 | none | One git repo per pecha; `opf_catalog.csv` **27,740** rows, `work_catalog.csv` **83,545** | catalog aging |
| [buda-base/tibetan-ocr-app](https://github.com/buda-base/tibetan-ocr-app) | **67** | 2025-12-15 | MIT | Desktop OCR; v0.3.0 2025-06-08; models on [HF/BDRC](https://huggingface.co/BDRC) | Y |
| [buda-base](https://github.com/buda-base) (166 repos) | — | 2026-08-26 | mixed | Library UI (376 open issues), Lucene-bo, etext tools | Y |
| [dharmamitra/mitra-parallel](https://github.com/dharmamitra/mitra-parallel) | 13 | 2026-08-04 | CC BY-SA 4.0 | v2: **1,693,730** sa–bo / sa–zh / zh–bo pairs | Y |
| [dharmamitra/dharmamitra-claude-code-agent](https://github.com/dharmamitra/dharmamitra-claude-code-agent) | 7 | 2026-06-20 | none | `/translate` + `/critical-edition` over their APIs | Y |
| [billingsmoore/MLotsawa](https://github.com/billingsmoore/MLotsawa) | 14 | 2026-07-18 | models MIT | T5 bo→en; UVA THL | Y |
| [84000/data-tei](https://github.com/84000/data-tei) | 6 | 2025-02-16 | **CC BY-NC-ND 3.0** | Human Kangyur TEI | Y |
| [cbeta-org/xml-p5](https://github.com/cbeta-org/xml-p5) | 74 | 2026-05-10 | CBETA | Chinese-canon git XML analogue; **not Tibetan** | Y |

Also alive, narrower: [Esukhia/bophono](https://github.com/Esukhia/bophono) (23★, 2025-12-28, MIT, phonetics); [84000](https://github.com/84000) org (13 repos, TEI+TM, last push 2026-08-27); [MonlamAI](https://github.com/MonlamAI) (**4,297** repos, almost no stars — training shards, [monlam.ai](https://monlam.ai)); [Divergent-Discourses](https://github.com/Divergent-Discourses) (27 repos, 2026-08-02) — 1950s–60s **newspapers**, wrong corpus.

Dead or archived: [Esukhia/derge-kangyur](https://github.com/Esukhia/derge-kangyur) (13★, archived 2022; “moved to OpenPecha/P000001”, which last pushed **2022-06-01**); [Esukhia/derge-tengyur](https://github.com/Esukhia/derge-tengyur) (2021-10-20); [Esukhia/Corpora](https://github.com/Esukhia/Corpora) (25★, 2023-04-10); [tibetan-nlp/awesome-tibetan-nlp](https://github.com/tibetan-nlp/awesome-tibetan-nlp) (46★, **2020-07-15**); [tibetan-nlp/classical-tibetan-corpus](https://github.com/tibetan-nlp/classical-tibetan-corpus) (31★, 2021); [CompassionAI/lotsawa](https://github.com/CompassionAI/lotsawa) (1★, 2023-10-17, GPL-3.0); [BuddhaNexus](https://github.com/BuddhaNexus) main app archived (Dharmamitra successor).

**SAT Daizōkyō.** [FACT] Live *web* platform ([SAT2018](https://21dzk.l.u-tokyo.ac.jp/SAT2018/master30.php)), not a GitHub etext org. No SAT XML dump comparable to CBETA `xml-p5` showed up in GitHub search.

**ACIP.** [FACT] No GitHub org. Derge etexts they keyed are reused by Esukhia’s archived repos, Dharmamitra (docs cite ACIP), [Steinert’s archive](https://acip-archive.christian-steinert.de/), and Asian Legacy Library. Successor is ALL, not code.

**Independent AI canon dump.** [FACT] [Buddhist-Classics-AI-Translation-Series](https://github.com/Buddhist-Classics-AI-Translation-Series/Buddhist-translations) (4★, 2026-03-17) claims complete AI Kangyur/Tengyur English. Quality unverified. That is a warning, not a hole.

### 2. OpenPecha

**Data model.** [FACT] The 2020 ACM paper ([Hill & Trinley](https://dl.acm.org/doi/fullHtml/10.1145/3418060)) defined git-hosted Tibetan etexts with stand-off OPF annotations. Toolkit v2 still does that: Pecha = UUID + `base/` + STAM layers. README states **Firebase**, not git, is the storage backend. [OpenPecha-Data](https://github.com/OpenPecha-Data): 9,531 public repos; catalog README is **10 MB**; last catalog push **2025-04-17**.

**Product now.** [FACT] Org bio: “We are actively building an app where AI meets Buddhist wisdom.” [openpecha.org](https://openpecha.org): “Open-Source Foundation for Buddhist Technology.” 2025-09-30 working-group post prioritizes WeBuddhist apps, creator partnerships, Sherab e-learning, and a Buddhist Open Data API ([forum](https://forum.openpecha.org/t/openpecha-projects-working-groups/485)). Esukhia lists OpenPecha, BDRC, Monlam AI, Berkeley as partners ([esukhia.net](https://esukhia.net/digital-resources)). Contact: `contact@dharmaduta.in`.

**Openness.** Mixed. Botok/toolkit/pyewts are Apache/MIT. Many product repos have **no LICENSE**. Wiki ([wiki.openpecha.org](https://wiki.openpecha.org)) is an “internal wiki… whether you’re new to the team.” `P000001` (the Derge Kangyur the archive README points to) is frozen at 2022.

**Does it already do the imagined project?** **No.** [FACT] No OpenPecha product sources inaccessible monastery holdings, OCRs them, and emits scholar-reviewed English. There *is* a 1-star translation workstation, OCR data collabs with BDRC/Monlam (Lhasa Kanjur ~160k lines, Lithang ~500k, Derge Kanjur ~800k — [BDRC 2024-08-28](https://www.bdrc.io/blog/2024/08/28/transforming-tibetan-text-digitization-bdrcs-groundbreaking-ocr-project/)), and WeBuddhist as a reader for already-digital scripture. [SPECULATION] They are building a Buddhist-wisdom app, not a Sakya-unknown-text pipeline.

**Funding.** [FACT] Historical: Khyentse Foundation USD 22,000 for pybo (pybo README); Barom/Esukhia canon; BDRC staff. Current partners as above. Grant ledgers not audited here.

### 3. Gaps an outsider could fill

- **Dharmamitra Tibetan dump is advertised and missing.** Docs: “complete Tibetan data” at `github.com/dharmamitra/dharmanexus-tibetan` ([guide](https://dharmamitra.github.io/dharmamitra-guides/dharmanexus/)). That URL **404s**. Sanskrit/Chinese/Pāli dumps exist.
- **OpenPecha-Data is unusable at catalog scale.** 27k OPF rows, 9.5k repos, 10 MB README-as-catalog, no LICENSE. A parquet/index would beat a new NLP library.
- **Botok lives; its issue tracker does not.** #109 “dialectpack for modern Tibetan” (2024-11, unlabelled); #108 “催更帮助文档” (2024-03). Last commit 2026-07-22 is a tokenizer fix.
- **BDRC OCR app (67★, highest-starred Tibetan tool here)** has real tickets: PDF rotation (#66), mixed Chinese/Tibetan (#29), train-your-own-model (#44), Windows packaging (#15), CLI/API (#22).
- **toolkit-v2** 45 open issues; last release **2025-10-29** while WeBuddhist is daily. Docs issue #380 still open.
- **`help wanted` is not a signal.** Hits are 2024 `monlam-apps-roadmap` tickets titled “hi hello how are you.” `good first issue`: **[]**. [OpenPecha/Requests](https://github.com/OpenPecha/Requests) has 180 open RFCs; sampled titles last updated **2024**.
- **Licenses / ToS.** 84000 TEI is **CC BY-NC-ND** (no derivatives). Dharmamitra [ToS](https://dharmamitra.github.io/dharmamitra-guides/dharmanexus/) forbids using their API “to populate third-party applications.”
- **Not missing:** another tokenizer, OCR trainer, T5, or parallel corpus.

### 4. Contribution paths

| Project | How | Links |
|---|---|---|
| OpenPecha | Discord + forum + issues. No `CONTRIBUTING.md` on Botok, toolkit-v2, WeBuddhist. Translation WG points at Good First Issues that do not exist. | [discord invite](https://discord.com/invite/7GFpPFSTeA), [forum.openpecha.org](https://forum.openpecha.org), [wiki](https://wiki.openpecha.org), [Requests](https://github.com/OpenPecha/Requests) |
| BDRC | Issues on `tibetan-ocr-app` / library. No org CONTRIBUTING.md found. HF is the data surface. | [github.com/buda-base](https://github.com/buda-base) |
| Dharmamitra | Email. Public APIs; **ToS bans third-party apps**. Claude pack is the intended shape. | dharmamitra.project@gmail.com |
| 84000 | TEI theoretically PR-able; NC-ND. Translation work is commissioned humans, not OSS. | [github.com/84000](https://github.com/84000) |
| Monlam AI | No public contributor guide found. Partner forge, not a community. | [github.com/MonlamAI](https://github.com/MonlamAI) |
| MLotsawa | Single maintainer; 0 issues; repo being split. | [MLotsawa](https://github.com/billingsmoore/MLotsawa) |
| Esukhia | Zoom office on org README; Kangyur archived. | [github.com/Esukhia](https://github.com/Esukhia) |

### 5. Pick, defended

**(b) thin layer on existing infra.**

**(a)** holds for any reimplementation of Botok, BDRC OCR, OPF, mitra-parallel, or MLotsawa. Those are live and used. Dharmamitra already ships an *agentic* translation + critical-edition starter over canonical etexts.

**(c)** is false as an OSS-code claim. The hole is not “nobody wrote Tibetan NLP.” If there is a hole, it is *access to a holding* plus *review*. CBETA-style git XML for Tibetan already had a 2014–2018 Esukhia push and then stalled in OpenPecha-Data (`P000001` frozen 2022).

**(b)** is the only honest build: glue BDRC OCR → OPF via toolkit-v2 → optional MLotsawa draft → human log. Do **not** wrap DharmaMitra into a product (ToS).

## Sources

| URL | What | Lang | Rel. |
|---|---|---|---|
| https://github.com/OpenPecha | Org, 539 repos, Discord | en | high |
| https://github.com/OpenPecha/Botok | Tokenizer stats | en | high |
| https://github.com/OpenPecha/toolkit-v2 | STAM/OPF + Firebase | en | high |
| https://github.com/OpenPecha-Data/catalog | 27,740 / 83,545 CSV rows | en | high |
| https://openpecha.org | Product site | en | high |
| https://wiki.openpecha.org | Internal wiki | en | med |
| https://discord.com/invite/7GFpPFSTeA | Discord | en | high |
| https://forum.openpecha.org/t/openpecha-projects-working-groups/485 | WG map, 2025-09-30 | en | high |
| https://dl.acm.org/doi/fullHtml/10.1145/3418060 | 2020 OpenPecha paper | en | high |
| https://github.com/Esukhia/derge-kangyur | Archived Kangyur | en | high |
| https://esukhia.net/digital-resources | Partner list | en | high |
| https://github.com/buda-base/tibetan-ocr-app | OCR app 67★ | en | high |
| https://www.bdrc.io/blog/2025/03/14/bdrc-announces-the-release-of-ocr-app-for-tibetan/ | OCR announcement | en | high |
| https://www.bdrc.io/blog/2024/08/28/transforming-tibetan-text-digitization-bdrcs-groundbreaking-ocr-project/ | OCR dataset sizes | en | high |
| https://huggingface.co/BDRC | OCR models | en | high |
| https://github.com/dharmamitra/mitra-parallel | Parallel v2 | en | high |
| https://github.com/dharmamitra/dharmamitra-claude-code-agent | Agent pack | en | high |
| https://dharmamitra.github.io/dharmamitra-guides/dharmanexus/ | Tibetan GitHub 404 + ToS | en | high |
| https://github.com/84000/data-tei | TEI NC-ND | en | high |
| https://github.com/billingsmoore/MLotsawa | Edge MT | en | high |
| https://github.com/cbeta-org/xml-p5 | Chinese git XML | zh/en | high |
| https://github.com/MonlamAI | 4,297 repos | en/bo | med |
| https://github.com/tibetan-nlp/awesome-tibetan-nlp | Stale 2020 list | en | med |
| https://github.com/CompassionAI/lotsawa | Stale 2023 MT | en | med |
| https://github.com/Buddhist-Classics-AI-Translation-Series/Buddhist-translations | Independent AI dump | en/zh | med |
| https://21dzk.l.u-tokyo.ac.jp/SAT2018/master30.php | SAT platform | ja/en | high |
| https://acip-archive.christian-steinert.de/ | ACIP Release 6 | en | med |
| https://github.com/BuddhaNexus | Archived predecessor | en | high |
| https://pecha.org | 301 → WeBuddhist | en | high |

## Gaps and what would settle them

- **OpenPecha-Data vs BDRC/ACIP coverage.** Counted CSV rows, not OPF quality. *Settle:* sample N P-ids against BDRC etexts.
- **`dharmanexus-tibetan` private, renamed, or never published?** *Settle:* email dharmamitra.project@gmail.com.
- **Monlam weights actually downloadable?** HF org API returned empty without auth. *Settle:* inspect `monlamai-API` + HF with a token.
- **Firebase vs git as source of truth.** *Settle:* read `openpecha-backend`.
- **Buddhist Classics AI quality.** *Settle:* chrF vs 84000 on a few Tohoku IDs (out of this slice).
- **SAT bulk XML terms.** *Settle:* SAT download page (Japanese).

## Implication for the open-source project

- **AGAINST a new full-stack repo.** Botok, BDRC OCR, OPF, mitra-parallel, MLotsawa, Dharmamitra agents occupy every layer.
- **AGAINST “just contribute to OpenPecha and you’re done.”** They pivoted to WeBuddhist. Catalog is messy. Contributor UX is Discord-shaped. Kangyur git is frozen at 2022.
- **AGAINST wrapping DharmaMitra as the product.** ToS forbids populating third-party apps.
- **FOR a thin orchestration layer** only if target *images* are legally obtainable: BDRC OCR → OPF → optional MLotsawa draft → human review. Glue, not 539 more packages.
- **FOR contributing upstream first** (BDRC OCR issues, Botok modern dialect, Dharmamitra Tibetan dump). That tests whether anyone here will work in this ecosystem.
- **NEUTRAL on “AI + scholarship” as a slogan.** Dharmamitra’s Claude pack already *is* that slogan for canonical etexts. A new repo is justified only if there is a corpus those projects cannot touch.
