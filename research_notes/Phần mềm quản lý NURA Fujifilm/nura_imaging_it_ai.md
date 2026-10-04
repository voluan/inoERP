# NURA (Fujifilm) — Imaging Informatics & AI Software Stack

Research date: 2026-10-04. Convention: everything under "Cited Findings" is **confirmed** by the linked source (with the source's date where known); everything under "Inferences" is **inferred** by the researcher and not stated by any source. Older items are dated. Note on naming: "DKH" in FUJIFILM DKH = **Dr. Kutty's Healthcare** (India/Middle East hospital group), not "Dr. Kodama".

Headline: Fujifilm has never publicly named the PACS/RIS/viewer products running inside NURA. Public sources confirm only (a) Fujifilm CT + mammography + "medical IT system based on AI technology", (b) the **REiLI** AI brand and **FCT PixelShine** deep-learning low-dose CT reconstruction, (c) a central **remote-reading hub** in Kozhikode (Calicut), Kerala for Indian sites, (d) a **blockchain "Digital Trust Platform"** for sharing anonymised data with Japan, and (e) a patient smartphone app / AI avatar for results. Exact SYNAPSE module names and versions at NURA are not disclosed anywhere I could find.

---

## Q1. Which Fujifilm PACS/RIS products are used (SYNAPSE PACS, RIS, 3D, Cardiovascular, VNA, Mobility)? On-premise or cloud?

### Takeaway
No public source names the PACS/RIS/viewer at NURA; Fujifilm consistently says only "medical IT system based on AI technology". Since SYNAPSE is Fujifilm's PACS platform, NURA almost certainly runs Fujifilm SYNAPSE-family software, but the exact modules, versions, and whether it's on-prem or cloud are unconfirmed.

### Cited Findings
- All Fujifilm press releases describe NURA's IT only as "medical IT system based on AI technology designed to support doctors conduct screening and tests for cancer and lifestyle diseases" (no product name). Examples: ASEAN expansion release (2025) — [Fujifilm HQ news 13076](https://www.fujifilm.com/bo/en/news/hq/13076); South Africa/Dubai release (30 Sep 2025) — [Fujifilm HQ news 12811](https://www.fujifilm.com/ae/en/news/hq/12811); Hyderabad release (17–19 Nov 2023), which adds that the system provides "image interpretation assistance to doctors" — [Fujifilm India news 10875](https://www.fujifilm.com/in/en/news/hq/10875).
- 2021 launch coverage (Japanese): NURA uses "AI技術を活用したITシステム" (an IT system using AI technology), with no system name given — [e-RadFan / Medical Watch, Feb 2021](https://www.e-radfan.com/product/77513/).
- The NURA Global Innovation Center release (Dec 2024) also gives no IT product names (no SYNAPSE, no cloud platform named) — [Fujifilm JP news 11974](https://www.fujifilm.com/jp/ja/news/list/11974).
- Fujifilm's DX case page for NURA covers the data-sharing platform, not PACS/cloud specifics; it explicitly lacks PACS/SYNAPSE/cloud details — [Fujifilm Holdings DX case-3](https://holdings.fujifilm.com/en/about/dx/activity/product/case-3).
- The Dec 2024 BusinessWire/Yahoo release on the Innovation Center includes a boilerplate line that Fujifilm's AI initiative will "enhance its imaging and informatics healthcare Synapse® portfolio which includes Synapse PACS, Synapse Cardiovascular, and Synapse VNA" — this is corporate boilerplate, not a statement that NURA uses these modules — [Yahoo Finance (BusinessWire), 24 Dec 2024](https://finance.yahoo.com/news/fujifilm-expands-health-screening-services-124800030.html).
- Context — Fujifilm India's HCIT portfolio (undated CAHO deck, around 2021–22, Rajeev K. Jha, National Service Manager HCIT, Fujifilm India): Synapse PACS ("FDA approved PACS"), Synapse Mobility ("FDA approved Mobility Zero Footprint viewer"), Synapse 3D Advanced Visualization, Synapse VNA; "CE certification"; "KLAS RATINGS – 4th Globally (KLAS 2020) and 1st in India"; AI integrated via "Web Service API or HL7" with "All AI integrated directly into Synapse" — [CAHO PDF, Fujifilm India](https://www.caho.in/files/Rajeev_K_Jha_AI_Overview_Fujifilm_India.pdf).
- Context — Fujifilm India launched **"HCIT Fenix"** at IRIA 2026 (2 Feb 2026): a healthcare IT ecosystem "integrating enterprise imaging, PACS, RIS, mobility, and workflow tools", developed under Make in India; also **SYNAPSE 3D** integration on the new FCT iStream CT — [Digital Health News, 2 Feb 2026](https://www.digitalhealthnews.com/fujifilm-india-unveils-advanced-imaging-and-healthcare-it-solutions-at-iria-2026-). No NURA mention in the article.
- Context — Fujifilm IR (Medical Systems Business Briefing, 12 Oct 2023): SYNAPSE PACS launched 1999 and claims "the largest" PACS market share; SYNAPSE VINCENT (3D, 2008); SYNAPSE SAI viewer (AI interpretation platform, 2019); SYNAPSE Creative Space (AI development platform, 2021); NURA is listed alongside these as a "packaged service" — [Fujifilm IR presentation PDF, 12 Oct 2023](https://ir.fujifilm.com/en/investors/ir-materials/presentations/session/main/0118/teaserItems1/0/tableContents/0114/multiFileUpload2_1/link/ff_presentation_20231012_001e.pdf).
- The same IR deck mentions a Fujifilm "cloud service for medical facilities" and remote service "ACTIVE LINE", plus a Japan-market cloud service that shares gastroscopy screening data between screening sites and second-reading institutes. None of these is linked to NURA in the deck — [Fujifilm IR PDF, Oct 2023](https://ir.fujifilm.com/en/investors/ir-materials/presentations/session/main/0118/teaserItems1/0/tableContents/0114/multiFileUpload2_1/link/ff_presentation_20231012_001e.pdf).

### Inferences
- NURA very likely runs a Fujifilm SYNAPSE-family PACS/viewer, because Fujifilm supplies "approximately 80–90 per cent of the imaging and technology platforms" ([BioSpectrum India, Jan 2026](https://www.biospectrumindia.com/views/17/27243/india-has-strong-medical-talent-increasing-health-awareness-and-a-real-need-for-structured-preventive-care-.html)), REiLI apps are delivered through SYNAPSE (SAI viewer / VINCENT / SYNAPSE 3D), and Fujifilm India sells Synapse PACS / Mobility / 3D / VNA. Exact modules and versions are **unknown**.
- Remote reading from Kozhikode across all Indian centers and the mobile NURA Express (Q3) means images must be centralised or shared over a WAN. That points to a central/hosted PACS (on-prem at the hub, or private cloud) rather than isolated per-site systems. Not confirmed.
- Outside India, partner-operated sites (Vietnam/VJH, Mongolia/Tavan Bogd, PURA Abu Dhabi/PureHealth, South Africa/InUversal) are described as using "Fujifilm's medical devices and medical IT systems" developed for NURA ([PURA release, Jan 2025](https://www.fujifilm.com/jp/en/news/hq/11888)). That suggests a replicable packaged IT stack, though it may be installed per country.
- A screening RIS/worklist must exist to sequence the 120-minute multi-station flow and produce a 40–50-page same-day report (Q3). It may be part of the front-office system covered by the other researcher. No source names it.
- The HCIT Fenix suite (Make in India, Feb 2026) could become NURA India's future RIS/PACS layer. This is speculative.

### Gaps
- No source names SYNAPSE PACS, SYNAPSE RIS, SYNAPSE 3D, SYNAPSE Cardiovascular, SYNAPSE VNA or Synapse Mobility at NURA. Versions, server topology, hosting (on-prem vs. AWS/Azure/Fujifilm cloud), and DICOM/HL7 integration details are undisclosed.
- Fujifilm's DX/IR materials and trade press (AuntMinnie, Express Healthcare, Medical Buyer) had no NURA IT-architecture case study that I could find.

---

## Q2. Which REiLI AI technologies are used, for which exams, and what is their regulatory status?

### Takeaway
Confirmed for NURA: **REiLI** (deep-learning abnormality detection that flags regions for physician review), **FCT PixelShine** (deep-learning denoising for ultra-low-dose CT, about 0.1–0.2 mSv), and CT-based **automatic lung-nodule detection**. CT is also used for COPD (emphysema) and heart-attack risk assessment, and Fujifilm is developing AI scoring for lung and heart. Specific REiLI app names and versions at NURA are not disclosed. Fujifilm's Japan-approved REiLI products (SAI viewer lung-nodule CAD, CXR-AID, rib-fracture CAD, VINCENT Agatston/Goddard scores) are documented, but I found no CDSCO (India) registrations.

### Cited Findings
**What NURA says it uses (confirmed)**
- NURA India technology page: "REiLI: uses deep learning and Fujifilm's extensive image processing database to detect abnormalities automatically"; "FCT PixelShine: Deep Learning based image processing software that improves the image quality of low-dose radiation scans"; "1/50x radiation than regular imaging machines"; "all findings are reviewed by NURA's qualified physicians before results are shared" — [nura.in/technology](https://nura.in/technology/) (accessed Oct 2026).
- NURA Thailand FAQ: REiLI is "trained on Fujifilm's extensive imaging database"; ultra-low-dose CT with **FCT PixelShine**; dose **0.1–0.2 mSv**, "approximately 97% less than standard diagnostic CT"; "Every AI-assisted finding is reviewed by NURA's qualified physicians" — [nurathailand.com/faq](https://nurathailand.com/faq/).
- Launch announcement (Nikkei xTech, 25 Jan 2021): AI and imaging used include **CT with automatic lung-nodule detection**, image-enhanced endoscopy, high-resolution mammography, and ultrasound. Covers **10 cancer types** (incl. lung, gastric, colorectal, prostate) plus **COPD and myocardial-infarction risk assessment via CT** — [Nikkei xTech, Jan 2021](https://xtech.nikkei.com/atcl/nxt/news/18/09511/).
- Fujifilm IR (Oct 2023): NURA is "Significantly reducing CT radiation dose with the use of AI" — [Fujifilm IR PDF](https://ir.fujifilm.com/en/investors/ir-materials/presentations/session/main/0118/teaserItems1/0/tableContents/0114/multiFileUpload2_1/link/ff_presentation_20231012_001e.pdf).
- Japanese-press summary: AI is used so CT can be low-dose yet high-quality, and AI for **lung and heart scoring** is being developed to explain risk to examinees; a CT technology that auto-detects lung-nodule candidates is used — [search-result summary of Fujifilm/Japanese coverage; see JST Science Portal interview, 18 Mar 2025](http://scienceportal.jst.go.jp/stories/20250318_e01/) (the interview itself confirms only the 120-min flow and 100-site target; the scoring detail came from related Japanese coverage and is **not independently verified**).
- NURA Innovation Center will develop "診断支援AI技術" (diagnostic-support AI) using anonymised, consented patient data — [Fujifilm JP news 11974, Dec 2024](https://www.fujifilm.com/jp/ja/news/list/11974).
- AI is positioned as assistant only: "AI helps by highlighting areas that may require closer attention … all final clinical decisions … made by trained physicians" (Masaharu Morita, Founder & Program Director, NURA) — [BioSpectrum India, 31 Jan 2026](https://www.biospectrumindia.com/views/17/27243/india-has-strong-medical-talent-increasing-health-awareness-and-a-real-need-for-structured-preventive-care-.html); JETRO (26 Mar 2026): AI is "あくまで医師のアシスタント" (strictly the physician's assistant) — [JETRO area report](https://www.jetro.go.jp/biz/areareports/2026/ac822db52064c952.html).
- Endoscopy at NURA India: "ultra-slim endoscope with **Multi Light** technology" offering White Light Imaging, **LCI** and **BLI** — [nura.in/technology](https://nura.in/technology/).

**REiLI product portfolio and regulatory status (Fujifilm-wide, Japan; NOT confirmed as deployed at NURA)**
- REiLI brand launched 2018. Development areas: AI denoising/image quality (CT/MR from ex-Hitachi Fujifilm Healthcare), organ segmentation, CAD (glioma measurement; pancreatic-cancer and bone-metastasis detection in development), and report-writing support. Semi-automatic finding-text generation for **lung and liver** is already productised — [JRC magazine article by Mako Fukuda, Fujifilm (May 2024)](https://jrcart.jp/wp-content/uploads/2024/05/magazine_33.pdf).
- **SYNAPSE SAI viewer**: launched **July 2019**, used at **600+ facilities in Japan**. Functions: organ recognition (lung/liver/kidney/spleen; left/right kidney and adrenal volumes), lung-segment and liver-segment labelling (works on non-contrast CT), vertebra/rib labelling, aorta view (added Apr 2024), SAI filters (liver/kidney/adrenal/pancreas/spleen). Regulatory: image-processing program FS-AI683 (certification 231ABBZX00029000); display program FS-V686 (231ABBZX00028000) — [JRC magazine, 2024](https://jrcart.jp/wp-content/uploads/2024/05/magazine_33.pdf).
- **Lung-nodule detection program FS-AI688** (for SAI viewer; shows bounding boxes on chest CT): **PMDA approval 30200BZX00150000** — [JRC magazine, 2024](https://jrcart.jp/wp-content/uploads/2024/05/magazine_33.pdf).
- **Rib-fracture detection program FS-AI691**: approval 30300BZX00244000 — [JRC magazine, 2024](https://jrcart.jp/wp-content/uploads/2024/05/magazine_33.pdf).
- **CXR-AID** (chest X-ray CAD, program LU-AI689, approval **30300BZX00188000**): detects nodule/mass, consolidation and pneumothorax with heatmap and score. Supports portable/seated/supine imaging. Its "CAD output check" function is "highly rated mainly at health-screening facilities" — [JRC magazine, 2024](https://jrcart.jp/wp-content/uploads/2024/05/magazine_33.pdf). CXR-AID was approved by Japan's PMDA, with core AI by **Lunit** — [AuntMinnie](https://www.auntminnie.com/imaging-informatics/artificial-intelligence/article/15629052/fujifilms-chest-x-ray-ai-software-gets-nod-in-japan); [PR Newswire](https://www.prnewswire.com/news-releases/fujifilm-introduces-its-ai-powered-product-for-chest-x-ray-in-japan-in-collaboration-with-lunit-301354317.html).
- **SYNAPSE VINCENT** (3D workstation FN-7941, certification 22000BZX00238000): its **Agatston score** (coronary calcium) and **Goddard score** (emphysema/LAA) can be shown inside SAI viewer — [JRC magazine, 2024](https://jrcart.jp/wp-content/uploads/2024/05/magazine_33.pdf).
- **SYNAPSE SAI Report** (viewer-integrated reporting) launched **July 2023**, with finding suggestions from SAI viewer analytics and hyperlinks back to the viewer state — [JRC magazine, 2024](https://jrcart.jp/wp-content/uploads/2024/05/magazine_33.pdf).
- Performance evidence: an external validation of **SYNAPSE SAI viewer V2.4** lung-nodule detection on Japanese LDCT screening (CTDIvol 1.5 mGy) found nodule sensitivity **96.0%**, lung-cancer sensitivity **93.0% (40/43)**, PPV **24.2%**, and **7.0 false positives per scan**. The authors flag "Low PPV and increased FP nodules" as a drawback — [Jpn J Radiol 2025;43(4):634–640, PMC11953200 (online 30 Nov 2024)](https://pmc.ncbi.nlm.nih.gov/articles/PMC11953200/).
- Third-party AI on REiLI/Synapse: Qure.ai's qXR chest X-ray AI is integrated with REiLI (qXR is CE Class II) — [Qure.ai news](https://www.qure.ai/us/news-press-coverages/qure-ai-validated-on-fujifilms-ai-enabled-platform-reili). Fujifilm India's HCIT deck lists marketplace partners: mammo (iCAD, ScreenPoint), CXR (Lunit, Qure.ai), chest/abdomen (Fujifilm, Riverain), neuro (MaxQ, Qure.ai), bone (Gleamer, 16Bit) — [CAHO PDF, Fujifilm India](https://www.caho.in/files/Rajeev_K_Jha_AI_Overview_Fujifilm_India.pdf).
- Fujifilm India's FCT iStream CT (Feb 2026) combines "Synergy-Drive" AI automation (positioning, scan planning, reconstruction) with REiLI — [Digital Health News, Feb 2026](https://www.digitalhealthnews.com/fujifilm-india-unveils-advanced-imaging-and-healthcare-it-solutions-at-iria-2026-).

### Inferences
- "Automatic lung-nodule detection on CT" (2021) plus "lung and heart scoring" (JST-era coverage) likely map to Fujifilm's lung-nodule CAD (FS-AI688 lineage) and VINCENT-type Agatston (coronary calcium) and Goddard/LAA (emphysema) quantification. Fujifilm has not confirmed which builds run at NURA or whether they are Japan-regulated versions or export variants.
- The "organ images and body composition" shown on the consultation touchscreen ([Ukiyo Journal, Nov 2025](https://www.ukiyo-journal.com/en/article/ai-preventive-medicine-fujifilm-nura-innovation)) suggest multi-organ CT segmentation (SAI viewer / VINCENT-style) is used for patient-facing visuals. Inferred.
- "Multi Light / LCI / BLI" is the branding of Fujifilm's ELUXEO (7000-series) / LASEREO endoscopy platforms, so NURA's transnasal endoscopy likely uses an ELUXEO processor with an ultra-slim Fujifilm scope. Use of **CAD EYE** (colon/stomach endoscopy AI) is **not** mentioned by any NURA source.
- "FCT PixelShine" is Fujifilm-branded deep-learning low-dose CT denoising. From outside knowledge, PixelShine is AlgoMedica's technology; this licensing link is **unverified** in my sources.
- Mammography AI at NURA is not stated. Fujifilm IR (Oct 2023) lists "REiLI × Mammography — AMULET SOPHINITY" as a product, so mammography AI may be present on newer units. Inferred.

### Gaps
- No public list of REiLI apps (names/versions) deployed at NURA, and no performance data from NURA's own population.
- **CDSCO (India)**: no registration records found for REiLI apps, SAI viewer, CXR-AID or PixelShine. I also found no Vietnam (DAV/IMDA), Mongolia, Thai FDA, UAE (MOHAP/DoH), or SAHPRA (South Africa) registrations, and no CE-mark records for CXR-AID or the lung-nodule CAD. Regulatory status outside Japan is unknown.
- The years of the Japanese approvals are not stated in the article. From the number prefixes, 302… is approximately Reiwa 2 (2020) and 303… approximately Reiwa 3 (2021), but this reading is an inference.

---

## Q3. How does remote reading work, and are there figures on reading time, turnaround, or AI productivity?

### Takeaway
In India, images from NURA centers and the mobile NURA Express are read remotely by physicians at the **NURA Global Innovation Center, Kozhikode (Calicut), Kerala** (opened Dec 2024). No source says Japanese radiologists read NURA images; Japan's role is anonymised data analysis and AI R&D. The only published turnaround metric is the 120-minute visit with same-day doctor consultation and report. No figures on reading time or AI productivity have been published.

### Cited Findings
- NURA Global Innovation Center (Kozhikode, Kerala; announced 24 Dec 2024) has four functions: (1) screening center; (2) training center for doctors, radiological technologists and nurses; (3) "インド国内の各「NURA」で撮影された医用画像を遠隔で読影する" — a central remote-reading center for images from every NURA in India; (4) diagnostic-support AI development using consented, anonymised data — [Fujifilm JP news 11974](https://www.fujifilm.com/jp/ja/news/list/11974); [Yahoo Finance/BusinessWire, 24 Dec 2024](https://finance.yahoo.com/news/fujifilm-expands-health-screening-services-124800030.html).
- **NURA Express** (mobile CT screening unit, India, launched ~May 2025; Fujifilm's "10th" NURA site): "撮影した画像は、同ケララ州コジコードにある『NURA Global Innovation Center』に常駐する医師が遠隔で読影します" (images are read remotely by physicians stationed at the Innovation Center). Images and results go to examinees via a dedicated smartphone app — [Fujifilm JP news 12176](https://www.fujifilm.com/jp/ja/news/list/12176); [InnerVision, 1 May 2025](https://www.innervision.co.jp/sp/products/release/20250501).
- 120-minute model: "Completing all tests and briefing in 120 minutes" — [Fujifilm IR PDF, Oct 2023](https://ir.fujifilm.com/en/investors/ir-materials/presentations/session/main/0118/teaserItems1/0/tableContents/0114/multiFileUpload2_1/link/ff_presentation_20231012_001e.pdf). Doctors review results with examinees "while viewing the actual diagnostic images" — [PURA release, Jan 2025](https://www.fujifilm.com/jp/en/news/hq/11888).
- Patient-facing flow (Bengaluru): registration and questionnaire → measurements → blood tests, CT, mammography, cervical exam → doctor explains organ images and body composition on a large touchscreen → **40–50-page report booklet plus online PDF the same day** — [Ukiyo Journal, 30 Nov 2025](https://www.ukiyo-journal.com/en/article/ai-preventive-medicine-fujifilm-nura-innovation).
- AI avatar for result feedback: Fujifilm is researching "AI assistant avatars that support feedback of health screening results" with **Microsoft Japan** (Nov 2023) — [Fujifilm India news 10875](https://www.fujifilm.com/in/en/news/hq/10875). JETRO (Mar 2026) reports AI-avatar result feedback as a feature — [JETRO](https://www.jetro.go.jp/biz/areareports/2026/ac822db52064c952.html).
- Thailand FAQ describes physician review of AI findings within the same visit; it does not describe remote reading — [nurathailand.com/faq](https://nurathailand.com/faq/).
- Anonymised screening data is "securely shared with a research and analysis team in Japan" via the Digital Trust Platform. This is analysis, not primary reading — [Fujifilm DX case-3](https://holdings.fujifilm.com/en/about/dx/activity/product/case-3).

### Inferences
- In India, NURA uses a **hub-and-spoke teleradiology model**: Kerala-based physicians read for the metro centers (Bengaluru, Gurugram, Mumbai, Hyderabad, Chennai) and NURA Express. Delivering same-day results within 120 minutes then requires near-real-time image transfer plus AI pre-reads (REiLI flags) to prioritise. Inferred from the stated functions and the 120-minute promise.
- Before Dec 2024, reading was presumably done on-site at each center (no hub existed). Inferred.
- Outside India, partner-run sites (Vietnam, Mongolia, UAE/PURA, South Africa) likely read locally under national licensing rules, since no cross-border reading is mentioned. Not confirmed.
- I found no evidence that radiologists in Japan do primary reads.

### Gaps
- No figures on radiologist headcount, reads per day, time per study, report turnaround beyond the 120-minute visit, AI-assisted time savings, or AI false-positive burden at NURA.
- The teleradiology software/platform, network (VPN/MPLS/cloud), and whether the Kerala hub also serves non-Indian sites are all undisclosed.

---

## Q4. Which imaging/diagnostic equipment is deployed, and how does it integrate with the IT systems?

### Takeaway
Confirmed modalities: Fujifilm **CT** (ultra-low-dose with FCT PixelShine; wide bore), **mammography** (flexible compression paddle), ultra-slim **transnasal endoscopy** with Multi Light (LCI/BLI), and **ultrasound** (2021 plan); a **mobile CT** unit (NURA Express); and lab tests (blood, urine, FIT stool kit). Exact CT, mammography and ultrasound model names are not published. The Mongolia flagship has 4 CTs and 3 mammography units.

### Cited Findings
- All releases: NURA uses Fujifilm "CT scan and mammography system" — [Fujifilm HQ news 13076](https://www.fujifilm.com/bo/en/news/hq/13076); [Fujifilm India news 10875](https://www.fujifilm.com/in/en/news/hq/10875).
- 2021 plan: CT (with lung-nodule detection AI), image-enhanced endoscopy, high-definition mammography, ultrasound — [Nikkei xTech, Jan 2021](https://xtech.nikkei.com/atcl/nxt/news/18/09511/). 2021 Japanese coverage also lists X-ray diagnostic systems including mammography, endoscopy systems, and in-vitro diagnostic (IVD) analysers — [e-RadFan, Feb 2021](https://www.e-radfan.com/product/77513/).
- NURA India technology page: Fujifilm ultra-low-dose CT; digital mammography with flexible compression paddle; nasal endoscopy with an ultra-slim scope and Multi Light (WLI/LCI/BLI). No model numbers given — [nura.in/technology](https://nura.in/technology/).
- Patient blog (24 Mar 2026): CT "with wider bore design"; mammography with flexible paddle; ultra-slim nasal endoscope; FIT kit sent home beforehand; "50 times lower" radiation via PixelShine — [Medstown](https://www.medstown.com/is-ai-the-future-of-healthcare-my-experience-with-nura-body-screening-in-india/).
- Mongolia, 2nd Ulaanbaatar center (opened 1 Aug 2024; Tavan Bogd Group with FUJIFILM DKH support): the largest NURA, with **4 CT scanners, 3 mammography systems**, capacity up to **150 people/day** — [BioSpectrum Asia, 24 Jul 2024](https://www.biospectrumasia.com/news/50/24615/japan-based-fujifilm-expands-health-screening-service-business-in-mongolia.html).
- Bangkok clinic (FUJIFILM DKH (Thailand) Co., Ltd., Chong Nonsi; reported launch 30 Jul 2026): ultra-low-radiation CT, mammography, on-site blood/urine testing — [The Story Thailand](https://www.thestorythailand.com/en/fujifilm-dkh-nura-health/).
- Vietnam (Hanoi): brain dock (MRI) and endoscopy under consideration (Mar 2026) — [JETRO](https://www.jetro.go.jp/biz/areareports/2026/ac822db52064c952.html).
- NURA Express: mobile CT; images sent for remote reading in Kozhikode — [Fujifilm JP news 12176](https://www.fujifilm.com/jp/ja/news/list/12176).
- Fujifilm's current India modality line (IRIA, Feb 2026): **FCT iStream** CT (REiLI + Synergy-Drive + SYNAPSE 3D integration), **AMULET SOPHINITY** FFDM (tomosynthesis, contrast), **FDR Smart X Essential** DR — [Digital Health News, Feb 2026](https://www.digitalhealthnews.com/fujifilm-india-unveils-advanced-imaging-and-healthcare-it-solutions-at-iria-2026-). Fujifilm India also markets **FCT Speedia HD** (model name "Supria") CT — [Fujifilm India FCT Speedia HD page](https://www.fujifilm.com/in/en/healthcare/x-ray/fct/fct-speedia-hd). Neither is tied to NURA by a source.

### Inferences
- NURA CT units are probably from Fujifilm's FCT family sold in India (FCT Speedia/Speedia HD = Supria, or newer FCT iStream / SCENARIA View-class), with FCT PixelShine reconstruction. The model is **not confirmed**.
- Mammography is likely an AMULET-series unit (Innovality in 2021–24 installs; SOPHINITY for newer sites). Not confirmed.
- Endoscopy is likely Fujifilm ELUXEO/LASEREO with a transnasal scope (Multi Light branding). Ultrasound is likely Fujifilm ARIETTA / SonoSite, but no NURA source mentions ultrasound beyond the 2021 plan. Current use is uncertain.
- Integration is presumably standard DICOM (modality → PACS/viewer → REiLI/PixelShine processing) plus HL7/API to the booking and reporting layer, consistent with Fujifilm India's "Web Service API or HL7" AI-integration design ([CAHO PDF](https://www.caho.in/files/Rajeev_K_Jha_AI_Overview_Fujifilm_India.pdf)). Not confirmed for NURA.

### Gaps
- No exact CT, mammography, US, DR or endoscope model numbers or software versions for any NURA site.
- I found no list of IVD/lab analysers or LIS integration (possibly in the other researcher's scope).

---

## Q5. What do Fujifilm case studies, IR materials and conferences say about NURA's IT architecture and outcomes (screenings, detection rates, AI performance)?

### Takeaway
Fujifilm publishes volume figures (rising from about 17k in Nov 2023 to more than 150k by Jan 2026) and "critical findings" counts, plus business targets: 100 sites and ¥20B revenue a year by FY2030, at roughly ¥20,000 per screening. It has published no cancer detection rates, PPVs, or NURA-specific AI performance data, and I found no peer-reviewed or RSNA/JRC/ECR/IRIA abstract reporting NURA outcomes. Some figures conflict, so cite them with their dates.

### Cited Findings
**Volumes and outcomes (with dates, conflicts noted)**
- ~**17,000** users across centers — Nov 2023 — [Fujifilm India news 10875](https://www.fujifilm.com/in/en/news/hq/10875).
- Mongolia alone: **15,000+** users since Sep 2023 — Jul 2024 — [BioSpectrum Asia](https://www.biospectrumasia.com/news/50/24615/japan-based-fujifilm-expands-health-screening-service-business-in-mongolia.html).
- **77,000+** users — Dec 2024 — [Fujifilm JP news 11974](https://www.fujifilm.com/jp/ja/news/list/11974).
- **80,000+** users — Jan 2025 — [PURA release](https://www.fujifilm.com/jp/en/news/hq/11888).
- nura.in (undated, accessed Oct 2026): **82,000+ screenings, 27,000+ critical findings, 25+ parameters, 13 centers** — [nura.in](https://nura.in/).
- Bengaluru: **20,000+** screened, **1,500+** potential life-threatening risks found early — Nov 2025 — [Ukiyo Journal](https://www.ukiyo-journal.com/en/article/ai-preventive-medicine-fujifilm-nura-innovation).
- "**more than 150,000 screenings globally**" over four years; about **13–14 centers** worldwide — 31 Jan 2026 — [BioSpectrum India interview with Masaharu Morita](https://www.biospectrumindia.com/views/17/27243/india-has-strong-medical-talent-increasing-health-awareness-and-a-real-need-for-structured-preventive-care-.html). This **conflicts** with nura.in's 82,000+, which is probably stale; the 150k figure is the most recent.

**Business / IR**
- Pricing: "just above 20,000 yen". FY2030 targets: **100 sites** and **¥20B/year** global revenue. Fujifilm also aims to bring medical-AI products to all 196 countries by FY2030 — [Fujifilm IR PDF, Oct 2023](https://ir.fujifilm.com/en/investors/ir-materials/presentations/session/main/0118/teaserItems1/0/tableContents/0114/multiFileUpload2_1/link/ff_presentation_20231012_001e.pdf).
- Prices (Mar 2026): Calicut ₹18,000 (~¥30,600); Hanoi ~10 million VND (~¥60,000) — [JETRO](https://www.jetro.go.jp/biz/areareports/2026/ac822db52064c952.html). India comprehensive package ₹20,000 — [nura.in](https://nura.in/).
- The IR deck lists NURA data-use programs: the "Asia Digital Transformation" program and the "Supply Chain Resilience in the Indo-Pacific Region" program, "Verifying a mechanism of utilizing anonymous health screening data, obtained with consent from patients under a secure environment" (the deck labels the sponsor "MEXT"; the Asia DX program is a METI scheme per the [METI page title](https://www.meti.go.jp/english/mobile/2023/20230316001en.html), which returned 403) — [Fujifilm IR PDF](https://ir.fujifilm.com/en/investors/ir-materials/presentations/session/main/0118/teaserItems1/0/tableContents/0114/multiFileUpload2_1/link/ff_presentation_20231012_001e.pdf).

**Footprint (all countries; as of Oct 2026 per latest sources)**
- India (operated by FUJIFILM DKH LLP, a JV of Fujifilm and Dr. Kutty's Healthcare): Bengaluru (Feb 2021), Gurugram (Jul 2022), Mumbai (Jan 2023), Hyderabad (Nov 2023), Calicut/Kozhikode Innovation Center (Dec 2024), NURA Express mobile (~May 2025), Chennai (listed on nura.in) — [Fujifilm IR PDF](https://ir.fujifilm.com/en/investors/ir-materials/presentations/session/main/0118/teaserItems1/0/tableContents/0114/multiFileUpload2_1/link/ff_presentation_20231012_001e.pdf); [nura.in](https://nura.in/); [Fujifilm JP news 12176](https://www.fujifilm.com/jp/ja/news/list/12176). JETRO (Mar 2026) counts 5 Indian fixed sites. BioSpectrum (Jan 2026) lists Bengaluru, Mumbai, Hyderabad, "Bandra", Calicut plus a mobile unit, which is inconsistent on Gurugram/Chennai — [JETRO](https://www.jetro.go.jp/biz/areareports/2026/ac822db52064c952.html); [BioSpectrum India](https://www.biospectrumindia.com/views/17/27243/india-has-strong-medical-talent-increasing-health-awareness-and-a-real-need-for-structured-preventive-care-.html).
- Mongolia: Ulaanbaatar #1 (17 Sep 2023) and #2 (1 Aug 2024), operated by Tavan Bogd Group — [BioSpectrum Asia](https://www.biospectrumasia.com/news/50/24615/japan-based-fujifilm-expands-health-screening-service-business-in-mongolia.html).
- Vietnam: Hanoi (Jul 2024) and Ho Chi Minh City (3 Nov 2025), operated by VJH / T-Matsuoka Medical Center with Fujifilm know-how — [Fujifilm HQ news 13076](https://www.fujifilm.com/bo/en/news/hq/13076); [JETRO](https://www.jetro.go.jp/biz/areareports/2026/ac822db52064c952.html).
- UAE: PURA (Abu Dhabi, Sheikh Shakhbout Medical City, PureHealth, Jan 2025; uses NURA devices and IT) — [Fujifilm HQ news 11888](https://www.fujifilm.com/jp/en/news/hq/11888). NURA Dubai (Jumeirah, Fujifilm-direct, FY2025 target) — [Fujifilm HQ news 12811](https://www.fujifilm.com/ae/en/news/hq/12811).
- South Africa: Cape Town V&A Waterfront, operated by The InUversal Group, FY2025 target — [Fujifilm HQ news 12811](https://www.fujifilm.com/ae/en/news/hq/12811).
- Thailand: Bangkok (Chong Nonsi), FUJIFILM DKH (Thailand) Co., Ltd., reported launched 30 Jul 2026 — [The Story Thailand](https://www.thestorythailand.com/en/fujifilm-dkh-nura-health/).
- Philippines (Manila) and Malaysia (Kuala Lumpur): announced for FY2025, Fujifilm-direct — [Fujifilm HQ news 13076](https://www.fujifilm.com/bo/en/news/hq/13076). I found no confirmation that either has opened.

### Inferences
- "Critical findings" (27,000+ out of 82,000+, about 33%) likely counts any clinically significant abnormality, including lifestyle markers, not confirmed cancers. It should not be read as a cancer detection rate.
- The gap between the 150k figure and the per-release counts may reflect counting method (screenings vs. unique users) or inclusion of partner sites (PURA, Mongolia).

### Gaps
- No published cancer detection rates, stage distribution, recall/PPV, interval-cancer data, or NURA-specific AI accuracy.
- I found no RSNA, JRC, ECR, IRIA or peer-reviewed abstract using NURA data (searches on lung, coronary calcium and emphysema outcomes returned nothing NURA-specific).
- Fujifilm's DX case page and IR decks contain no NURA IT-architecture diagram.

---

## Q6. Data storage, cybersecurity, and privacy compliance (India DPDP Act 2023, Vietnam Decree 13/2023, cross-border transfer to Japan)

### Takeaway
Fujifilm's only documented data architecture for NURA is a **blockchain-based "Digital Trust Platform" (DTPF)**. It shares **anonymised, consented** screening data with a research team in Japan for AI and risk-prediction work, and was piloted under Japanese government Asia-DX programs. There are no public statements on DPDP Act, Vietnam Decree 13, Mongolian or Thai PDPA compliance, on data residency for primary images, or on cybersecurity certifications.

### Cited Findings
- Fujifilm's DTPF for NURA "employs blockchain technology to prevent data tampering and enable secure data exchange". It is "a multi-stakeholder participatory data-sharing platform that utilizes blockchain and other technologies to address the risks of spoofing, falsification, and alteration of information". Anonymised data is "securely shared with a research and analysis team in Japan", and AI analyses data to give feedback to examinees and will "predict disease risk based on health checkup data" — [Fujifilm Holdings DX case-3](https://holdings.fujifilm.com/en/about/dx/activity/product/case-3).
- IR (Oct 2023): verifying "a mechanism of utilizing anonymous health screening data, obtained with consent from patients under a secure environment" under the Asia DX and Indo-Pacific Supply Chain Resilience programs — [Fujifilm IR PDF](https://ir.fujifilm.com/en/investors/ir-materials/presentations/session/main/0118/teaserItems1/0/tableContents/0114/multiFileUpload2_1/link/ff_presentation_20231012_001e.pdf).
- Innovation Center AI development uses "患者さまの同意のもと匿名化したデータ" (data anonymised with patient consent) — [Fujifilm JP news 11974](https://www.fujifilm.com/jp/ja/news/list/11974).
- JETRO (Mar 2026): Indian screening data is handled "インドの法令や規制のもと" (under Indian laws and regulations), with possible future use for service enhancement and research — [JETRO](https://www.jetro.go.jp/biz/areareports/2026/ac822db52064c952.html).
- nura.in footer has a Privacy Policy, **GDPR Privacy Notice** and **Grievance Mechanism** — [nura.in](https://nura.in/). Thailand FAQ: "Health records remain entirely confidential between you and the medical team" and references a GDPR Privacy Notice — [nurathailand.com/faq](https://nurathailand.com/faq/).
- Patient data access is through a NURA mobile app (iOS/Android) for booking, history and results — [nura.in](https://nura.in/); NURA Express results come via a dedicated smartphone app — [Fujifilm JP news 12176](https://www.fujifilm.com/jp/ja/news/list/12176).

### Inferences
- Primary DICOM images and identifiable records probably stay in-country (India: Kerala hub and center systems), with only anonymised derivatives going to Japan via DTPF. That would fit the consent-plus-anonymisation design and DPDP Act cross-border rules, but it is not stated.
- A "Grievance Mechanism" on nura.in is consistent with Indian IT Rules/DPDP grievance-officer requirements. Explicit DPDP compliance is **not** claimed.
- For Vietnam, the partner operator (VJH) would be the data controller under Decree 13/2023. Any transfer to Japan would need a cross-border transfer impact assessment. No source confirms this happens.

### Gaps
- No source addresses DPDP Act 2023 / DPDP Rules 2025, Vietnam Decree 13/2023 (or the 2025 PDP Law), Mongolia's personal-data law, Thailand PDPA, UAE/South Africa (POPIA) compliance, or ISO 27001 / HITRUST / VAPT certifications.
- Storage location (on-prem vs. cloud region), encryption, backup/DR and retention periods for NURA images are undisclosed.
- I found no cybersecurity incidents or disclosures involving NURA.
