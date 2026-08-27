# Who has already digitized Tibetan texts, and is Sakya among them

## Verdict

- **BDRC is the global scan/etext backbone.** [FACT] Live banner: “over 35 million pages” ([library.bdrc.io](https://library.bdrc.io/)). [FACT] 2024 talk by director Jann Ronis: ~30M images, ~25M Tibetan ([YouTube](https://www.youtube.com/watch?v=4JKdUKC7K7I)). Access is mixed: free account for PD PDFs; guests get first+last 20 pages; copyright, “sealed,” and embargoed works are restricted ([access policies](https://www.bdrc.io/access-policies/)). IIIF and Linked Data APIs are live. **No bulk image dump.**
- **BDRC does not hold the Sakya Monastery wall.** [FACT] Place record `bdr:G880`; a 5-volume 2018 *catalogue* of the Gorum library (`WA3CN8601`/`MW3CN8601`) scanned in TAR, IIIF behind login; reprints of Sakya *authors* (e.g. *sa skya bka' 'bum*); a 2015 Potala *catalogue* of Sakya-school texts (`MW3CN5011`, copyright-restricted). None of these are the wall manuscripts.
- **Other archives cover the canon, Dunhuang, and Nepal — not Sakya.** [FACT] ACIP/ALL Kangyur–Tengyur–Sungbum etexts are public domain ([ALL](https://asianlegacylibrary.org/library/downloads/)). Esukhia Derge etexts are public domain. Adarsha is a searchable Jiang/Derge reader. IDP digitizes Dunhuang Tibetan; NGMPP microfilmed ~1/5 of 180,000 Nepal MSS in Tibetan, no bulk download.
- **PRC digitization of Sakya is real, internal, incomplete, and not public.** [FACT] Officials: cataloguing done by 2020; ~20% leaf-scanned by 2022, by monks; wall still unfunded ([People’s Daily, 2022-03-01](http://xz.people.com.cn/n2/2022/0301/c138901-35154373.html)). [FACT] March 2026: the same official still petitioning for a *national* digitization special project ([china.com.cn](http://cul.china.com.cn/2026-03/11/content_43370134.htm)). TAR/NLC public portals do not serve the wall.
- **Obtainable today: no for Sakya-unique MSS; yes at scale for circulating Tibetan literature.** [FACT] Public wall/palm-leaf images ≈ 0. Public Sakya-*tradition* reprints on BDRC = thousands of volumes already in print canons. The untranslated bulk that *is* obtainable is BDRC extra-canonical Tibetan plus the Tengyur (84000: 0.7% published in English as of 2026).

## Findings

### 1. BDRC (formerly TBRC)

**Scale.** [FACT] Dec 2021: 20 Kangyur editions, 6 Tengyur, gsung 'bum of 600+ masters, “over 27,000 blockprint volumes and 27,000 modern publications” ([bdrc.io](https://www.bdrc.io/blog/2022/01/06/dharma-jewels-online-the-bdrc-collections/)). [FACT] Ronis 2024: 30M / 25M Tibetan. [FACT] BUDA 2026 banner: 35M pages. SPARQL `AO_volumePagesGrandTotal` returned HTTP 500 on 2026-08-27 (Fuseki), so a machine total could not be re-counted.

**Open vs restricted.** [FACT] Policy last clarified 2019 after Harvard counsel ([access policies](https://www.bdrc.io/access-policies/)): BDRC owns no copyrights. Old xylographs/MSS = public domain, full PDF for registered users. Modern computer-input reprints = restricted. “Sealed” tantras blocked at holders’ request. Unauthenticated IIIF of the Gorum-catalogue thumbnail returned IIIF Auth at `library.bdrc.io/iiifcookielogin`.

**OCR / etext.** [FACT] Ronis 2024: ~5M etext pages; “20 more million images to OCR” then beyond the tech. [FACT] 28 Feb 2026 Khyentse grant: “more than 26 million Tibetan images have been processed through OCR pipelines”; datasets/models to be released **public domain** on Hugging Face through summer 2027 ([blog](https://www.bdrc.io/blog/2026/02/28/bdrc-launches-major-initiative-to-build-open-buddhist-datasets-for-ai/)). Existing HF *models* are CC-BY-NC-4.0; some *datasets* ODC-By/CC-BY. [SPECULATION] 26M internally OCR’d ≠ 26M clean public etexts until that dump ships.

**IIIF / API / dumps / license.** [FACT] Image API v2.1 at `iiif.bdrc.io`; PDF/ZIP job API ([API.md](https://github.com/buda-base/buda-iiif-server/blob/master/API.md)); presentation `iiifpres.bdrc.io`. Linked Data: `ldspdi.bdrc.io/resource/{id}.ttl` plus SPARQL *templates*, not an open playground. [FACT] 2017 Harvard poster: TBRC RDF migrated “under CC0.” [FACT] No current bulk RDF or image dump URL found. [FACT] IA collection `buddhist-digital-resource-center` = **30,084** items (2026-08-27); mix of openAccess / fairUse / geo-restricted. Platform: 160+ repos at [github.com/buda-base](https://github.com/buda-base) (MIT/Apache-2.0). Harvard DRS deposit in progress.

**Sakya in the catalogue.** [FACT] `bdr:G880` = Sakya monastery / 萨迦寺, founded 1073. [FACT] `WA3CN8601`: “Catalog of Sakya monastery Gorum library,” 5 vols, 2018, publisher `sa skya sgo rum rig gnas rtsom sgrig khang`, `CopyrightUndetermined`, computer-input, image groups `I3CN21135`–`I3CN21139` — a *finding aid*, not the wall. [FACT] `MW3CN5011`: 2015 Potala catalogue of Sakya-school holdings, 621 pp., IA Open Library / fair use. [FACT] *sa skya bka' 'bum* etexts (e.g. `MW00EGS1017151`) are Indian/modern reprints of the Five Founders.

Partner collections on BDRC (none = the wall): NLM `PR1NLM00` 5,897 vols online Mar 2023 (~20% of NLM Tibetan); ALL/NLM 2022–25 added 4,383 vols / 1.44M pages; LTWA 420 vols / 216,444 images (2024); CIHTS Himalayan scans; PL480 ~6,000 Indian reprint vols.

### 2. Other archives

| Project | Holds | License / access |
|---|---|---|
| **Adarsha** | [FACT] Jiang+Derge Kangyur etext, partial Tengyur ([kagyuoffice](https://kagyuoffice.org/digitization-of-the-dharma/)). Not unique-MSS images. | Online app. [CLAIM] no bulk dump/license found. |
| **ACIP → ALL** | [FACT] Kangyur 28.7 MB, Tengyur 69 MB, Sungbum 80.2 MB; ALL waives copyright ([downloads](https://asianlegacylibrary.org/library/downloads/)). | PD. |
| **Esukhia / eKangyur** | [FACT] Proofread Derge Kangyur (from 2013 UVA–SOAS) + Tengyur; now OpenPecha `P000001`. “Public Domain.” | PD, GitHub. |
| **THL (UVa)** | [FACT] Multimedia + literary encyclopedia; LoC Derge Kanjur scans went to BDRC ([LoC guide](https://guides.loc.gov/tibetan-collection/digital-collections)). | Academic, mixed. |
| **RY Wiki Texts** | [FACT] 5,650 wiki pages ([rywikitexts](https://rywikitexts.tsadra.org/index.php/Main_Page)). | Wiki, not a scan archive. |
| **Internet Archive** | [FACT] 30,084 BDRC items; 2018 BDRC–IA partnership. | Per-item PD / copyright / fair use. |
| **IDP** | [FACT] ~155k catalogue entries / 114k digitised (2026-01-01). BL Stein ~3,100 Tibetan Cave 17 items; BnF Pelliot Tibetan 4,174 ([idp.bl.uk](https://idp.bl.uk/about/projects/tibetan-manuscripts/)). | Free view. Not Sakya. |
| **NGMPP/NGMCP** | [FACT] 1970–2001: >180k MSS / ~5M folia; ~1/5 Tibetan ([Hamburg](https://www.aai.uni-hamburg.de/en/forschung/ngmcp/history/history.html)). Kathmandu or SBB Berlin; **no new film copies**. Some 15th–16th-c. films on BDRC as `PR1TIBET00` (Cambridge). | Catalogue open; not bulk-open. |
| **Cambridge / Bodleian** | [FACT] Cambridge via NGMPP on BDRC. Bodleian: small set; Digital Bodleian has Richardson pillar copies. | Tiny vs BDRC. |
| **84000** | [FACT] English canon translations. Kangyur 32,632 pp published (50%), 80% translated; Tengyur 859 pp (0.7%) ([progress](https://84000.co/progress-and-impact), 2026). | Free to read. |
| **Lotsawa House** | [FACT] >6,000 translations, 9 languages. | Free; not scans. |
| **CIHTS** | [FACT] Tawang, Lithang, Peking, Narthang, Derge, Gondhla, Tabo Kangyur/Tengyur scans ([cihts.ac.in](https://cihts.ac.in/multimedia-section/)); shared with BDRC. | Institutional. |
| **OpenPecha** | [FACT] OPF etexts of BDRC/Google-OCR works. | Apache-2.0 toolkit; text licenses follow sources. |

### 3. PRC-side digitization

**Sakya Monastery.** [FACT] Monk-run scan group 2011–2012. 2017 Xinhua: ~6,000 scriptures scanned since 2012; a monk said photocopies *could* be shared after archiving ([Xinhua](http://news.xinhuanet.com/english/2017-10/12/c_136674892.htm)) — no portal then, none found now. [FACT] 2022-03-01, 洛卓加措: 50,000+ volumes (this interview does *not* use 84,000), 21 palm-leaf MSS; catalogued by 2020; ~20% leaf-scanned; ~10,000+ volumes besides the wall; remaining wall still fundraising ([xz.people.com.cn](http://xz.people.com.cn/n2/2022/0301/c138901-35154373.html)). [CLAIM] China Daily 2025: “nearly 3,000 volumes, approximately 7,000 pages” — incompatible with the 2022 10,000-volume figure; treat as garbled English. [CLAIM] 2025 TAR feature: 100,000 pages of iron-ring scriptures — a roundup, not a dataset. [FACT] March 2026: same official proposing a national “digital twin” project ([china.com.cn](http://cul.china.com.cn/2026-03/11/content_43370134.htm)). That petition is evidence the wall is **not done** and **not a public API**.

**State programs, not Sakya-public.** [FACT] 中华古籍保护计划 / 中华古籍资源库: 10.7万+部/件, overwhelmingly Chinese-script; no Sakya-wall collection located ([nlc.cn](https://www.nlc.cn/pcab/zy/szzy/index.shtml)). [FACT] TAR “cloud share”: 212 titles / 23,116 leaves as of Apr 2021 ([Xinhua](http://www.xinhuanet.com/2021-04/23/c_1127367997.htm)). [FACT] Potala palm-leaf project 2018–2026: RMB 110.4 million; 36,000 leaves digitized; *not* Sakya, not a bulk dump ([xizang.gov.cn](https://www.xizang.gov.cn/xwzx_406/bmkx/202606/t20260615_545458.html)). [FACT] CTRC Tibetan-literature DB (2021): 12,000+ volumes, **internal network only**. Later public opening not verified. [FACT] Print series *萨迦噶彭宝典宝库* (~230 vols) 2025; digitization is a *future* step. CNKI was not queried (paywall).

### 4. Can an outside OSS project obtain Sakya Monastery’s manuscripts today?

**No for the wall and the 21 palm-leaf books. Partly for the already-published school.**

Paths that work: BDRC account (PD xylographs + circulating Sakya-author reprints); IA 30,084 BDRC items; ACIP/Esukhia/Adarsha/84000 etexts; TAR Library ~23k leaves (2021, not the wall); buy the 2018 Gorum catalogue / 2025 *噶彭宝典* print set.

Paths that do not: no Sakya IIIF/GitHub/HF/NLC wall collection; `WA3CN8601` is a login-gated catalogue; the 2017 “share photocopies” quote is unimplemented; the 2026 CPPCC proposal is the opposite of a release.

**Volume of Sakya-*monastery-attributable* images publicly downloadable now:** on the order of **zero unique wall/palm-leaf pages**. [SPECULATION] Counting every BDRC reprint whose *author* is a Sakya master yields thousands of volumes — not “hidden in Sakya,” and already in the 84000/BDRC/Esukhia stack.

### 5. If not Sakya, what *is* obtainable and still largely untranslated?

Canonical Tibetan is the solved-for-etext layer: Derge Kangyur+Tengyur exist as PD Unicode. English: Kangyur half-published; Tengyur **0.7% published**. Extra-canonical is the real bulk.

Pullable today: ~25 million Tibetan BDRC images (2024), PD xylographs/MSS with a free account, modern reprints legally blocked, no tarball; ~5 million etext pages, 2026–27 PD OCR dump promised; NLM 1.4M pages in the 2022–25 ALL tranche, ~80% of NLM Tibetan still offline as of 2023; ACIP Sungbum 80.2 MB PD, mostly untranslated; LTWA 216k images; CIHTS Himalayan MSS; NGMPP films (non-bulk); IDP Dunhuang Tibetan (studied, not “unknown”).

The real translation gap is the Tengyur (~162k pages) and 600+ masters’ gsung 'bum on BDRC — “not in English,” not “uncatalogued in a wall.” 84000, Tsadra, Lotsawa House, and the 2025–27 BDRC/Khyentse AI corpus already occupy OCR/translation.

## Sources

| URL | What it is | Lang | Rel. |
|---|---|---|---|
| https://www.bdrc.io/access-policies/ | BDRC access/license | en | high |
| https://library.bdrc.io/ | BUDA; 35M-page banner | en | high |
| https://www.youtube.com/watch?v=4JKdUKC7K7I | Ronis 2024: 25M Tibetan, OCR backlog | en | high |
| https://www.bdrc.io/blog/2026/02/28/bdrc-launches-major-initiative-to-build-open-buddhist-datasets-for-ai/ | 26M OCR’d; PD HF dump planned | en | high |
| https://github.com/buda-base/buda-iiif-server/blob/master/API.md | IIIF Image + PDF API | en | high |
| https://ldspdi.bdrc.io/resource/G880.ttl | RDF: Sakya monastery | bo/en/zh | high |
| https://ldspdi.bdrc.io/resource/MW3CN8601.ttl | 2018 Gorum catalogue, 5 vols | bo/en | high |
| https://asianlegacylibrary.org/library/downloads/ | ACIP PD etexts | en | high |
| https://github.com/Esukhia/derge-kangyur | PD Derge Kangyur | bo/en | high |
| https://idp.bl.uk/about/projects/tibetan-manuscripts/ | IDP Tibetan digitisation | en | high |
| https://www.aai.uni-hamburg.de/en/forschung/ngmcp/history/history.html | NGMPP 180k MSS / ~1/5 Tibetan | en | high |
| https://84000.co/progress-and-impact | Kangyur 50% / Tengyur 0.7% | en | high |
| http://xz.people.com.cn/n2/2022/0301/c138901-35154373.html | Sakya 20% scanned, 2022 | zh | high |
| http://news.xinhuanet.com/english/2017-10/12/c_136674892.htm | 2017 Sakya scan + “share” quote | en | high |
| http://cul.china.com.cn/2026-03/11/content_43370134.htm | 2026 CPPCC digitization petition | zh | high |
| http://www.xinhuanet.com/2021-04/23/c_1127367997.htm | TAR 23,116 leaves online | zh | high |
| https://www.nlc.cn/pcab/zy/szzy/index.shtml | 中华古籍资源库 | zh | high |
| http://xzmuseum.cn/2021/07/20/909797e29abc446ba24f187e6e830dc0.html | CTRC DB internal-only 2021 | zh | high |

## Gaps and what would settle them

- **Live BDRC image total.** `AO_volumePagesGrandTotal` 500’d. Ask help@bdrc.io for released-image count and the open/restricted split.
- **Works physically from Sakya.** SPARQL `?w bdo:workIsAbout bdr:G880` plus publisher filters; not completed here (Fuseki).
- **CTRC / TAR / NLC later openings.** 2021 CTRC was intranet; 2026 petition implies still closed. Search 萨迦寺 / 果如 on TAR and 中华古籍资源库 with a Chinese ID.
- **True monk-scan leaf count.** 2022 (~10k vols + 20%), 2025 English (3k vols / 7k pages), and 2025 Chinese (100k pages) cannot all be true. Read the 2018 Gorum catalogue; ask 管委会 for `已扫描叶数`.
- **CNKI** not queried. **2026–27 BDRC PD OCR dump** promised, not shipped. **NGMPP Tibetan as files:** catalogue yes, bulk digital no.

## Implication for the open-source project

- **AGAINST any design that depends on “sourcing Sakya Monastery manuscripts.”** The wall is a monk-run, underfunded PRC heritage project with no public API. An outside repo cannot ingest it today. Pretending otherwise repeats the viral tweet.
- **AGAINST treating “untranslated” as “undigitized.”** Kangyur/Tengyur etexts are already PD. English Kangyur is half-done. Remaining work is translation labor and extra-canonical gsung 'bum, not a missing scanner at Sakya.
- **AGAINST building a new scan archive.** BDRC + IA + ALL + CIHTS + LTWA + NLM already are that archive, with IIIF and a 2025–27 PD OCR grant. Duplicating BUDA wastes motion.
- **FOR (narrow) work on top of BDRC/Esukhia/ACIP:** OCR cleanup, recension alignment, translation of extra-canonical works 84000 will not touch for decades. Do not re-license modern PRC/Indian reprints as CC-0.
- **If you proceed:** ingest only ACIP/Esukhia PD etexts and BDRC public-domain items via documented IIIF/PDF APIs and IA. Do not scrape login-gated IIIF. Do not claim Sakya provenance for Derge/PL480 reprints. Partner with BDRC/OpenPecha/84000; do not compete.
- **Honest product question:** the unmet need is translating *already digitized* extra-canonical Tibetan, plus better umé OCR — a crowded field BDRC just funded. Sakya-wall uniqueness is not available to you.
