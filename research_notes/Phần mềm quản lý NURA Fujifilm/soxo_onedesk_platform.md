# SOXO (soxo.in) and the "OneDesk" platform as NURA's management system

Research date: 2026-10-04. All sources are public: company website, Indian registry aggregators, search-engine snippets of LinkedIn/ZoomInfo, the public npm registry, public Certificate Transparency (CT) logs (crt.sh), and public RDAP data. No authenticated endpoint was accessed and no API key or token was recorded. Hostnames taken from CT logs only show that a TLS certificate was issued for that name on a given date. They do not show what the host does. Every reading of a hostname's purpose below is labelled **inferred**.

Methodology note on CT evidence: CT queries were run on 2026-10-04 against `%.onedesk.app` (2,239 certificate rows) and `%.soxo.in` (1,277 rows). Dates given are the earliest and latest `not_before` dates seen for each name. Wildcard certificates (`*.onedesk.app`, `*.soxo.in`) also exist, so a host missing from the list does not prove the host does not exist.

---

## Q1. What does soxo.in say about the company, its products and clients? Is "OneDesk" a named product, and what modules does it have?

### Takeaway
soxo.in is a thin brochure site. It presents SOXO as a "business automation" and "product development" company in Cyberpark Kozhikode, and lists healthcare modules (EHR, equipment interfacing, scheduling/cancellation, inventory, accounting/billing). It names no clients and never mentions "OneDesk" or NURA. "OneDesk" appears only as the domain `onedesk.app`, which hosts SOXO's NURA, DKH and other deployments. It is not marketed as a named product anywhere public, and it is unrelated to OneDesk Inc. of Montreal.

### Cited Findings
- **Confirmed:** Homepage tagline "We make your work Faster & Smarter!". SOXO describes itself as streamlining businesses "by automating your business workflow", replacing manual processes with digital solutions — [soxo.in](https://soxo.in)
- **Confirmed:** The homepage lists these healthcare modules: Electronic Health Records (EHR), Equipment Interfacing, Scheduling and appointment cancellation, Inventory management, Accounting and billing. It also lists automation for the automobile and financial sectors — [soxo.in](https://soxo.in)
- **Confirmed:** The About page says "A company turning ideas into beautiful products", "a leading Product Development Company", solutions "from billing to customer relationship management", "Quick installation", "24/7 customer support" and "complete customization" — [soxo.in/about.html](https://soxo.in/about.html)
- **Confirmed:** Address: 3rd Floor, Sahya, Cyberpark, 167/A, Kozhikode – 673014, Kerala. Email hello@soxo.in. Phones 78 99 205111 / 8156911112. The site names no clients ("clients across globe"), no leaders and no founding date — [soxo.in](https://soxo.in); [soxo.in/about.html](https://soxo.in/about.html)
- **Confirmed:** The words "OneDesk" and "NURA" do not appear on soxo.in's Home, About or Careers pages — [soxo.in](https://soxo.in); [soxo.in/career.html](https://soxo.in/career.html)
- **Confirmed:** The apex `https://onedesk.app` currently returns an nginx 404 page behind Cloudflare (`server: cloudflare`, page footer `nginx/1.28.0`). There is no public marketing page — direct HTTP check on 2026-10-04 of [onedesk.app](https://onedesk.app)
- **Confirmed:** The current registration of onedesk.app dates from 2022-02-22 (registrar GoDaddy; nameservers elaine/huxley.ns.cloudflare.com; expires 2027-02-22) — [Google Registry RDAP for onedesk.app](https://pubapi.registry.google/rdap/domain/onedesk.app)
- **Confirmed:** CT shows wildcard certificates for onedesk.app from 2018-12 to 2019-09, then none until 2022-02-25 (`mis.onedesk.app`). The 2018–2019 certificates predate the current 2022 registration — [crt.sh %.onedesk.app](https://crt.sh/?q=%25.onedesk.app)
- **Confirmed (disambiguation):** "OneDesk" is also the brand of OneDesk Inc., a Montreal helpdesk/project-management SaaS founded in 2009 (onedesk.com, npm `@pipedream/onedesk`, `n8n-nodes-onedesk`). It is a different company — [bitscale profile of OneDesk Inc.](https://ghost.bitscale.ai/onedesk-inc/); [npm search "onedesk"](https://registry.npmjs.org/-/v1/search?text=onedesk&size=20)
- **Confirmed:** Module-like hostnames under onedesk.app include `nura-desk-*` (staff desk UI) and `nura-api-*` (API) for each country, plus `nuracrm`, `nurafeedback`, `nura-payment*`, `nura-communication`, `nura-api-emr`/`emr`, `nura-api-diagnosis`/`nura-desk-diagnosis`, `finalreport`, `nura-pdf-exporter`, `nura-profile-exporter`, `nura-exporter`, `qmsdkh`/`qmsapi`, `qcdkh`/`qc-dev-api`, `mis`/`misapireports`, `superset`, `auth`, `nura-api-keycloak`, `phr-api-in-uat`/`phr-keycloak`, `abdm`/`abdmapi`, `helpdesk`, `tickets`, `onesight`/`nuraonesight`, `engage-dev`, `xrayr`, `dkh-pacs` — [crt.sh %.onedesk.app](https://crt.sh/?q=%25.onedesk.app)

### Inferences
- **Inferred:** "OneDesk" is SOXO's internal or platform brand. The staff application appears to be called "NURA Desk" (`nura-desk-<country>`), with a matching backend, "NURA API" (`nura-api-<country>`). The prior research's `nuraapi.onedesk.app/prod` fits this pattern (`nuraapi.onedesk.app` certificates 2025-01-13 → 2025-03-14).
- **Inferred module map from hostnames** (names only, not verified functionally):
  - Staff desk UI: `nura-desk-*`.
  - Queue management: `qmsdkh`, `qmsdkh2`, `qmsapi`, `qms-dubai.soxo.in`, `qms-dkh-test.soxo.in`.
  - Quality control or checklists: `qcdkh`, `qc-ui`, `qc.soxo.in`.
  - CRM: `nuracrm`.
  - Patient feedback: `nurafeedback`, `feedback-api-th`, `feedback-api-mn-dev`, `feedback-dev-iq-api`.
  - Payments, separate per country: `nura-payment`, `nura-th-payment`, `nurath-payment-api`, `nura-payment-in-ui`.
  - Messaging: `nura-communication`, `engage-*`.
  - EMR: `emr`, `nura-api-emr`.
  - Report generation and PDF export: `finalreport`, `nura-pdf-exporter`, `nura-profile-exporter`.
  - MIS and BI: `mis`, `misapireports`, `superset` (Apache Superset).
  - Single sign-on: `auth`, `nura-api-keycloak`, `phr-keycloak` (Keycloak).
  - Personal health record: `phr-api-in-uat`.
  - India's Ayushman Bharat Digital Mission (ABDM/ABHA) integration: `abdm`, `abdmapi`, `abdm-dev-ui`.
  - Support desk: `helpdesk`, `tickets`.
  - Imaging: `dkh-pacs`, `xrayr`.
- **Inferred:** This set matches what the user asked about (reception, scheduling, queue/stations, billing/payments, EHR/EMR, report generation, analytics). Lab/LIS and inventory are not visible as separate hostnames (see Q4).

### Gaps
- No public product page, brochure, datasheet or screenshot names "OneDesk" or describes its modules. The module list above comes from hostnames only.
- The LinkedIn headline from prior research ("IT Division of Nura Centres : by Fujifilm-Japan and DKH-India") could not be re-found in this session. LinkedIn returned HTTP 999 to direct fetches.

---

## Q2. Who owns SOXO? Legal entities, identifiers, partners, and overlap with Dr. Kutty's Healthcare / FUJIFILM DKH LLP

### Takeaway
SOXO operates through two LLPs, not a private limited company. Both have the same three designated partners: Mohamed Kasim (DIN 01504489), Ashique Mohammed Athikkal and Thekkumpat Subrahmanian Anoop. Mohamed Kasim is also a designated partner of **FUJIFILM DKH LLP**, a director of **Dr. Kutty's Healthcare Pvt Ltd**, and a partner or director in about 14 other DKH-group entities. He also appears as Managing Director of Matria Hospital (formerly Cradle Hospital), Kozhikode. SOXO is therefore a DKH-group affiliate, controlled at least in part by the same person who sits on the FUJIFILM DKH JV.

### Cited Findings
- **Confirmed: Entity 1, SOXO TECH LLP**
  - LLPIN AAX-0496, incorporated 17 May 2021, ROC Bangalore, status Active.
  - Registered office: No. 39, Ground Floor, Dickenson Road, Bangalore 560042.
  - Activity: "Information Technology (Application Development & Software Solutions)". Contribution/authorised capital ₹1.00 lakh.
  - Last balance sheet filed for FY ending 31-Mar-2025.
  - Designated partners, all appointed 17 May 2021: Thekkumpat Subrahmanian Anoop (DIN 09162023), Ashique Mohammed Athikkal (DIN 09161890), Mohamed Kasim (DIN 01504489).
  - Sources: [Infyner – Soxo Tech LLP](https://www.infyner.com/company/soxo-tech-llp/AAX-0496); [search snippet of Paperli/TheCompanyCheck](https://paperli.ai/company/soxo-tech-llp-AAX-0496)
- **Confirmed: Entity 2, SOXO TECHNOLOGIES LLP**
  - LLPIN ABB-2977, incorporated 06 Jun 2022, ROC Ernakulam, status Active.
  - Registered office: 19/1924 C, Sheratton Complex, Chalappuram (near Ganapath Boys High School), Kozhikode 673002.
  - Designated partners: Thekkumpat Subrahmanian Anoop and Ashique Mohammed Athikkal (both 2022-06-06), and Mohamed Kasim (2022-08-17). Capital shown as ₹1.39 lakh. Last balance sheet 31-Mar-2025.
  - Infyner lists the business activity as "Aviation (Air Transportation)", which is likely a misclassification in the aggregator or the filing.
  - Sources: [Infyner – Soxo Technologies LLP](https://www.infyner.com/company/soxo-technologies-llp/ABB-2977); [Paperli snippet](https://paperli.ai/company/soxo-technologies-llp-ABB-2977); also listed at [Tofler](https://www.tofler.in/soxo-technologies-llp/company/ABB-2977), [Falcon Ebiz](https://www.falconebiz.com/LLP/SOXO-TECHNOLOGIES-LLP-ABB-2977) and [Filesure](https://www.filesure.in/company/soxo-technologies-llp/ABB-2977?tab=about) (not opened)
- **Confirmed:** Search snippets tie the Cyberpark address (3rd Floor, Sahya, Cyberpark) to Soxo Technologies LLP — [search result summary citing Tofler/Filesure](https://www.tofler.in/soxo-technologies-llp/company/ABB-2977)
- **Confirmed: Ashique Mohammed Athikkal** (DIN 09161890, Malappuram) is a designated partner in exactly these two LLPs among his visible current appointments — [Infyner profile](https://www.infyner.com/people-profile/ashique-mohammed-athikkal/09161890). The npm package `soxo-application-loader` (2023) gives "Ashique Mohammed" as its author — [npm registry](https://registry.npmjs.org/soxo-application-loader)
- **Confirmed: Mohamed Kasim** (DIN 01504489, Malappuram) has 16 current appointments — [Infyner profile](https://www.infyner.com/people-profile/mohamed-kasim/01504489):
  - Designated partner: FUJIFILM DKH LLP (AAR-1513, incorporated 26 Nov 2019, Kozhikode); Dr. Kutty's Healthcare Services LLP (AAQ-8555); Soxo Tech LLP; Soxo Technologies LLP; DKH Motors LLP; DKH Cars LLP (Chalappuram); DKH Realtors LLP; DKH Holdings LLP; DKH Properties LLP (2024); Prostick Tech LLP (2021); Frontier Infraventure LLP (2026).
  - Director: Dr. Kutty's Healthcare Pvt Ltd (U85110KL2008PTC022476, 23 May 2008, Tirur); Cradle Calicut Maternity Care Pvt Ltd (U85110KL2009PTC024936); Infutec Healthcare (TN) Pvt Ltd; Tirur My School Foundation.
  - Managing Director: DKH Developers Pvt Ltd.
- **Conflicting:** A Paperli snippet for FUJIFILM DKH LLP lists only two designated partners, Paniketty Unni Subin (DIN 08621952) and Habeeb Rehiman (DIN 01504406), both appointed 26-Nov-2019. Infyner additionally lists Mohamed Kasim as a designated partner. Registered address per Paperli: Door No 2/1085 A10, Matria, Palazhi, NH 17 Bypass Road, Calicut — [Paperli – FUJIFILM DKH LLP](https://paperli.ai/company/fujifilm-dkh-llp-AAR-1513) vs. [Infyner – Mohamed Kasim](https://www.infyner.com/people-profile/mohamed-kasim/01504489)
- **Confirmed:** Matria Hospital, Calicut (formerly "Cradle Hospital Calicut", established 2010, gynaecology and neonatal care) was founded by Dr. V. K. Kutty ("Dr Mohammed Kutty" in the infobox). It lists **Dr. Mohammed Kasim as Managing Director** — [Wikipedia: Matria Hospital](https://en.wikipedia.org/wiki/Matria_Hospital)
- **Confirmed:** NURA's site names "Dr Kutty's Healthcare" and "Fujifilm" as parent organisations — [nura.in/technology](https://nura.in/technology/)
- **Confirmed (aggregator, unverified):** A search summary drawn from ZoomInfo, RocketReach and Tracxn describes Soxo as "a Software Development company located in Kozhikode, Kerala with 38 employees. It was founded in 2021". The underlying pages returned 403 — [ZoomInfo](https://www.zoominfo.com/c/soxo/1311446110); [RocketReach](https://rocketreach.co/soxo-profile_b7fe47f3c25c34f6); [Tracxn](https://tracxn.com/d/companies/soxo/__pd8IXBlssHLhGC6802pyeZ1ENhHZ55wzXvJ1tSuMJLw)
- **Confirmed:** The earliest CT certificate for soxo.in / www.soxo.in is dated 2021-07-07 — [crt.sh %.soxo.in](https://crt.sh/?q=%25.soxo.in)

### Inferences
- **Inferred:** The "Dr Mohammed Kasim, MD/CEO" in the prior research is very likely the same person as registry partner Mohamed Kasim (DIN 01504489). The basis: the DKH-group directorships, the Matria MD title on Wikipedia, and the Cradle Calicut Maternity Care directorship. No public source found here explicitly calls him "CEO of SOXO".
- **Inferred:** SOXO Tech LLP was set up in Bangalore in May 2021, in the same year Fujifilm opened its first NURA centre in Bengaluru (2021). The Kozhikode LLP followed in June 2022. This timing is consistent with SOXO being formed as the DKH group's captive IT arm for NURA.
- **Inferred:** The registered address of Soxo Technologies LLP (Sheratton Complex, Chalappuram) is in the same locality as DKH Cars LLP (Chalappuram). This suggests group-shared premises before the move to Cyberpark.
- **Inferred, weak:** Habeeb Rehiman's DIN (01504406) is numerically close to Mohamed Kasim's (01504489). This hints that both obtained DINs at about the same time (DKH-group insiders), but it proves nothing.
- **Inferred:** No evidence was found of Fujifilm (Japan or India) holding any stake in SOXO. The only Fujifilm link is through the FUJIFILM DKH LLP JV, where the DKH side and SOXO share a partner.

### Gaps
- Partner contribution percentages, revenue and profit for either LLP: these sit behind paywalls (Infyner, Tofler) and were not retrieved.
- Whether either LLP's partners hold their stakes on behalf of Dr. Kutty's Healthcare or DKH Holdings LLP is unknown.
- The role of Thekkumpat Subrahmanian Anoop (DIN 09162023) was not established. He may be a technical co-founder.
- MCA master data was not checked directly because of the portal's captcha.

---

## Q3. Tech stack, team size and NURA work (LinkedIn, jobs, npm/GitHub)

### Takeaway
SOXO's public npm packages confirm a **React (Ant Design/Bootstrap) front end with a NestJS back end**, plus Firebase utilities, i18n (en/ar/de), PDF generation and viewing, QR/barcode, e-signature consent, camera capture, SecuGen fingerprint capture, a configurable workflow ("process/steps") engine and a backend-driven reporting engine. 2025–26 versions add OpenAI Realtime and Gemini Live voice features. Job ads ask for React, Node.js, Python, Frappe (ERPNext), DevOps and QA. LinkedIn and ZoomInfo snippets show SOXO engineers working on "the Nura product", including an on-site go-live at SSMC Abu Dhabi. The aggregator headcount is about 38.

### Cited Findings
- **Confirmed (careers page, undated, current on 2026-10-04):** Openings at Cyberpark: Senior Front End Developer (React.js, 4+ yrs), Senior Back End Developer (Node.js, 4+ yrs), Python Developer, Quality Analyst, **Frappe Developer**, DevOps Engineer, Full Stack Developer (Node.js + React.js), UI/UX Designer — [soxo.in/career.html](https://soxo.in/career.html)
- **Confirmed:** npm user "soxo" (later "soxo-dev") publishes the following packages — [npm search "soxo"](https://registry.npmjs.org/-/v1/search?text=soxo&size=20):
  - `soxo-bootstrap-core`: 215 versions, 2022-10-13 → 2025-12-09.
  - `ui-soxo-bootstrap-core`: 169 versions, 2025-12-15 → 2026-09-25, latest 2.6.61.
  - `soxo-firebase-core`: 81 versions, 2022-10 → 2025-01.
  - `soxo-react-scripts`: a CRA fork, 2022.
  - `soxo-view-builder`: 2023.
  - `soxo-application-loader`: 2023.
  - The repository and homepage fields point to the GitHub org **soxo-tech** (`github.com/soxo-tech/firebase-core`, `github.com/soxo-tech/soxo-bootstrap-core`).
  - Sources: [npm: ui-soxo-bootstrap-core](https://registry.npmjs.org/ui-soxo-bootstrap-core); [npm: soxo-bootstrap-core](https://registry.npmjs.org/soxo-bootstrap-core)
- **Confirmed:** The package's developer docs say "We use React on the front end and NestJS for the backend", that developers start from a "Starter-Kit" for front end and back end, and that there is an "inbuilt" user-rights module — [unpkg: core/lib/introduction.md](https://unpkg.com/ui-soxo-bootstrap-core@2.6.61/core/lib/introduction.md)
- **Confirmed:** Release process: Jira task branches (`task/<JIRA-ID>-…`), a `develop` channel (`-dev.N` tags) and `master`/`latest`, published via GitHub Actions. Husky, Prettier, ESLint and Jest configs are present — [unpkg: DEVELOPER_GUIDE.md](https://unpkg.com/ui-soxo-bootstrap-core@2.6.61/DEVELOPER_GUIDE.md)
- **Confirmed: Dependencies** — [npm registry metadata](https://registry.npmjs.org/ui-soxo-bootstrap-core):
  - UI: react, react-router-dom, antd, bootstrap, framer-motion.
  - Data: firebase, i18next/react-i18next, moment-timezone, xlsx, react-csv.
  - PDF: pdf-lib (+ fontkit), pdfjs-dist, @react-pdf-viewer.
  - Capture and identity: html5-qrcode, qrcode.react, react-barcode, react-signature-canvas, react-html5-camera-photo, react-phone-input-2, libphonenumber-js.
  - Maps: google-map-react.
  - Admin tooling: react-ace and react-json-editor-ajrm (in-app script/JSON editors).
- **Confirmed: Package structure** — [unpkg file listing](https://unpkg.com/ui-soxo-bootstrap-core@2.6.61/?meta):
  - Core models: users, roles, menu-roles, menus, permissions, pages, modules, lookup-types/values, branches, departments, financial-years, invoice-numbers, process, steps, step-transactions, process-transactions, checklists, comments, attachments, outbox, user-preferences, scripts.
  - Masters: doctor and staff.
  - Components: consent (signature-pad, pdf-signature), finger-print-reader, finger-print-search, fingerprint-protected element, camera/web-camera, approval-form/approval-list, notice-board, spotlight-search, license-alert, a business "slots" component.
  - Reporting: dashboard and reporting modules.
  - Themes: a `nura-theme.png` among the theme assets.
- **Confirmed:** The doctor master form has In House / Out Side type, Reg. No., Qualification, Designation, Signature and contact fields — [unpkg: doctor-add.js](https://unpkg.com/ui-soxo-bootstrap-core@2.6.61/core/models/doctor/components/doctor-add/doctor-add.js)
- **Confirmed:** The fingerprint reader calls `https://localhost:8443/SGIFPCapture`, which is the local endpoint of the SecuGen fingerprint WebAPI — [unpkg: finger-print-reader.js](https://unpkg.com/ui-soxo-bootstrap-core@2.6.61/core/lib/components/finger-print-reader/finger-print-reader.js)
- **Confirmed:** `ProcessStepsPage` is a "generic multi-step process runner". It loads process steps from the backend, tracks step and process timings, and supports Next/Back/Skip/Finish and chaining to the next process. It also supports "voice-controlled navigation through Gemini Live API" and step-level text-to-speech narration. It reads the URL params `opb_id`/`reference_id` and `opno`/`reference_number` for the process log — [unpkg: core/modules/steps/readme.md](https://unpkg.com/ui-soxo-bootstrap-core@2.6.61/core/modules/steps/readme.md). A companion `openai-realtime.js` defaults to model `gpt-realtime` via `api.openai.com/v1/realtime/calls` — [unpkg: openai-realtime.js](https://unpkg.com/ui-soxo-bootstrap-core@2.6.61/core/modules/steps/openai-realtime.js)
- **Confirmed:** The reporting dashboard renders backend-configured reports: `input_parameters` (filter form) and `display_columns` from `CoreScripts.getReportingLisitng(...)`, keyed by a `dbPtr` "db pointer" (falls back to `localStorage.db_ptr`) — [unpkg: reporting-dashboard README](https://unpkg.com/ui-soxo-bootstrap-core@2.6.61/core/modules/reporting/components/reporting-dashboard/README.md)
- **Confirmed (LinkedIn snippet):** A SOXO Technologies software engineer's profile describes building "scalable, high-performance web applications and delivering real-time healthcare solutions". It also mentions "successful on-site implementation of the Nura Healthcare Platform at SSMC Hospital, Abu Dhabi, with seamless deployment, system integration, and staff training", a platform "developed by Soxo Technologies in collaboration with DKH & Fujifilm" — [LinkedIn profile (search snippet)](https://www.linkedin.com/in/masood-abdul-samad-08287919b/)
- **Confirmed (ZoomInfo snippet):** A "Full Stack Engineer at Soxo, currently engaged with the Nura product, operating in the healthcare domain" — [ZoomInfo person page (snippet)](https://www.zoominfo.com/p/Hasna-Noufal/9043103537)
- **Confirmed (CT):** Hostnames contain `nuradockerdev` (from 2023-11), `nura-apiec2-in-qa` (2025-09/10), `superset` (2026-03) and `nura-api-keycloak` (2026-06). onedesk.app sits behind Cloudflare with nginx 1.28.0 at the origin — [crt.sh %.onedesk.app](https://crt.sh/?q=%25.onedesk.app); HTTP check of [onedesk.app](https://onedesk.app)
- **Confirmed (CT):** `orthanc.soxo.in` certificates were issued 2023-07-20 → 2023-10-10 — [crt.sh %.soxo.in](https://crt.sh/?q=%25.soxo.in)

### Inferences
- **Inferred stack:**
  - Front end: React SPA (CRA/webpack) with Ant Design, using SOXO's shared component library.
  - Back end: NestJS (Node.js/TypeScript), with metadata-driven menus, roles, processes and reports.
  - Infrastructure: Docker, likely AWS EC2 (from the "ec2" hostname), Cloudflare in front of nginx.
  - Identity and BI: Keycloak SSO and Apache Superset BI (2026).
  - Patient portals: Firebase on the patient-facing side (prior research: nura.in portal is React + Firebase + Razorpay).
  - Other: Python for some services, Frappe/ERPNext for ERP work (`dkherp.onedesk.app` is a plausible candidate).
- **Inferred:** `opb_id`/`opno` is Indian HIS jargon for OP (outpatient) bill ID and OP number. The process log is therefore keyed to the patient visit or bill, consistent with a guest-journey workflow (registration → stations → report → consult) driven by the generic process/steps engine.
- **Inferred:** The fingerprint (SecuGen), camera, signature-pad consent and QR/barcode components point to front-desk patient identification, consent capture and wristband or label printing at reception.
- **Inferred:** The OpenAI Realtime and Gemini Live voice-navigation and narration features (2025–26) may relate to NURA's AI-assistant or results-explanation ambitions, but nothing public ties them to the patient-facing avatar.
- **Inferred:** `orthanc.soxo.in` suggests that SOXO ran an Orthanc (open-source DICOM server) instance in 2023, probably for DICOM integration or testing.
- **Inferred:** Team size is roughly 30–50 people, based on the aggregator figure of 38 and eight concurrent job openings.

### Gaps
- No direct evidence of .NET or Flutter. The NURA mobile app's framework was not established here.
- No job ad was found that mentions HL7, ASTM, DICOM MWL or analyzer interfacing. Indeed and Naukri pages returned 403, and LinkedIn returned 999.
- The GitHub org `soxo-tech` could not be browsed from this environment (403 from proxy, and search API blocked).
- Headcount was not verified from a primary source.

---

## Q4. Public evidence on NURA's staff-side handling of LIS/analyzers, DICOM MWL to Fujifilm CT/mammography, SYNAPSE PACS/REiLI integration, and the AI-avatar results explanation

### Takeaway
Fujifilm publicly describes only a "medical IT system based on AI technology" and names its imaging AI (REiLI, PixelShine). It never names SOXO or any software vendor, and gives no LIS or MWL details. SOXO's own site claims "Equipment Interfacing". CT logs show a DICOM server (Orthanc, 2023), a `dkh-pacs` host (Sept 2026), `xrayr` and report-export services. No public document describes analyzer (ASTM/HL7) interfacing, modality worklists, or a SYNAPSE/REiLI integration by SOXO. The AI-avatar work is publicly attributed to a Fujifilm and Microsoft Japan research collaboration, not to SOXO.

### Cited Findings
- **Confirmed:** NURA's technology page names REiLI ("uses deep learning and Fujifilm's extensive image processing database to detect abnormalities automatically") and FCT PixelShine (deep-learning low-dose CT enhancement). It describes a low-dose CT, digital mammography with AI, transnasal endoscopy (LCI/BLI), and a 120-minute flow with same-day physician review and a digital health report — [nura.in/technology](https://nura.in/technology/)
- **Confirmed:** Fujifilm press releases describe "Fujifilm's medical devices and medical IT system based on AI technology designed to support doctors". Results come in about 120 minutes, and patients "hear the results from a doctor while viewing the actual diagnostic images". No software vendor is named — [Fujifilm PURA release, 2025-01-31](https://www.fujifilm.com/my/en/news/hq/11888); [Fujifilm ASEAN release, 2025-10-30](https://www.fujifilm.com/in/en/news/hq/13076)
- **Confirmed:** The Hyderabad opening release (2023-11-17) says: "NURA will promote research on AI assistant avatars that support feedback of health screening results and post-health screening follow-up using AI technology", in collaboration with Microsoft Japan Co., Ltd. At that date there were four NURA locations (Bengaluru, Gurugram, Mumbai, Ulaanbaatar) and about 17,000 users — [Fujifilm news 10875](https://www.fujifilm.com/in/en/news/hq/10875)
- **Confirmed:** NURA Express (2025-03-18) is a CT bus in Kozhikode. Images are read remotely at the NURA Global Innovation Center, and results go to users through a dedicated smartphone app. It was called the tenth NURA-related centre — [Fujifilm news 12176](https://www.fujifilm.com/in/en/news/hq/12176). The CT log shows `nura-api-ct-bus-test.onedesk.app` issued 2025-03-12, six days before the announcement — [crt.sh %.onedesk.app](https://crt.sh/?q=%25.onedesk.app)
- **Confirmed:** Fujifilm's "Digital Trust Platform" case study for NURA describes a blockchain-based, consent-driven data-sharing platform. Anonymised NURA health data from India and Mongolia was shared with a research team in Japan under METI's Indo-Pacific supply-chain resilience project. No vendor is named — [Fujifilm Holdings DX case 3](https://holdings.fujifilm.com/en/about/dx/activity/product/case-3). CT shows `datatrust.soxo.in` issued 2022-09-30 — [crt.sh %.soxo.in](https://crt.sh/?q=%25.soxo.in)
- **Confirmed:** SOXO's homepage lists "Equipment Interfacing" among its healthcare modules — [soxo.in](https://soxo.in)
- **Confirmed (CT):** Imaging and report hostnames: `orthanc.soxo.in` (2023-07 → 2023-10), `dkh-pacs.onedesk.app` (first cert 2026-09-25), `xrayr`/`xrayr-api.onedesk.app` (2025-10 →), `finalreport.onedesk.app` (2025-08 →), `nura-pdf-exporter`/`nura-profile-exporter`/`nura-exporter.onedesk.app` (2026-09-09), `nuraai.soxo.in` (2023-03 →) — [crt.sh %.onedesk.app](https://crt.sh/?q=%25.onedesk.app); [crt.sh %.soxo.in](https://crt.sh/?q=%25.soxo.in)

### Inferences
- **Inferred:** The split of work most consistent with the evidence:
  - Fujifilm supplies the modalities (CT, mammography, endoscopy) and imaging IT (PACS/viewer with REiLI/PixelShine AI).
  - SOXO's OneDesk/NURA Desk supplies the guest-journey layer: booking, reception, consent, queue/stations, billing/payments, EMR/consultation, report assembly and PDF export, the patient app/portal backend, CRM and feedback.
  - Interfacing between the two would be needed for patient demographics and orders to the modalities (MWL) and for image or report links back. No public source describes how this is done.
- **Inferred:** `datatrust.soxo.in` (Sept 2022) may be SOXO's piece of the Fujifilm Digital Trust Platform pilot with NURA India/Mongolia, but this is unconfirmed.
- **Inferred:** `nuraai.soxo.in` and the OpenAI/Gemini voice features in SOXO's library may support AI-assistant features. The Microsoft-avatar research is attributed to Fujifilm, so who implements the avatar is unknown.

### Gaps
- There is no public evidence on which LIS NURA uses, on analyzer models, or on ASTM/HL7 interfacing.
- There is no public evidence of DICOM MWL generation from OneDesk to Fujifilm modalities, or of the SYNAPSE version, cloud versus on-premises deployment, or whether REiLI runs inside SYNAPSE SAI viewer.
- The meaning of `dkh-pacs` (a SOXO-hosted PACS, an Orthanc-based store, or a proxy to Fujifilm SYNAPSE) is unknown.

---

## Q5. Other customers of SOXO/OneDesk, and sales outside India

### Takeaway
The public footprint is almost entirely the DKH and NURA ecosystem: NURA (many countries), PURA (PureHealth at SSMC, Abu Dhabi), DKH and Matria Hospital (Kozhikode), DKH Dubai entities, an unidentified "Al Salama" deployment, an unidentified "Your Centre" multi-site client in Kerala (Tirur, Vadakara), and a Stop-TB-related project. There is no evidence that SOXO markets OneDesk to unrelated third parties under its own brand.

### Cited Findings
- **Confirmed (CT, soxo.in):**
  - DKH: `dkh.soxo.in` (2022-09), `dkhapi.soxo.in` (2022-10 → 2026).
  - Matria: `matria.soxo.in` (2022-09), `matria-dev.soxo.in` (2022-11 → 2023-12).
  - Al Salama: `alsalama.soxo.in`, `alsalama-dev.soxo.in` (2022-11 → 2026).
  - Queue management: `qms-dubai.soxo.in` (2023-01 →), `qms-dkh-test.soxo.in` (2023-06 →).
  - Stop TB: `stoptb.soxo.in` (2022-11 →).
  - Other: `crm-dev`, `insiderapi(-v2)`, `chat.soxo.in` (2025-07), `ulbrwebuat.soxo.in` (2023-08).
  - Source: [crt.sh %.soxo.in](https://crt.sh/?q=%25.soxo.in)
- **Confirmed (CT, onedesk.app):**
  - DKH: `dkhone` (2024-11 →), `dkhdxbone` (2023-11 →), `dxb1uat` (2024-05 → 10), `dkherp`/`dkherp-test` (2024-11 →), `qmsdkh`/`qmsdkh2`, `qcdkh`, `dkh-pacs`.
  - Matria: `matria-test` (2025-07 →).
  - Al Salama: `alsalama-dev`, `nura-api-alsalama-dev`, `nura-desk-alsalama-dev` (2025-04 →).
  - "Your Centre": `yourcenter` (2023-10 →), `yourcentertirur`, `yourcentervadakara` (2024-11 →), `yourcentre`/`yourcentre2`, `api-yourcentre-dev`, `yourcenter-ontashdev`.
  - Dubai accounting: `yourbooksdxb` (2026-01 →).
  - Stop TB: `stoptb-india-ui-dev` (2023-11 →).
  - Unidentified: `nims`, `th-nims` (2025-06 / 2025-10 →), `aestcui` (2023-12 →), `starter-api`, `applications`, `auto-run`.
  - Source: [crt.sh %.onedesk.app](https://crt.sh/?q=%25.onedesk.app)
- **Confirmed:** Matria Hospital (formerly Cradle Hospital), Calicut, has Dr. Mohammed Kasim as MD — [Wikipedia](https://en.wikipedia.org/wiki/Matria_Hospital). FUJIFILM DKH LLP's registered address is "Matria, Palazhi … Calicut" — [Paperli](https://paperli.ai/company/fujifilm-dkh-llp-AAR-1513)
- **Confirmed:** PURA health screening centre opened 2025-01-31 at Sheikh Shakhbout Medical City, Abu Dhabi. It is managed and operated by Pure Health and uses "Fujifilm's medical devices and medical IT systems" drawing on NURA expertise — [Fujifilm news 11888](https://www.fujifilm.com/my/en/news/hq/11888). CT shows `pura-api-dubai-release` and `pura-desk-dubai.onedesk.app` (2025-04-16 →) — [crt.sh](https://crt.sh/?q=%25.onedesk.app). A SOXO engineer's LinkedIn mentions on-site implementation of the "Nura Healthcare Platform at SSMC Hospital, Abu Dhabi" — [LinkedIn snippet](https://www.linkedin.com/in/masood-abdul-samad-08287919b/)
- **Confirmed:** Fujifilm India ran "NEVER STOP" TB screening campaigns in Kerala (Wayanad) with handheld X-ray and Qure.ai CAD. No SOXO or DKH role is mentioned — [BioSpectrum India](https://www.biospectrumindia.com/news/97/21967/fujifilm-india-launches-second-phase-of-tb-campaign.html)

### Inferences
- **Inferred:** OneDesk is reused as a multi-tenant HIS/ERP-style platform across the DKH group:
  - Matria Hospital, with "QMS" and "QC" variants for DKH.
  - DKH ERP (Frappe/ERPNext, given the Frappe job ad).
  - DKH Dubai entities (`dkhdxbone`, `dxb1uat`, `yourbooksdxb`).
- **Inferred:** "Your Centre" at Tirur, Vadakara and a third site ("ontash"?) is a multi-branch clinic or diagnostic client in Malabar, Kerala. Tirur is DKH's home town (Dr. Kutty's Healthcare Pvt Ltd is registered in Tirur). Its identity and ownership were not found.
- **Inferred:** "Al Salama" (2022 → 2026, including a NURA-branded API/desk) may be a hospital or health centre in the Gulf. Al Salama Hospital in Abu Dhabi and Emirates Health Services' Al Salama Health Center in Dubai are candidates, but this is unconfirmed.
- **Inferred:** `stoptb.soxo.in` and `stoptb-india-ui-dev` may be a TB-screening data app tied to a Stop TB Partnership or Fujifilm TB programme in India. SOXO's role is unconfirmed.
- **Inferred:** "Selling outside India" is in practice NURA/PURA deployment across Fujifilm's network plus DKH's own Gulf entities. No independent foreign customer was found.

### Gaps
- No public case study, testimonial, client logo or press release names any SOXO customer.
- The identities behind "Your Centre", "Al Salama", "nims", "aestcui", "ulbr" and "insider" are unresolved.

---

## Q6. How OneDesk is deployed for NURA centres outside India (Vietnam, Mongolia, Thailand, UAE and others)

### Takeaway
CT logs show a consistent **per-country deployment pattern**: separate `nura-api-<cc>` back ends and `nura-desk-<cc>` staff front ends, with dev/qa/uat/staging/release tiers, and separate payment and feedback services per country. Certificates appear for India, UAE/Dubai, PURA (Abu Dhabi), Mongolia, Vietnam (Hanoi), Thailand, South Africa, the Philippines, Uzbekistan, Iraq (`iq`) and Sri Lanka (`lk`). Several of these predate Fujifilm's public announcements. Customer-facing country portals (api.nura.vn, api.nurathailand.com) are separate domains (from prior research).

### Cited Findings (all CT dates from [crt.sh %.onedesk.app](https://crt.sh/?q=%25.onedesk.app) unless stated)
- **India:**
  - Per-centre hosts: `nuraindia` (2023-10 →), `nurahyderabad` (2023-11-28 →), `nura.onedesk.app` (2023-11 →).
  - Release tiers: `nura-api-india-release-20` (2024-10 →), `nura-desk-india-staging`/`-test`, `nura-api-in-uat`/`-in-qa` (2025-07 →), `nura-payment-in-ui` (2026-06).
  - India-only services: `abdm`/`abdmapi` (2025-08/09 →), `phr-api-in-uat` (2026-07).
  - `nura-mumbai.soxo.in` (2023-02 →) — [crt.sh %.soxo.in](https://crt.sh/?q=%25.soxo.in).
  - Fujifilm: Hyderabad opened 2023-11-19 — [Fujifilm 10875](https://www.fujifilm.com/in/en/news/hq/10875).
- **UAE / Dubai:** `nuradubaidevapi` (2024-07), `nuradubai` (2024-08), `nura-desk-dubai-release-v2` (2024-10 →), `nura-api-dubai-release-20` (2024-10 →), `nura-api-ae-uat`/`nura-desk-ae-uat` (2026-02 →), `uatnura.ae.onedesk.app` (2025-09 →), `qms-dubai.soxo.in` (2023-01 →). Fujifilm's 2025-09-30 release mentions an existing UAE centre plus a new Dubai location in Jumeirah — [Fujifilm 12811](https://www.fujifilm.com/in/en/news/hq/12811).
- **PURA (Abu Dhabi, SSMC / PureHealth):** `pura-api-dubai-release`, `pura-desk-dubai` (2025-04-16 →). PURA opened 2025-01-31 — [Fujifilm 11888](https://www.fujifilm.com/my/en/news/hq/11888).
- **Mongolia:** `nura-api-mongolia-release-20`/`-staging` (2024-11 →), `nura-desk-mongolia-staging`/`-test` (2024-11 →), `nura-api-mongolia-testprod` and `nura-desk-mn` (2025-03), `nura-api-mongolia-global-release` (2025-04 → 06), `nura-api-mn-uat`/`-mn-qa` (2025-07/08 →), `feedback-api-mn-dev` (2026-01). Ulaanbaatar was among the four NURA sites by Nov 2023 — [Fujifilm 10875](https://www.fujifilm.com/in/en/news/hq/10875).
- **Vietnam:** `han1uat` (2024-04-23 →), `han1staging` (2024-06 →), `nuravietnam1`/`2`/`wp1`/`wp2` (2024-05 →), `nuravietnam` (2024-06 →), `hanoi-dev`/`hanoi-staging` (2024-08 →), `nura-desk-vietnam-staging` (2025-01 →), `nura-vietnam-global-staging` (2025-01 →), `nura-api-vnm-global-release`/`nura-desk-vnm` (2025-04 → 06), `nura-api-hanoi-dev` (2025-06), `nura-api-vn-uat`/`-vn-qa` (2025-07/08 →). Also `nura-website-vn-qa`/`-staging`/`-uat.soxo.in` (2025-08 →). Fujifilm: Hanoi opened July 2024, and Ho Chi Minh City was due to open 2025-11-03, operated by Vietnam Japan Health Technology JSC (VJH) — [Fujifilm 13076](https://www.fujifilm.com/in/en/news/hq/13076).
- **Thailand:** `nura-api-th-uat`, `nura-desk-th-uat`, `uatnura.th` (2025-08 →), `nurath-staging` (2025-12 →), `nura-api-th-uat-develop` and `nura-payment-th` (2025-12-31 →), `nura-desk-th-develop`, `nura-th-payment`, `nurath-payment-api`, `feedback-api-dev-th` (2026-01 →), `feedback-api-th` (2026-01 →), `th-nims` (2025-10 →). Fujifilm: Bangkok centre under direct Fujifilm operation, planned for FY2025 — [Fujifilm 13076](https://www.fujifilm.com/in/en/news/hq/13076).
- **South Africa:** `nura-api-south-africa`, `nura-desk-south-africa-test` (2025-03-30 →), `nurasa` (2025-04 →). Fujifilm announced the Cape Town centre (V&A Waterfront, with The InUversal Group) on 2025-09-30 — [Fujifilm 12811](https://www.fujifilm.com/in/en/news/hq/12811).
- **Philippines:** `nura-api-ph-uat`, `nura-desk-ph-uat` (2026-02-17 →). Fujifilm announced a Manila centre (direct operation) on 2025-10-30 — [Fujifilm 13076](https://www.fujifilm.com/in/en/news/hq/13076).
- **Uzbekistan:** `nura-api-uzb-test`, `uzb.onedesk.app` (2025-03-08 →). No public Fujifilm announcement of an Uzbekistan NURA was found.
- **Iraq (`iq`):** `nura-api-iq-uat`, `nura-desk-iq-uat` (2026-07-04 →), `feedback-dev-iq-api` (2026-07-06). No public announcement was found.
- **Sri Lanka (`lk`):** `nura-api-lk-uat`, `nura-desk-lk-uat` (2026-08-06). No public announcement was found.
- **Network size:** A search snippet states "As of August 2026, there are 13 centres worldwide with six in India, also in Mongolia, Vietnam, Thailand, Dubai and South Africa". This comes from a search summary of NURA and Fujifilm pages and was not opened — [nura.in/know-more-about-nura (snippet)](https://nura.in/know-more-about-nura/)

### Inferences
- **Inferred:** OneDesk is deployed as **separate single-country instances**, each with its own API, staff desk, payment gateway service and feedback service. The likely reasons are data residency, country-specific payment gateways and localisation; the i18n library ships en/ar/de translations, with other languages possibly loaded per deployment. The `dbPtr` parameter in SOXO's reporting library supports a multi-database design.
- **Inferred:** "global-release" and "global-staging" hostnames for Mongolia and Vietnam (2025-01 → 06) suggest a 2025 move toward a common "global" NURA codebase, with each country configured from it.
- **Inferred:** `dkhdxbone`, `dxb1uat` and the Dubai QMS (2023) point to DKH-run or DKH-supported Dubai operations predating Fujifilm's UAE announcements.
- **Inferred:** The CT dates show SOXO standing up country environments 3–8 months before public openings (Hanoi UAT April 2024 vs. July 2024 opening; South Africa March 2025 vs. September 2025 announcement). The Iraq and Sri Lanka UAT environments (July–August 2026) and Uzbekistan (2025) may therefore indicate unannounced expansion or pilots. This is unconfirmed.
- **Inferred:** Mongolia's operation through a local partner and Vietnam's through VJH (HCMC) do not appear to change the vendor: SOXO-hosted NURA instances exist for both countries.

### Gaps
- No Malaysia (`my`) host was found, though Kuala Lumpur was announced. It may use a wildcard certificate or a different domain.
- Hosting regions (in-country or not), the cloud provider for each country, and compliance arrangements (Vietnam Decree 13/2023, Thailand PDPA, UAE ADHICS/DoH) are not publicly documented.
- Whether local operators (VJH in Vietnam, InUversal in South Africa, PureHealth for PURA) license OneDesk directly or receive it through Fujifilm or FUJIFILM DKH is unknown.

---

## Q7. Is Kameda Infologics' Yasasii (HIS/RIS/LIS) used at any NURA centre?

### Takeaway
No evidence was found. Kameda Infologics' public client list and site content do not mention NURA, PURA, FUJIFILM DKH, Dr. Kutty's or Matria. NURA, PURA and DKH hostnames all point to SOXO's own OneDesk/NURA Desk stack. The lead is **not supported**. A Yasasii or Synapse-Yasasii RIS role inside the radiology layer at some site cannot be strictly excluded from public data.

### Cited Findings
- **Confirmed:** Kameda Infologics sells YASASII HIS/EMR, a RIS (sold as "FUJIFILM YASASII-RIS" / "Synapse-Yasasii RIS" with Fujifilm), LIS, blood bank, telehealth and related products. It has a Fujifilm partnership and offices in India, Japan, UAE, KSA, USA, Malaysia and the UK — [kamedainfologics.net](https://kamedainfologics.net/); [search summary of Kameda RIS pages](https://www.kamedainfologics.net/ris)
- **Confirmed:** The Kameda client list includes KIMS Hospital Group (India/GCC), Danat Al Emarat (Abu Dhabi), KAUST, KIMS Oman/Qatar/Bahrain/Dubai/Sun City (Al-Jubail), Dubai Police, Matheny, Dr. Solaiman Fakeeh Executive Clinics (Jeddah), Almoosa Hospital, Dr. Chatora/Baines Intercare (Zimbabwe), MVA Clinic (Eswatini) and CNC Mauritania. **No NURA, PURA, Fujifilm health-screening, DKH or Matria entry appears** — [kamedainfologics.net/clients](https://kamedainfologics.net/clients)
- **Negative search result (no source to cite):** Web searches on 2026-10-04 combining "Yasasii" with "NURA", "Dr. Kutty", "DKH" or "health screening" returned nothing relevant. The only results were unrelated "Kutty" doctors, Matria Hospital's Wikipedia page, and Fujifilm's NURA Global Innovation Center release ([Fujifilm 11974](https://www.fujifilm.com/in/en/news/hq/11974)), which names no Kameda or Yasasii product.
- **Confirmed:** Hostnames for NURA's staff system (`nura-desk-*`, `nura-api-*`), PURA (`pura-desk-dubai`) and DKH (`dkhone`, `dkherp`, `qmsdkh`, `dkh-pacs`) are all on SOXO's onedesk.app domain — [crt.sh %.onedesk.app](https://crt.sh/?q=%25.onedesk.app)

### Inferences
- **Inferred:** Because NURA's front-desk, workflow, EMR, billing and reporting layer is SOXO's in-house platform, Yasasii HIS is very unlikely to be NURA's primary system. Fujifilm India's selling of Yasasii-RIS with Synapse to hospitals such as KIMS appears to be a separate channel.
- **Inferred:** At PURA, PureHealth or SSMC may run their own enterprise systems for the wider hospital, but the PURA screening workflow appears to run on SOXO's stack (CT hostnames plus the LinkedIn SSMC go-live snippet).

### Gaps
- Kameda case-study pages were not fully reviewed. No press release or LinkedIn post linking Kameda to NURA was found, but private deployments would not necessarily be public.
- Whether NURA uses any third-party RIS (Yasasii-RIS or SYNAPSE RIS) for radiologist worklists and reporting, as opposed to OneDesk's `finalreport` module, remains unknown.
