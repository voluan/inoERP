# Fujifilm healthcare IT portfolio for health screening centers and clinics, and what likely runs NURA

Research date: 2026-10-04. Labels used below: **[Confirmed]** means a cited source states it directly. **[Inferred]** means it is my reasoning from the cited facts. Dates are given for anything older than 2026.

Main finding up front: no public Fujifilm source names the management software (reservation, reception, billing, reporting) that runs NURA. Fujifilm's public material about NURA only ever names three things: its imaging equipment (CT, mammography), its AI ("REiLI"), and a few NURA-specific digital pieces (the NURA app, centralized remote reading, the Digital Trust Platform). Fujifilm's Japanese health checkup management package, **Hellseher NEXT (ヘルゼア ネクスト)**, came from Hitachi. It is built around Japanese insurance and billing rules, and I found nothing linking it to NURA. The most plausible non-Japanese candidate I found is **Yasasii (HIS/RIS/LIS)** from **Kameda Infologics**. This is a Japanese-owned company based in Kerala, and Fujifilm India resells its RIS next to Synapse PACS. Linking it to NURA is an inference only.

---

## Q1. Which health checkup (健診/人間ドック) management systems and related IT does the Fujifilm group sell in Japan, and what do they do?

### Takeaway
In Japan, Fujifilm's health checkup management package is **Hellseher NEXT**. It is a full health checkup operations system covering reservation, barcode reception, result entry by OCR or online, judgment and comment generation, report output, follow-up, and billing to several payers including health insurance societies. It started at Hitachi Medico and Hitachi Solutions, came to Fujifilm with the Hitachi diagnostic imaging deal in 2021, and is sold by Fujifilm Medical. Around it sit a cloud web-reservation add-on, a cloud web-reservation service for municipal checkups, the C@RNA Connect cloud referral service, the SYNAPSE imaging and AI line (PACS, SAI viewer, REiLI), the NEXUS endoscopy information system, a cloud service for organized gastroscopy screening, and chest X-ray AI (CXR-AID).

### Cited Findings
**Hellseher NEXT: product and functions [Confirmed]**
- Fujifilm Japan lists "ヘルゼア ネクスト" under its healthcare IT category "medical-examination-service-support-system" (健診業務支援システム). It describes it as a system that "健診施設の施設運営から健診データ処理、営業支援まで、健診業務をトータルでサポートする", i.e. it covers facility operations, checkup data processing and sales support. — [Fujifilm: ヘルゼア ネクスト](https://www.fujifilm.com/jp/ja/healthcare/healthcare-it/medical-examination-service-support-system/hellseher-next)
- Functions shown on the Fujifilm product page:
  - Reservation, with calendar and table views of booking counts ("カレンダー、表形式の予約人数表示")
  - Barcode reception ("バーコードによる受付")
  - Result entry by online interface or OCR ("オンラインやOCRなどさまざまな入力方法")
  - Judgment support that writes comments from test results, interview answers and findings combined ("検査結果のほかに問診結果や所見を組み合わせたコメント生成")
  - Report output under any chosen conditions ("任意の条件で各種帳票を出力")
  - Management of people who need a re-test or detailed examination ("再検査や精密検査の対象者が管理")
  - Billing to several destinations, including employer groups and health insurance societies ("団体宛、健保宛に複数個所への請求")
  - Option modules: process management (工程管理), data analysis (データ分析), and mobile or visiting checkup scheduling (巡回スケジュール)

  — [Fujifilm: ヘルゼア ネクスト](https://www.fujifilm.com/jp/ja/healthcare/healthcare-it/medical-examination-service-support-system/hellseher-next)
- Hellseher web reservation option:
  - Bookings 24 hours a day.
  - A cloud design that keeps personal information off the cloud ("クラウド上に個人情報を置かない設計").
  - Syncs contract and capacity data with the Hellseher database.
  - Handles group quotas (団体枠), recommended optional tests, and visiting or mobile checkup bookings (巡回予約).
  - Aimed at corporate checkups (企業健診) and resident checkups (住民健診).
  - Priced as an initial fee plus a flat monthly fee.

  — [Fujifilm: Hellseher NEXT Web予約](https://www.fujifilm.com/jp/ja/healthcare/healthcare-it/medical-examination-service-support-system/hellseher-next/reserve)
- Hellseher NEXT was shown as a "健診業務トータルサポートシステム" next to the chest X-ray lesion-detection AI "CXR-AID" at the FUJIFILM MEDICAL 60th Anniversary Seminar in Nagoya (event page gives no date). — [Fujifilm event page](https://www.fujifilm.com/jp/ja/healthcare/events/13808/product)
- A Fujifilm Medical job posting covers health checkup system development and SE work: requirements definition, basic design and system testing. This suggests the system is still actively developed and customized. — [Fujifilm Medical job posting (hrmos)](https://hrmos.co/pages/fms/jobs/2247260463838150656)
- A search-result snippet names Ebina General Hospital's Ebina Medical Support Center (海老名総合病院附属海老名メディカルサポートセンター) as a Hellseher NEXT user on Fujifilm's case-study page. I did not open that page. — [Fujifilm Hellseher NEXT consultation/case page](https://www.fujifilm.com/jp/ja/healthcare/healthcare-it/medical-examination-service-support-system/hellseher-next/consultation)

**Hellseher lineage: Hitachi to Fujifilm [Confirmed]**
- **Hellseher NEXT** was developed jointly by **Hitachi Medico** and **Hitachi Solutions**. The announcement came in Aug 2011, with release in **March 2012**.
  - Hitachi Medico supplied its health checkup system sales experience and operating know-how. Hitachi Solutions supplied medical business-system engineering.
  - The release named three feature groups: workflow visualization (exam progress, progress per contract, follow-up of detailed exams), integration with imaging, physiological-test and lab systems, and user customization (contract-specific information, custom reports, CSV export).
  - The standard configuration cost **about ¥30 million**, with a target of **40 systems in Japan in FY2012**.

  — [Hitachi Solutions press release, 2011-08-18](https://www.hitachi-solutions.co.jp/company/press/news/2011/0818.html)
- The original "Hellseher" was a Hitachi Medico and Hitachi Software Engineering health checkup system used with Hitachi's "EUR" report-design software. Kameda Makuhari Clinic chose it because it was a flexible, extensible package. This comes from a search summary of the Hitachi case study, which I did not open in full. — [Hitachi case study: Kameda Makuhari](https://www.hitachi.co.jp/Prod/comp/soft1/casestudy/contents/kamedamakuhari/index.html)
- Fujifilm agreed on 2019-12-18 to buy Hitachi's diagnostic imaging business for about ¥179 billion. The scope was "diagnostics imaging systems (CT, MRI, X-ray systems, ultrasound) and electronic health record". — [Fujifilm press release (US site), 2019-12-18](https://healthcaresolutions-us.fujifilm.com/?p=1110)
- The deal closed on **March 31, 2021**, when all shares were transferred. — [Diagnostic Imaging](https://www.diagnosticimaging.com/view/fujifilm-acquires-hitachi-diagnostic-imaging-business); [Hitachi High-Tech notice](https://www.hitachi-hightech.com/global/en/products/healthcare/topics/20210401.html)

**Other Fujifilm Japan screening and clinic IT [Confirmed]**
- **Municipal health checkup web reservation system (自治体向け健診Web予約システム)**, sold by Fujifilm Medical Co., Ltd.:
  - Cloud service for municipalities and health checkup institutions.
  - Web booking around the clock plus phone booking, automatic eligibility checks, real-time booking status, and childcare booking.
  - Targets people using their past attendance history and nudge theory.
  - Uses searchable encryption, and municipalities upload personal data anonymized and encrypted.
  - Two tiers: Type-Basic for a single municipality and Type-Advanced for a whole prefecture. Type-Basic starts at **¥770,000 per year**.

  — [Fujifilm: 自治体向け健診Web予約システム](https://www.fujifilm.com/jp/ja/business/health-support/health-check/reservation-system)
- **C@RNA Connect** is a cloud regional referral service (地域医療連携サービス) linking clinics to core hospitals:
  - Clinics book CT/MRI and consultations at partner hospitals 24 hours a day, 365 days a year, with live availability.
  - An optional "Online PDI" connection transfers images in IHE-PDI format without physical media.
  - Clinical documents are delivered online.

  — [Fujifilm: C@RNA Connect](https://www.fujifilm.com/jp/ja/healthcare/healthcare-it/it-integrated/carna-connect)
- **SYNAPSE line and AI**, per Fujifilm's Oct 12, 2023 Medical Systems Business Briefing:
  - SYNAPSE PACS launched in 1999 and SYNAPSE VINCENT (3D analysis) in 2008.
  - The AI brand "REiLI" was announced in 2018. The SYNAPSE SAI viewer AI interpretation platform launched in 2019, and the SYNAPSE Creative Space AI development platform in 2021.
  - Fujifilm claims SYNAPSE "continues to maintain the largest global market share" in PACS and gained share in 2022.

  — Fujifilm Holdings, *Medical Systems Business Briefing*, 12 Oct 2023 (slide and transcript text; the exact PDF URL was not captured; Fujifilm Holdings IR library: https://holdings.fujifilm.com/en/investors)
- Screening-relevant endoscopy IT from the same 2023 briefing:
  - The "NEXUS" endoscopic information management system.
  - A "Cloud service contributing to organized gastroscope screening", which securely shares screening data between gastroscopy screening sites and secondary interpretation institutes.
  - An affordable LED endoscope model aimed at "health screening centers and clinics conducting screening tests".

  — same 2023 briefing
- **Fujifilm's own checkup facilities**: Fujifilm runs in-house checkup facilities in Japan.
  - 富士フイルム健康管理センター offers 人間ドック with a results interview. — [fujifilm-kense.com](https://www.fujifilm-kense.com/ningen-dock/)
  - 富士フイルムメディテラスよこはま is run under the Fujifilm Group health insurance society and has an online 職域人間ドック reservation system (manual dated 2023-04). — [Medieterrace Yokohama](https://www.fujifilm-mediterrace.com/); [reservation manual PDF](https://www.fujifilm-mediterrace.com/pdf/%E8%81%B7%E5%9F%9F%E4%BA%BA%E9%96%93%E3%83%89%E3%83%83%E3%82%AF%E3%83%BB%E4%BA%BA%E9%96%93%E3%83%89%E3%83%83%E3%82%AF%E3%81%AE%E4%BA%88%E7%B4%84%E6%96%B9%E6%B3%95(%E6%93%8D%E4%BD%9C%E3%83%9E%E3%83%8B%E3%83%A5%E3%82%A2%E3%83%AB%E3%83%BC20230403_02).pdf)
- **App for checkup participants (健診受診者向けスマホアプリ)**, under development by FUJIFILM Corporation since July 2024:
  - Medical supervision by Integrity Healthcare Inc. (株式会社インテグリティ・ヘルスケア).
  - Tested with about 700 employees at Fujifilm Medieterrace Yokohama.
  - Planned features: optional-test recommendations based on guidelines, a digital report that includes CT images, AI-supported physician feedback, a chatbot that explains results and terms, tracking of employees who need follow-up exams, and online occupational health consultations.
  - Offering to health-conscious companies targeted by FY2026.
  - The release names NURA in India, Mongolia and Vietnam as related operations.

  — [Fujifilm news 11595](https://www.fujifilm.com/jp/ja/news/list/11595)
- Fujifilm Medical Services Solutions (富士フイルムメディカルサービスソリューション) handles sales and service for modalities in Japan (MRI, CT, X-ray, mammography, endoscopy, ultrasound, IVD). Its page lists no health checkup software. — [FMSS what-we-do](https://www.fujifilm.com/fmss/ja/what-we-do)

### Inferences
- [Inferred] Fujifilm group subsidiaries such as Fujifilm Medical sell Hellseher NEXT in Japan. It almost certainly also does Japan-specific output such as 特定健診 XML submission and 協会けんぽ forms, since Japanese health checkup packages must. The Fujifilm page summary I retrieved does not say so explicitly.
- [Inferred] Hellseher NEXT is a big on-premises package with heavy SE work: about ¥30M per site in 2012, customization, and SE job postings. Only the web-reservation part is offered as cloud. That model does not fit low-cost, fast multi-country rollout of 10 to 100 NURA sites, which counts against Hellseher being NURA's core system without major localization.
- [Inferred] The parts of the Japanese portfolio most likely to be re-used at NURA are the imaging and AI layer: SYNAPSE/REiLI, CXR-AID-type AI, and remote-reading tooling. The checkup administration layer is the least likely to be re-used.

### Gaps
- I could not open the Fujifilm Medix magazine case-study PDFs (vol. 41 and vol. 52; the medix.fujifilm.com host was unreachable). These probably describe Hellseher NEXT sites in detail.
- No current installed-base figure for Hellseher NEXT was found. The only number is the FY2012 target of 40 systems.
- No public confirmation of 特定健診 XML, station guidance or kiosk features, or PACS integration specifics for the current Hellseher NEXT version.
- I did not confirm whether a separate "Fujifilm Medical IT Solutions" entity exists under that exact name. Fujifilm Medical Co., Ltd. (富士フイルムメディカル) appears as the seller of the municipal reservation system and as the employer for health checkup system SE roles.

---

## Q2. Which Japanese health checkup institutions or know-how partners did Fujifilm use to design NURA's operations?

### Takeaway
No public source names a Japanese health checkup institution that designed NURA's operations. The sources only speak of "Japanese-style" screening. The confirmed operating know-how partner is **Dr. Kutty's Healthcare (DKH)** from Kerala, India, with which Fujifilm formed **FUJIFILM DKH LLP** in 2019. Japanese clinical input that is confirmed is narrower: Integrity Healthcare supervises the new checkup app, and Fujifilm's in-house checkup facility (Medieterrace Yokohama) was the app test site. Training and centralized remote reading are done in India, at the NURA Global Innovation Center in Kozhikode, not in Japan.

### Cited Findings
- The 2020 JETRO-supported Asia DX project ("AIと医師の協業を前提とした健診センタービジネスの発展性に関する実証実験…") names the local partner as Dr. Kutty's Healthcare (DKH). It describes the collaboration as "インド国内での検診センター運営ノウハウを保有するDKH社と協業し、健診サービスビジネスを展開する", i.e. teaming up with DKH because DKH has screening-center operating know-how in India. The project scope was screening 2,000 people to test imaging-diagnosis AI, and building abdominal (kidney, liver, gallbladder) anomaly-detection AI tested on 300 cases. — [JETRO Asia DX project sheet (©2020)](https://www.jetro.go.jp:443/ext_images/_News/announcement/2021/6854667ac8d219bd/6.pdf)
- FUJIFILM DKH LLP was formed with Dr. Kutty's Healthcare in 2019. Bengaluru and Kozhikode (Kalikat) are directly operated, while Vietnam runs on a partner model. — [JETRO area report, 2026-03-26](https://www.jetro.go.jp/biz/areareports/2026/ac822db52064c952.html)
- The NURA India website says it is "operated by FUJIFILM DKH and powered by Fujifilm's advanced medical imaging technology. Combining Fujifilm's global expertise in diagnostic imaging with Dr. Kutty's operatio[nal …]". — [nura.in](https://nura.in/)
- **NURA Global Innovation Center**, Kozhikode, Kerala, opened 2024-12-24 as the 8th NURA site. It has three roles: a screening center, a training center for physicians, radiological technologists and nurses who work across NURA, and a centralized remote-reading center for images taken at NURA sites across India. Kerala is described as DKH's home region. — [Fujifilm news 11974 (JP)](https://www.fujifilm.com/jp/ja/news/list/11974); [English version](https://www.fujifilm.com/jp/en/news/hq/11974)
- The Vietnam launch (Hanoi, 2024-07-01) has VIETNAM JAPAN HEALTH TECHNOLOGY JSC as operator, T-Matsuoka Medical Center as collaborator, and FUJIFILM DKH LLP providing operational support. Fujifilm provides "蓄積してきた健診サービスのノウハウ" (its accumulated screening-service know-how). FUJIFILM DKH draws on 45,000+ examinees across four Indian sites and one Mongolian site. — [Fujifilm news 11563](https://www.fujifilm.com/jp/ja/news/list/11563)
- In Mongolia, the Oct 2023 briefing describes the first "Opening NURA under partnership agreement": a technology partnership agreement with the conglomerate **Tavan Bogd Group**, a Fujifilm partner in photography since 1995. Ulaanbaatar opened in Sept 2023. — Fujifilm Holdings, *Medical Systems Business Briefing*, 12 Oct 2023 (IR materials; https://holdings.fujifilm.com/en/investors); see also [Fujifilm news: Ulaanbaatar](https://www.fujifilm.com/jp/en/news/hq/11626)
- Origin story: the idea came from a 2010 conversation in Dubai between a Fujifilm employee and an Indian colleague, who asked why comprehensive screening of the kind standard in Japan did not exist in India. Morita Shoji, head of new business in the Medical Systems Division, led the project. The name "NURA" comes from "New Era". — [Toyo Keizai, 2026-01-27 (partly paywalled)](https://toyokeizai.net/articles/-/930724); see also [JETRO area report 2026](https://www.jetro.go.jp/biz/areareports/2026/ac822db52064c952.html)
- Integrity Healthcare provides cooperation and medical supervision for Fujifilm's checkup-participant app, which was tested at Fujifilm Medieterrace Yokohama. — [Fujifilm news 11595](https://www.fujifilm.com/jp/ja/news/list/11595)
- For data analysis, anonymized NURA checkup data is "securely shared with a research and analysis team in Japan" through Fujifilm's blockchain-based Digital Trust Platform. — [Fujifilm Holdings DX case: NURA](https://holdings.fujifilm.com/en/about/dx/activity/product/case-3)

### Inferences
- [Inferred] The "Japanese-style" model is probably based on Fujifilm's own in-house checkup facilities (富士フイルム健康管理センター, Medieterrace Yokohama) and its Japanese imaging customer base, rather than an outside Japanese hospital partner. No source confirms that a particular Japanese institution trained NURA staff.
- [Inferred] A possible Kameda connection exists but is unproven. Kameda Medical Center's Makuhari clinic has used Hitachi's Hellseher. The Kameda family-chaired Kameda Infologics (Kerala, the same state as DKH) makes the Yasasii HIS/RIS, which Fujifilm India resells (see Q4). I found **no** source tying Kameda to NURA. Searches for "亀田 富士フイルム NURA" returned nothing relevant.

### Gaps
- The original Japanese and English NURA launch releases (Fujifilm news 5909, Jan 2021) returned HTTP 403, so I could not check whether they name a Japanese know-how partner. A search snippet of 5909 only says NURA supports doctors with "高精細な診断画像を提供する当社の医療機器やAI技術を活用したITシステム" (Fujifilm's high-definition imaging equipment and IT systems using AI). — [Fujifilm news 5909](https://www.fujifilm.com/jp/ja/news/list/5909)
- I found no source confirming that Japanese radiologists read NURA images remotely. All confirmed remote reading is by doctors at the Kozhikode hub.

---

## Q3. Has Fujifilm described the NURA "solution" as an exportable package that includes a center management system? Is there a named "NURA system"?

### Takeaway
Yes, NURA is presented as an exportable package. Fujifilm files NURA under "Packaged services" and "Network services" in its business framework, and it now licenses NURA's "運営ノウハウ" (operating know-how), equipment and medical IT to third-party operators: PURA (Abu Dhabi), VJH/T-Matsuoka (Vietnam) and Tavan Bogd (Mongolia). However, Fujifilm never names a center management or HIS product in any NURA material. The named digital pieces are the AI (REiLI), centralized remote reading, the NURA smartphone app with "Your Annual Health Report", and the Digital Trust Platform for data sharing. The generic phrase "医療ITシステム" (medical IT system) is used without a product name.

### Cited Findings
- In the Oct 2023 Medical Systems Business Briefing, NURA ("Health screening center") is listed under **"❹ Packaged services"**, described as "Services covering prevention, diagnosis and treatment", next to SYNAPSE Creative Space. Its slides carry both the "2 Network services" and "4 Packaged services" tags. The slides give a price "just above 20,000 yen", "Completing all tests and briefing in 120 minutes", and "Significantly reducing CT radiation dose with the use of AI". — Fujifilm Holdings, *Medical Systems Business Briefing*, 12 Oct 2023 (IR materials; https://holdings.fujifilm.com/en/investors)
- The same 2023 briefing describes a two-step plan: expanding sites, then "Establishing a mechanism for effective use of data obtained from health screening (e.g. analyzing health screening data to predict disease risks…)". It also cites selection for the "Asia Digital Transformation" and "Supply Chain Resilience in the Indo-Pacific Region" programs. — same source
- **PURA, Abu Dhabi** (announced 2025-01-31) opened in Sheikh Shakhbout Medical City and is run by **Pure Health**. It uses "健診センター「NURA」の運営を通じて培ってきたノウハウ" (know-how built up running NURA) together with Fujifilm's CT, mammography and AI. At that point Fujifilm had 5 sites in India, 2 in Mongolia and 1 in Vietnam, with more than 80,000 examinees. — [Fujifilm news 11888](https://www.fujifilm.com/jp/ja/news/list/11888)
- A Japanese search snippet of Fujifilm news describes PURA as adopting NURA's "運営ノウハウや医療機器・医療ITシステム" (operating know-how, medical equipment **and medical IT systems**). — [Fujifilm news list (search snippet)](https://www.fujifilm.com/jp/ja/news/list/11888)
- **NURA Express** is a mobile CT screening unit in Kerala launched March 2025 as the 10th facility. Results are fed back through "専用のスマートフォンアプリ" (a dedicated smartphone app), and images are read remotely at the Kozhikode hub. — [Fujifilm news 12176](https://www.fujifilm.com/jp/ja/news/list/12176)
- **NURA app and report**: the NURA app gives smartphone access to images and results. The "Your Annual Health Report" runs about 50 pages with A/B/C/D grades. The AI covers low-dose CT, support for radiologists, and cardiovascular and cancer risk scoring. — [JETRO area report, 2026-03-26](https://www.jetro.go.jp/biz/areareports/2026/ac822db52064c952.html)
- The app is listed on the App Store as "NURA App" (id6444829208) and on Google Play as package com.nura. — [nura.in](https://nura.in/)
- The NURA global site says "Fujifilm's AI REiLI powers our low-radiation imaging — every scan is reviewed by both AI and doctor". — [nura.one](https://nura.one/)
- **Digital Trust Platform (DTPF)** uses "blockchain and other technologies to address the risks of spoofing, falsification, and alteration". It works as a "multi-stakeholder participatory data-sharing platform" where patient consent controls data release. Anonymized data goes to a Japanese analysis team, and AI feedback goes to patients. It was selected for METI's "Indo-Pacific Region Supply Chain Resilience Project". — [Fujifilm Holdings DX case 3](https://holdings.fujifilm.com/en/about/dx/activity/product/case-3)
- **ASEAN rollout (JETRO Global South program, first round)**: an "AI健診イノベーション実証事業" (AI health-screening innovation demonstration) runs from Dec 2024 to Nov 2027. It plans NURA sites in Singapore, Malaysia, Thailand, the Philippines and elsewhere, plus a "医療データ利活用基盤" (medical data utilization platform). It is run jointly with FUJIFILM DKH LLP and FUJIFILM DKH HEALTHCARE INVESTMENT L.L.C. — [JETRO Global South adoption sheet](https://www.jetro.go.jp/ext_images/services/grobal_south/kekka-gs1/pdf/12.pdf) (text as retrieved; the PDF URL comes from search results)
- April 2026 Medical Systems Business Briefing: NURA has "a unique business model by placing AI at the core", which allows "the provision of uniform, high-standard health screening services with high reproducibility, regardless of country or region". On-site issues feed back into AI and product development, "a cycle of business operations and technological development". — Fujifilm Holdings, *Medical Systems Business Briefing*, 8 Apr 2026 (event transcript; https://holdings.fujifilm.com/en/investors)
- Scale and targets:
  - VISION2030 (Apr 2024) set a goal of 100 NURA locations by FY2030. — [Fujifilm Holdings: VISION2030](https://holdings.fujifilm.com/en/news/list/1710)
  - There were 12 sites as of January 2026. — [Toyo Keizai 2026-01-27](https://toyokeizai.net/articles/-/930724)
  - India has 5 sites (Bengaluru, Gurugram, Mumbai, Hyderabad, Kozhikode). Vietnam has 2 (Hanoi, July 2024; Ho Chi Minh City, Nov 2025). Mongolia is also operating, and the Philippines and Malaysia are planned. — [JETRO 2026](https://www.jetro.go.jp/biz/areareports/2026/ac822db52064c952.html)

### Inferences
- [Inferred] The exported "package" has four parts: (a) Fujifilm modalities (CT, mammography, X-ray, ultrasound, endoscopy), (b) the AI and imaging-IT layer (REiLI, probably SYNAPSE-family PACS and viewers, plus centralized remote reading), (c) the NURA operating playbook (120-minute flow, same-day physician feedback, staff training at the Kozhikode hub), and (d) NURA-branded patient-facing digital tools (app, annual report, DTPF data sharing). A back-office center management system is presumably included under "医療ITシステム", but the product is not named. It may be an Indian or third-party HIS, or a custom build by FUJIFILM DKH, rather than a Fujifilm Japan product.
- [Inferred] Because PURA (Pure Health) and Vietnam (VJH) are separate operators, at least some sites probably run on the operator's own HIS. That makes a single proprietary "NURA system" less likely than a standard set of imaging, AI, reporting and app components on top of local administrative software.

### Gaps
- No Fujifilm source names a "NURA system", "screening center management system", or HIS/RIS vendor for NURA.
- I could not confirm who developed the NURA app (Fujifilm Japan, FUJIFILM DKH, or an outside agency). The App Store and Play Store developer fields were not checked in this pass.

---

## Q4. Does Fujifilm sell clinic or screening management software outside Japan, and through which subsidiaries?

### Takeaway
Outside Japan, Fujifilm's healthcare IT is the **Synapse enterprise imaging line**: PACS, VNA, 3D, Mobility zero-footprint viewer, AI Orchestrator/REiLI, and RIS/EIS. In the US, Synapse is pitched to outpatient imaging centers. In India, Fujifilm India Pvt. Ltd.'s HCIT unit sells Synapse together with **"Yasasii RIS"** from **Kameda Infologics** (Trivandrum, Kerala). That gives Fujifilm a channel into an HIS/EMR/RIS/LIS family (Yasasii) in exactly the region where NURA runs. I found no evidence that Hellseher NEXT, or any Fujifilm health checkup administration package, is sold in India, ASEAN or Vietnam.

### Cited Findings
- A Fujifilm India Pvt. Ltd. HCIT presentation (Rajeev K. Jha, National Service Manager – HCIT; it mentions KLAS 2020 and "Convergence Achieved Fall 2021", so it dates from about 2021–22) lists the imaging informatics platform as Synapse Mobility, Synapse 3D Advanced Visualization, **"Yasasii RIS"**, Synapse PACS and Synapse VNA. It claims KLAS 2020 rankings of 4th globally and 1st in India, and "5200+ sites". It also shows REiLI AI platform integration and validated third-party AI vendors (ScreenPoint, Qure.ai, Riverain, CureMetrix, Harrison.ai, Aidoc, 16Bit). — [CAHO / Fujifilm India presentation PDF](https://www.caho.in/files/Rajeev_K_Jha_AI_Overview_Fujifilm_India.pdf)
- **Kameda Infologics**:
  - Founded in 2000 in Trivandrum, Kerala, with offices in New Delhi, Jeddah and Tokyo. — [Kameda Infologics (search summary of company pages)](https://kamedainfologics.net/)
  - Chairman is Dr. Toshitada Kameda. The site references "Synapse-Yasasii RIS, PACS, EMR, HIS" and Fujifilm. Products: YASASII HIS/EMR, RIS, LIS, Blood Bank, Healthcare App, Telehealth, Nursing Home, Long-term Care, Home Health and an Epidemic Management System. Clients include KIMS hospitals (India and the Gulf), Dubai Police, Danat Al Emarat and Almoosa Hospital. — [kamedainfologics.net](https://kamedainfologics.net/); [products](https://kamedainfologics.net/products)
  - The company says it "partnered with Fujifilm in Tokyo, Japan, and Fujifilm brings global presence to Kameda products and solutions" (search-result summary of the company's pages). — [Kameda Infologics RIS page](https://www.kamedainfologics.net/ris)
  - KLAS (2020-11-20) calls it "an established EMR/HIS vendor in Japan" that is expanding YASASII into the Middle East. — [KLAS first look 2020](https://klasresearch.com/report/kameda-infologics-first-look-2020/1805)
  - The Yasasii product pages I retrieved do **not** mention a health checkup or executive-wellness module. — [kamedainfologics.net/products](https://kamedainfologics.net/products)
- **US**: Fujifilm Healthcare Americas sells the cloud-capable Synapse Enterprise Imaging portfolio and has marketed a package "tailored to outpatient imaging centers". — [ITN: outpatient imaging centers](https://www.itnonline.com/content/fujifilm-unveils-comprehensive-enterprise-imaging-and-informatics-solution-tailored); [GlobeNewswire RSNA 2022](https://www.globenewswire.com/en/news-release/2022/11/21/2560034/0/en/Fujifilm-Showcases-Cloud-based-Synapse-Enterprise-Imaging-Portfolio-at-the-2022-Radiological-Society-of-North-America-Annual-Meeting.html)
- **Synapse AI Orchestrator and REiLI**: an open, vendor-neutral way to plug Fujifilm and third-party AI into Synapse workflows. — [Fujifilm US: Synapse AI Orchestrator](https://healthcaresolutions-us.fujifilm.com/products/enterprise-imaging/synapse-ai-orchestrator/)
- Fujifilm operates NURA abroad through **FUJIFILM DKH LLP** (India, 2019) and **FUJIFILM DKH HEALTHCARE INVESTMENT L.L.C.** (named in the ASEAN demonstration). — [JETRO 2026](https://www.jetro.go.jp/biz/areareports/2026/ac822db52064c952.html); [JETRO Global South sheet](https://www.jetro.go.jp/ext_images/services/grobal_south/kekka-gs1/pdf/12.pdf)
- Fujifilm Healthcare Taiwan's company page lists X-ray, endoscopy, mammography and "healthcare IT" with no product detail. — [Fujifilm Healthcare Taiwan](https://www.fujifilm.com/fmst/ja/what-we-do)

### Inferences
- [Inferred] The most likely Fujifilm-channel IT stack for NURA India is **Synapse PACS/viewer with REiLI AI** for imaging and remote reading. That fits the centralized reading hub in Kozhikode and "Fujifilm's AI REiLI powers our low-radiation imaging". It may be paired with **Yasasii RIS and possibly Yasasii HIS/LIS** from Kameda Infologics, given Fujifilm India's existing "Synapse-Yasasii" bundle and the shared Kerala base with DKH. **This is an inference; no source confirms that NURA uses Yasasii.** Other researchers' files suggest other candidate vendors (e.g., an Indian health checkup software vendor). The report writer should cross-check those notes.
- [Inferred] For partner-operated sites (PURA/Pure Health in the UAE, VJH/T-Matsuoka in Vietnam), Fujifilm's IT contribution is probably limited to imaging and AI and the NURA app and report. The local operator's HIS likely does registration and billing.

### Gaps
- No evidence found of Fujifilm selling a checkup or clinic administration product in Vietnam or ASEAN. Not found does not mean it does not exist. I did not search Fujifilm Vietnam or Thailand product pages specifically.
- The exact contractual relationship between Fujifilm and Kameda Infologics (OEM, reseller or alliance), and when it started, was not confirmed from a primary Fujifilm source.

---

## Q5. What competitor management systems exist for health screening centers, for context on what NURA's system likely offers?

### Takeaway
Japan has a mature market for health checkup packages. Besides Fujifilm's Hellseher NEXT, it includes NEC (CARNAS), Technoa (iD-Heart), KKC Information Systems (TAC 総合健診システム) and Kissei Comtec (PAXiS screening reading support), among others. These packages share a standard feature set: reservation and contract management, reception, progress or station management, result capture from devices and labs, auto-judgment and comments, report printing, follow-up, multi-payer billing, and statutory data output. I did not research international (Indian or ASEAN) competitors in depth in this pass.

### Cited Findings
- Japanese health checkup systems are described as supporting the whole flow from reservation and reception through examination to accounting and invoicing for 健康診断, 人間ドック and 特定健診. Products named in search results (I did not check each vendor page):
  - **CARNAS** (NEC), for health checkup institutions
  - **iD-Heart** (Technoa), covering 人間ドック, 協会けんぽ, 特定健診 and individual health insurance societies
  - **タック総合健診システム** (KKC Information Systems), from estimate to invoice, with more than 20 years of installations
  - **PAXiS-Screening** (Kissei Comtec), total support for checkup image reading
  - **CARADA健診サポート**, for result delivery and an app
  - Also mentioned: NEO, ALTURA and CHECKUP PRISM

  — [ASPIC health checkup service list](https://www.aspicjapan.org/asu/service/list/kenk); [Kissei Comtec PAXiS 総合健診 PDF](https://www.kicnet.co.jp/solutions/medical/paxis_top/sougoukensin_information.pdf); [Nikkan Kogyo release](https://www.nikkan.co.jp/releases/view/29954); [NJC PDF](https://www.njc.co.jp/wp-content/uploads/2019/01/3094.pdf); [2ndlabo overview](https://2ndlabo.com/ps1334/)
- NEC has offered medical software packages since the 1970s and has worked on IT for 特定健診 and 特定保健指導 (specific health checkups and specific health guidance). — [NEC Technical Journal](https://jpn.nec.com/techrep/journal/g08/n03/pdf/080302.pdf)
- The Hellseher NEXT feature set described in Q1 is a good reference for a Japanese full-function package: reservation, barcode reception, OCR or online result entry, judgment comments, reports, follow-up, multi-payer billing, process management, analytics and mobile checkup scheduling. — [Fujifilm: Hellseher NEXT](https://www.fujifilm.com/jp/ja/healthcare/healthcare-it/medical-examination-service-support-system/hellseher-next)

### Inferences
- [Inferred] Based on what Fujifilm publicly says NURA does, NURA's management layer must at least support:
  - Package-based booking: retail and B2B corporate, with about 40% B2B in Hanoi.
  - Fast reception and station or progress control to hold a 120-minute total time.
  - Modality, lab and PACS integration with AI results.
  - Remote-reading worklists.
  - Same-day physician feedback with images.
  - Structured A/B/C/D grading in a roughly 50-page report.
  - Delivery to a patient app.
  - Corporate billing and follow-up of people needing further testing.
  - Consent-based anonymized data export (DTPF).

  This matches the Japanese health checkup package model (Hellseher-type features) more than a generic hospital HIS.
- [Inferred] Japanese packages are deeply tied to Japanese insurance rules (健保/協会けんぽ billing, 特定健診 XML). NURA's overseas system would need different payer and billing logic: self-pay, corporate, and in the UAE, insurer billing through Pure Health.

### Gaps
- International health screening management vendors (Indian, ASEAN and Gulf HIS or wellness-center software) were not researched in this pass, and I have no market-share data for Japanese health checkup systems.
- The 2ndlabo comparison article returned HTTP 503. The competitor list above comes from search-result summaries and has not been checked against each vendor's own page.
