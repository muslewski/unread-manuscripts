# sakyalibrary.com and Sakya-lineage digital publishing

## Verdict

- **[FACT] sakyalibrary.com is not the Tibet Sakya Monastery wall library.** It is “A Sakya Digital Library”: Kathmandu Unicode Tibetan etexts (Word + searchable PDF) from IBA, Sachen International (Guru Lama), and Chödung Karmo, funded by the Khenpo Appey Foundation. Live 27 Aug 2026. ([About](http://sakyalibrary.com/home/page/f344da50-c2c1-452b-a8f7-95ae75e6e7fc), [Introduction](http://sakyalibrary.com/home/page/966a3738-446b-4787-898b-59e434b725e9))
- **[FACT] ~784 titles, Tibetan only, not scans.** Three collection pages: **784** `/Library/Book/{guid}` records, **1,568** `/Assets/files/` links (docx+pdf). Hugging Face dump: **783** Unicode texts. No manuscript images. ([Collections](http://www.sakyalibrary.com/Library/Collections); [HF](https://huggingface.co/datasets/old-acc-of-h/sakya-library-texts))
- **[FACT] License is CC-NC-SA plus extra no-edit terms; some titles are empowerment-gated.** Introduction uses CC BY-NC-SA **3.0**; footer uses **4.0**. Extra conditions forbid additions/deletions except spelling. A JS flag `IsTearmCondition` opens an empowerment modal and POSTs PII to `/Library/AddCustomerInfo`.
- **[FACT] Bulk acquisition is technically easy, legally constrained, and already done.** No `robots.txt` or sitemap (404). Undocumented JSON at `/Library/GetDatatableSearchTitle` returns direct `PdfUrl`/`DocUrl`. Internet Archive already holds **1,622** items under creator “Sakya Library” (uploaded Aug 2024).
- **[FACT] Adjacent Sakya orgs publish lineage literature from diaspora seats, not the TAR wall.** IBA/CKTG, Khenpo Appey Foundation / Wisdom “Sakya Classics,” Sachen Foundation (US), The Sakya Tradition Inc., Seattle `sakya.org`, Tsechen Kunchab Ling, Lotsawa House, BDRC, and the Austrian Sakya Research Centre. **sakyaresourceguild.org does not resolve.**
- **The 84,000 number and this website are different objects.** Wikipedia/China News Service describe cataloguing and **>20% scan-digitization by 2022 of the Tibet monastery stacks**; that archive is not this site. Press that stitches the two together (e.g. [thearchaeologist.org](https://www.thearchaeologist.org/blog/ancient-library-in-tibet-creates-digital-archive-of-84000-scriptures)) is contaminated, not evidence that sakyalibrary.com is the 84k corpus.
- **Implication:** this slice argues **against** treating sakyalibrary.com as a source of genuinely unknown Tibet manuscripts. It is a frozen, already-mirrored etext dump of known scholastic works.

## Findings

### 1. Who runs it, what is hosted, is it alive?

**Operator.** [FACT] IBA, Tinchuli/Boudhanath, Kathmandu, founded 2001 by Khenchen Appey Rinpoche (1927–2010), directed by Khenpo Ngawang Jorden, PhD; **Sachen International** (Guru Lama); **Chödung Karmo** (2010, IBA). Funded by the **Khenchen Appey Foundation**. Contact `sakyalibrary[at]gmail[dot]com`. ([About](http://sakyalibrary.com/home/page/f344da50-c2c1-452b-a8f7-95ae75e6e7fc); [IBA](https://internationalbuddhistacademy.org/about-us/); [KAF](https://www.khenpoappey.org/en/introduction); SRC [S1331](https://sakyaresearch.org/sources/1331) dates the site “2016–”.)

**Domain / hosting.** [FACT] Registered **2015-12-23**, expires **2026-12-23**, last changed **2025-10-24** (RDAP). IIS 8.5 / ASP.NET MVC 5.2 at `139.180.147.34` (Vultr, Singapore). **HTTPS :443 times out.** 2019 WHOIS: registrant **Microtec Pte Ltd** (Singapore); CKTG’s Lojong Android app is `com.microtecweb.mindtrainning`. [CLAIM] Microtec built the site — not confirmed beyond WHOIS + that package name.

**What is hosted.** [FACT] Print → two DVDs — “Rare and Precious Buddhist Scriptures” (IBA + Sachen International, **2012**) and “Eighteen Renowned Scriptures” (Sachen International, **2011**) — then free online. Each title: Unicode Word (Monlam Uni Ouchan2, `.docx` / Word 97–2003) + searchable PDF. Homepage: “The texts on this website are in Tibetan only.” No scans. ([Introduction](http://sakyalibrary.com/home/page/966a3738-446b-4787-898b-59e434b725e9))

**URL patterns (all HTTP).** `/` → `/Home/Index`; `/home/page/{guid}` (intro/about); `/Library/Collections`; `/Library/Collection/{guid}?topicId={guid}`; `/Library/Book/{guid}` (iframe PDF + Word); `/Assets/files/{CODE}.pdf|.docx` (`001UMA.pdf`, `AJAM001_….docx`); `/Library/Search?skey=`; JSON `/Library/GetDatatableSearchTitle|Author|Content`; `/Library/Feed`; POST `/Library/AddCustomerInfo`; `/Home/Language/{guid}`; Wayback also has `/Account/Signin`.

**Counts.** [FACT] Collection roots: Eighteen Great Treatises commentaries `dcd9b329-…` **172**; Collected works `76334317-…` **462**; Various `b5dc9bfe-…` **150**. **Union 784 books / 1,568 assets.** Index is only a preview (211 book links + 27 “more…”). Contents: Madhyamaka, Vinaya, Prajñāpāramitā, Abhidharma, Pramāṇa, Trisaṃvara; gsung ’bum of Lama Dampa, Amezhab, Gorampa, Rongtön, Tsarchen, Rendawa, Dezhung Tulku; biographies, tantra, Shangpa Kagyü, lojong. [SPECULATION] Kathmandu input of **known** treatises, not TAR palm-leaf uniques. BDRC already holds Sachen International print (15-vol. *sa skya bka’ ’bum*, Kathmandu 2006, [MW00EGS1017151](https://library.bdrc.io/show/bdr:PR0ET004)).

**Search / robots.** [FACT] Advanced search: Title/Author/Content. JSON `GET /Library/GetDatatableSearchTitle?skey=…` returns `{iTotalRecords, aaData:[{Id,Name,Author,IsTearmCondition,DocUrl,PdfUrl,…}]}`. Empty `skey` → 0. No catalog dump of all 784 without crawling HTML or paging search. `robots.txt` and `sitemap.xml` are **404** (“The controller for path '/robots.txt' was not found”). No documented API.

**Living or abandoned.** [FACT] HTTP 200 in Aug 2026; IBA, CKTG (still lists it as **2016**), KAF, Sachen Foundation, SRC still link. Corpus frozen: RSS `lastBuildDate` **2015-09-18**; `001UMA.pdf` Last-Modified **2015-05-30**; `001UMA.docx` **2011-03-13**; Wayback `/home/index` from **2016-06-21**. Domain renewed 2025. **Frozen corpus, still hosted.**

### 2. Terms / copyright / machine processing

Introduction, quoted:

> These works are licensed under a Creative Commons Attribution-NonCommercial-ShareAlike 3.0 Unported License.  
> These texts were inputted and edited with a lot of hard work for you to use free of charge, for educational and scholarly purposes, fulfilling the wishes of the late Khenchen Appey Rinpoche (Ngawang Yönten Zangpo).  
> You may publish these texts under two conditions:  
> 1. Apart from spelling corrections, no other additions or deletions are to be made to the text.  
> 2. You must acknowledge our work in the publication using the following text:  
> These texts were published in digital format in 2015 by the InternationalBuddhist Academy in conjunction with Sachen International of Lama Guru.

Footer on every page: “This work is licensed under a Creative Commons Attribution-NonCommercial-ShareAlike **4.0** International.” [FACT] 3.0 vs 4.0 is unresolved on the site itself. [FACT] Extra “no additions or deletions” is **stricter than CC** (CC-SA permits adapted works if shared alike). Translation is an adaptation; they did not grant a translation exception.

**Restricted subset.** [FACT] If JSON `IsTearmCondition` is true, downloads open a modal: “Access to this text is restricted to individuals who have received the appropriate levels of empowerment, transmission and instruction from a qualified Lama.” Name/Email/Empowerment/Lama → POST `/Library/AddCustomerInfo`. HF still has 783 rows after excluding “practitioners guided by a Lama,” so the gated set is small.

**Already copied.** [FACT] HF `old-acc-of-h/sakya-library-texts` (2024, 783 rows, ~283 MB; YAML `cc-by-sa-4.0` vs body CC BY-NC-SA 4.0; README confuses the site with “Sakya Monastery”). IA collection `sakya-library`, **1,622** items, uploader `alanjas@hotmail.com`, 16 Aug 2024, same 2015 IBA/Sachen credit.

### 3. Technical feasibility of bulk acquisition

[FACT] **Technically easy, not licensed for vacuuming.** Three collection pages already list every GUID and asset. Files send `Accept-Ranges: bytes`. No robots policy; no rate-limit headers on the few HEADs used here. Asset names are sequential (`001UMA`, plus `KHEZ`/`NAMT`/`AJAM`…). JSON search returns `PdfUrl`/`DocUrl`. NC + extra no-edit + empowerment gate ≠ permission to scrape and relicense. HTTPS absent; verbose ASP.NET errors leak stack traces.

### 4. Adjacent Sakya-world digital efforts

| Org | Publishes | Scale |
|---|---|---|
| **IBA + Chödung Karmo** | English/Spanish Appey, Rongtön, Gorampa, Migmar Tsering; **2025** titles; site is their Tibetan dump ([publications](https://chodungkarmo.org/publications/)) | Dozens of books |
| **Khenpo Appey Foundation** | Funds the site; Wisdom “Sakya Classics”; pipeline includes Pang Lodrö Tenpa Abhidharma “recently rediscovered in Tibet and brought to Nepal” via Appey ([projects](https://www.khenpoappey.org/en/translation-projects)) | Scholarly series |
| **Sachen Foundation** (US, 42nd Sakya Trizin, 2017) | Mahāyāna prayer PDFs; 50-text Tibetan–English prayer book (2020); [directory](https://www.sachenfoundation.org/archives/sakya-resource-directory/) **links out** to this site, BDRC, 84000. Vajrayana later “to authorized centers” | Practitioner PDFs |
| **Sakya Trichen / Khön** | [hhsakyatrizin.net](https://hhsakyatrizin.net/) (old hhthesakyatrizin.org 301s here): bio, schedule, Wisdom volumes (*Freeing the Heart and Mind*, Stearns Lamdré). Not a manuscript library | Teachings + books |
| **The Sakya Tradition, Inc.** (Cambridge MA, 2018/2020) | [E-library](https://sakyatradition.org/sakya-e-library/) of living-master teachings; [CC BY-NC-ND 4.0](https://sakyatradition.org/creative-common-license/) | Contemporary, multilingual |
| **Seattle Sakya Monastery** | Phuntsok Phodrang / Dagchen (1929–2016); ~2,500-vol physical library; [downloads](https://www.sakya.org/downloads/) = few English PDFs ([FAQ](https://www.sakya.org/resources/faq/)) | Community archive |
| **Tsechen Kunchab Ling** (NY) | Physical library “hundreds” of books; 2014 **84000** sutra reading with HH ([library](https://sakyatemple.org/library-activities/)) | Lending + liturgy |
| **Sakya Research Centre** (ÖAW, 2011–) | [443 Tibetan etexts, 6,693 sources](https://sakyaresearch.org/features); TEI-XML; catalogs this site as S1331 | Research graph |
| **Lotsawa House** | [~15 English Kabum items](https://www.lotsawahouse.org/topics/sakya-kabum/) (Derge/Dehra Dun 15 vols.) | Tiny slice |
| **sakyaresourceguild.org** | **No DNS A record** (27 Aug 2026). Jeff Watt’s old Resource Guide (`mypage.direct.ca/w/wattj/`) 301s away; his live work is Himalayan Art (art, not etext) | Dead / misremembered |

### 5. Same corpus as Tibet Sakya Monastery, or diaspora literature?

**Not the same.** [FACT] sakyalibrary.com’s own origin story is IBA/Sachen **print → DVD (2011–2012) → website (2015–2016)** of inputted Unicode. [FACT] Wikipedia, citing China News Service (28 Feb 2022): the **TAR** monastery began digitizing in 2011; by 2022 all ~84,000 books were **catalogued** and **>20% fully digitized**; “monks now maintain a digital library” — not identified as sakyalibrary.com. ([en.wikipedia.org/wiki/Sakya_Monastery](https://en.wikipedia.org/wiki/Sakya_Monastery); [tibet.cn item](http://m.tibet.cn/cn/religion/202202/t20220228_7154118.html))

[FACT] *The Archaeologist* (22 Nov 2024) copies the 84,000 / 2011 / 20% figures **and** this site’s CC + Appey sentences, then points at “the Sakya Digital Library.” That mash-up is how a Kathmandu etext site gets misread as the TAR wall.

[SPECULATION] Some *works* (Gorampa, Rongtön, Amezhab) surely also sit on TAR shelves — ordinary transmission, not evidence this site is the uncatalogued 84k. HF/IA/BDRC already treat this material as **known Sakya scholastic literature**.

## Sources

| URL | What it is | Lang | Reliability |
|---|---|---|---|
| http://sakyalibrary.com/home/index | Live home | en/bo | high |
| http://sakyalibrary.com/home/page/966a3738-446b-4787-898b-59e434b725e9 | Introduction, terms, DVD origins | en | high |
| http://sakyalibrary.com/home/page/f344da50-c2c1-452b-a8f7-95ae75e6e7fc | About / operators | en | high |
| http://www.sakyalibrary.com/Library/Collections | Full collection HTML | bo/en | high |
| http://sakyalibrary.com/Library/Feed | RSS; lastBuild 2015-09-18 | xml | high |
| http://sakyalibrary.com/Library/GetDatatableSearchTitle | Undocumented JSON search | json | high |
| https://internationalbuddhistacademy.org/about-us/ | IBA operator | en | high |
| https://chodungkarmo.org/publications/ | CKTG 2025 books + 2016 site | en | high |
| https://www.khenpoappey.org/en/introduction | Funder | en | high |
| https://www.khenpoappey.org/en/translation-projects | KAF/Wisdom pipeline | en | high |
| https://sakyaresearch.org/sources/1331 | SRC record, dated 2016 | en | high |
| https://sakyaresearch.org/features | Etext/source counts | en | high |
| https://huggingface.co/datasets/old-acc-of-h/sakya-library-texts | Unofficial 783-row scrape (2024) | en/bo | med |
| https://archive.org/details/SakyaLibrary_002UMA | IA; collection `sakya-library`; 1622 hits | en | high |
| https://library.bdrc.io/show/bdr:PR0ET004 | BDRC: Sachen International | en | high |
| https://www.sachenfoundation.org/archives/ | US prayer/practice archive | en | high |
| https://www.sachenfoundation.org/archives/sakya-resource-directory/ | Directory linking the site | en | high |
| https://www.sakya.org/downloads/ | Seattle downloads | en | high |
| https://www.sakya.org/resources/faq/ | Seattle / Dagchen / ~2,500 vols | en | high |
| https://sakyatemple.org/library-activities/ | TKL library / 84000 event | en | high |
| https://sakyatradition.org/our-mission/ | TST Inc. 2018/2020 | en | high |
| https://sakyatradition.org/creative-common-license/ | TST CC BY-NC-ND 4.0 | en | high |
| https://hhsakyatrizin.net/ | 41st Sakya Trichen site | en | high |
| https://www.lotsawahouse.org/topics/sakya-kabum/ | Public Kabum translations | en | high |
| https://en.wikipedia.org/wiki/Sakya_Monastery | TAR 84k / 2011 / 2022 20% | en | med |
| http://m.tibet.cn/cn/religion/202202/t20220228_7154118.html | CNS 2022 digitization | zh | med-high |
| https://creativecommons.org/licenses/by-nc-sa/3.0/ | License named on intro | en | high |
| https://www.thearchaeologist.org/blog/ancient-library-in-tibet-creates-digital-archive-of-84000-scriptures | 2024 mash-up of 84k + this site | en | **low** |
| RDAP `sakyalibrary.com` | Created 2015-12-23, expires 2026-12-23 | en | high |

## Gaps and what would settle them

- **Gated-title count.** HF 783 vs site 784 ⇒ almost all public. **Settle:** IBA catalog dump.
- **Any TAR page-images?** Sampled PDFs are typeset Unicode. **Settle:** IBA on source (xylograph vs input).
- **TAR monks’ digital library URL.** CNS 2022 gives none. **Settle:** Chinese institute pages / TASS 2003, not this domain.
- **sakyaresourceguild.org.** Dead DNS. **Settle:** human bookmark; likely Watt’s Guide or Sachen’s directory, misremembered.
- **CC 3.0 vs 4.0 vs extra no-edit.** **Settle:** email `sakyalibrary@gmail.com` / KAF, including translation rights.

## Implication for the open-source project

- **AGAINST “source the hidden 84,000 via sakyalibrary.com.”** Wrong corpus, wrong scale (~784 vs ~84k), wrong medium (Unicode input vs wall scans), already mirrored.
- **AGAINST treating “95% untranslated” as a property of this site.** These are canonical scholastic texts; many already have English (CKTG, Wisdom/KAF, Lotsawa House, 84000, Stearns Lamdré). Remaining work is **selected classics under lineage orgs**, which KAF already lists.
- **AGAINST bulk-rescrape-and-relicense.** NC + SA + extra no-edit + empowerment modal. HF/IA already copied it. Training or “open” translations from this dump would fight the actual rights-holders.
- **NEUTRAL only for a cooperative viewer** if IBA/KAF asked (search, BDRC/SRC alignment). That is a website upgrade, not unknown-manuscript discovery.
- **Design:** TAR wall ≠ this domain. For Sakya-lineage etext in modern languages, talk to CKTG/KAF/Sachen Foundation/The Sakya Tradition — already doing it, on known books.
