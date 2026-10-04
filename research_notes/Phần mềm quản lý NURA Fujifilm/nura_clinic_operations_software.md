# NURA (Fujifilm) – Clinic Operations / Front-Office & Workflow Software Layer

Research date: 4 Oct 2026. Scope: the non-imaging management layer at NURA centers (booking, registration, patient flow, billing/payments, packages, reports, CRM, HIS/LIS/EMR). Imaging PACS/AI is covered by another researcher and appears here only where it touches the management layer.

Method note: Beyond press and media sources, I inspected **publicly served** web pages and client-side JavaScript of NURA's own websites and patient portals (nura.in, nura.in/portal, nurathailand.com, pwa-uat.nurathailand.com, nura.vn, nura.mn, nura.one) and the public app-store metadata (Google Play page, Apple iTunes lookup API) on 4 Oct 2026. Findings from that inspection are labelled **[observed in public site code, 2026-10-04]**. I deliberately left out the keys and tokens that appear in the client bundles. Everything labelled "Inference" is my own reasoning, not a stated fact.

---

## Q1. What system runs booking, registration, patient flow and billing? Is it named? Is it Fujifilm-proprietary, a Fujifilm Japan product, or third-party/local?

### Takeaway
No Fujifilm press release, IR document or interview names NURA's front-office system. The public evidence does point to one system: a **custom platform built by SOXO, a Kozhikode (Kerala) software company that calls itself the "IT Division of Nura Centres"**. Its backend runs under the domain **onedesk.app** ("OneDesk", apparently SOXO's platform name). The same system handles slot booking, pre-registration, payments (Razorpay in India), coupons, corporate tagging, questionnaires, reports and loyalty rewards. It is not a Japanese Fujifilm 健診 (health-checkup) product, and none of the usual Indian third-party HIS/CRM vendors show up. Inside the center, Fujifilm says patient flow runs on QR-coded wristbands, with a dedicated staff member (one-to-one concierge) guiding each guest.

### Cited Findings
**Who built the system: SOXO, the "IT Division" of NURA, located at NURA's own Kerala center**
- The Android app "Nura – Ai Health Screening" (package `com.nura`) is published by developer **FUJIFILM DKH LLP**. The listed developer contact is email ashique@nura.in, phone **+91 78992 05111**, and address **"Nura Global Innovation Center, Arapuzha Road, Pantheerankave PO, Kozhikode, Kerala 673019"**. Support contact: hello@nura.in, +91 7310494949. 10K+ downloads; page shows "Updated on Sep 29, 2026" — [Google Play listing](https://play.google.com/store/apps/details?id=com.nura&hl=en)
- SOXO's own website lists the same phone number, **"78 99 205111"**, with email hello@soxo.in. It describes its healthcare offerings as "Electronic Health Records. Equipment Interfacing. Scheduling and canceling appointments. Inventory management. Accounting and billing. Tracking patient details and medical reports." — [soxo.in](https://soxo.in/)
- The Kerala IT park listing for SOXO says: founded **March 2021** as a "product development company to build tech products in healthcare and for enterprise businesses"; based in Sahya Building, Cyberpark Kozhikode; MD/CEO **Dr Mohammed Kasim**. Its footer address is "3rd Floor, Sahya, Cyberpark, 167/A, Kozhikode – 673014" — [Cyberpark listing](https://cyberparks.in/listings/soxo/); [soxo.in services page](https://soxo.in/services2.html)
- A LinkedIn profile headline (seen in search results; LinkedIn blocked a direct fetch) reads: "Ratnakaran KA – **SOXO LLP., Cyberpark, Kozhikode – IT Division of Nura Centres : by Fujifilm-Japan and DKH-India**" — [LinkedIn (search-result title)](https://www.linkedin.com/in/ratnan-indian/)
- Company registries list related entities **"SOXO TECHNOLOGIES LLP"** and **"SOXO TECH LLP"**. I could not open their registry details (HTTP 403) — [Tofler](https://www.tofler.in/soxo-technologies-llp/company/ABB-2977); [Crediwatch](https://www.crediwatch.com/profile/soxo-tech-llp)
- The website package catalogue is pulled live from a WordPress REST endpoint hosted on SOXO's domain (`uatnura.soxo.in/wp-json/wp/v2/packages`). The portal matches the WordPress field `acf.product_id` to its backend `packageId` **[observed in public site code, 2026-10-04]** — [nura.in patient portal](https://nura.in/portal/auth/login)

**Platform architecture (India) [observed in public site code, 2026-10-04]**
- The "Book Screening" buttons on package pages go to the patient portal, for example `nura.in/portal/health-screening-packages/appointment-slot?package=25&firm=1/bengaluru`. The `firm=` parameter selects the branch — [nura.in package page](https://nura.in/package/well-women-screening-bangalore/)
- The portal at `nura.in/portal` is a React single-page app (Vite/rolldown build, **Ant Design**, **Firebase**, a PDF viewer, **Cloudflare Turnstile**). It loads **Razorpay** checkout (`checkout.razorpay.com/v1/checkout.js`) and has a "RAZOR" payment mode constant. The bundle declares app version "1.0.16" — [nura.in/portal](https://nura.in/portal/auth/login)
- The main API is at **`https://nuraapi.onedesk.app/prod`** (nginx). A secondary API is at `https://portal.nura-in.com/prod`, and the payment page is a separate React app at `https://payment.nura.in/payment` — [nura.in/portal](https://nura.in/portal/auth/login)
- Report files come from **`https://blrffdkhportal.nura-in.com/FileFSLink`**. That host answers as **Microsoft-IIS/10.0, X-Powered-By: ASP.NET**. The portal code recognises Windows drive and UNC file paths and rewrites the city codes `del|bom|hyd|ccj` to `BLR` — [nura.in/portal](https://nura.in/portal/auth/login)
- API endpoint names show what the front office covers: `/bookings/branches`, `/bookings/available-slots`, slot hold, `/bookings/confirm-booking`, `/bookings/reschedule-booking`, `/bookings/pre-registration`, `/bookings/registration`, `/bookings/initiate-payment-v2`, `/bookings/proceed-payment`, `/bookings/payment-status`, `/bookings/validate-coupon`, `/bookings/gift`, `/bookings/customer-list` (corporate list), `/bookings/homekit-address`, `/bookings/screening-video-completion`, `/questionnaire/get-questions`, `/questionnaire/record-answers`, `/reports/load-reports`, `/reports/load-report`, `/files/read-file-pdf`, `/reports/trigger-report-mail`, `/reward/rewards-lists`, `/reward/redemption`, `/reward-transactions/redeem-calc`, `/doctor-appointment/booking-secure-link-details`, `/bookings/switch-account`, `/bookings/migrate-account`, `/branch-master/get-records`, `/item/get-all-items`, `/settingslist/load-all-settings`. Login is by mobile or email OTP — [nura.in/portal](https://nura.in/portal/auth/login)
- Internal field names include `opNo` (outpatient number), `firmId`, `masptr`, a `db_ptr` request header, and `corporate_pointer` — [nura.in/portal](https://nura.in/portal/auth/login); [nura.vn](https://nura.vn/)

**The same platform is reused in other countries [observed in public site code, 2026-10-04]**
- **Thailand:** a pre-production PWA at `pwa-uat.nurathailand.com` uses the same codebase. Its page title is still "India's First Ai Powered Health Screening Center", and it still loads Razorpay. It calls `api.nurathailand.com/prod` (same `/bookings/...` endpoint schema), uses a payment service at **`nura-th-payment.onedesk.app`** and a report server `file-report.nurathailand.com` (Node/Express), and pulls its package catalogue from `uatnura.soxo.in` — [pwa-uat.nurathailand.com](https://pwa-uat.nurathailand.com/)
- **Vietnam:** the nura.vn site (Next.js) calls **`api.nura.vn/prod`** with the same endpoint naming (`/branch-master/get-records`, `/auth/web-login`, `/bookings/generate-otp`, `db_ptr` header). It has user pages for appointments, bookings, reports and rewards, plus `/prereg/...` pre-registration — [nura.vn](https://nura.vn/)
- The Vietnam bundle also carries Mongolian payment strings: "Use **QPay** to book appointment" and instructions to register with **PayOn**, with a link to **Tavan Bogd Finance** branches. This suggests one front-end codebase serves both Vietnam and Mongolia — [nura.vn](https://nura.vn/)

**In-center patient flow / queue management**
- From Gurugram and Mumbai onward (2022), Fujifilm introduced "QRコード付きリストバンドでそれぞれの受診者の検査進捗を管理し各検査の待ち時間を短縮するフロー" (a flow that tracks each examinee's test progress with a **QR-coded wristband** to cut waiting time at each test). It also introduced a way for examinees to see results on their smartphone at any time. *Secondary source summarising Fujifilm's July 2022 Japanese release; I could not open the original* — [AIsmiley, 2022](https://aismiley.co.jp/ai_news/fuji-film-india-nura/)
- JETRO's site visit (Calicut, 11 Feb 2026) describes the station order. A staff member accompanies each guest one-to-one ("担当スタッフがマンツーマンで対応"). Sequence: change clothes → urine sample, blood draw, BP/weight/height → CT → ECG → oral exam → vision/fundus. Women add mammography and cervical screening. Next comes AI-avatar feedback, then the doctor consultation, all within 120 minutes — [JETRO, 26 Mar 2026](https://www.jetro.go.jp/biz/areareports/2026/ac822db52064c952.html)
- Toyo Keizai (2026) also describes concierges guiding each visitor one-to-one, treated "as guests rather than patients" ("ゲストとしてマンツーマンで案内する") — [Toyo Keizai](https://toyokeizai.net/articles/-/930724)
- NURA's corporate FAQ says the 120-minute visit "includes registration, vitals, lab tests, all AI-assisted imaging, and an in-person doctor consultation", with "zero waiting and zero confusion" — [nura.in/corporates](https://nura.in/corporates/)

**What Fujifilm says publicly**
- Fujifilm releases describe only "medical IT systems based on AI technology designed to support doctors". They name no booking, HIS or billing product — [Fujifilm, Global Innovation Center, 24 Dec 2024](https://www.fujifilm.com/jp/en/news/hq/11974); [BioSpectrum Asia, 21 Jul 2022](https://www.biospectrumasia.com/news/49/20737/fujifilm-unveils-two-new-nura-health-centres-for-cancer-screening-in-india.html); [Fujifilm, Ulaanbaatar, Jul 2024](https://www.fujifilm.com/jp/en/news/hq/11626)
- In Japan, Fujifilm Medical Co. develops and installs 健診システム (health-checkup systems) for domestic customers. *Search-snippet level only; the job page has since returned 404* — [hrmos job posting (snippet)](https://hrmos.co/pages/fms/jobs/2247260463838150656)

### Inferences
- **Classification:** the front office and workflow layer is **built by a NURA-affiliated local developer (SOXO, Kozhikode)**, not by Fujifilm Japan and not by an off-the-shelf third-party vendor. The evidence:
  - the app developer's phone equals SOXO's phone;
  - the developer address is NURA's own Calicut center;
  - a SOXO employee calls SOXO the "IT Division of Nura Centres";
  - SOXO hosts NURA's package-catalogue backend.
  
  Within the JV, this makes the platform effectively proprietary to Fujifilm DKH. SOXO was founded in March 2021, one month after the first NURA center opened, and Dr. Kutty's Healthcare is based in Kerala. Both facts suggest SOXO is a captive or affiliated tech arm of the DKH side, but no source states the ownership.
- "OneDesk" (onedesk.app) is most likely SOXO's name for its multi-tenant platform. Hints: the `db_ptr` header, `firmId`, separate country API hosts and a separate Thai payment host on onedesk.app. The naming (`branch-master`, `item`, `opNo`, `settingslist`) reads like an Indian HIS/ERP data model.
- The IIS/ASP.NET report server in Bangalore, together with Windows/UNC file paths, points to an older on-premises .NET HIS/report server. The newer React/Node API layer appears to sit on top of it.
- In-center routing between stations is most likely done in the same SOXO system, with QR wristbands scanned at each station. Fujifilm's 2022 description of QR wristbands managing "test progress" fits a station-status queue, but no source names the queue software.
- For Japanese Fujifilm 健診 products, I found no evidence of export to NURA. The overseas NURA stack looks locally developed.

### Gaps
- No official name for the HIS/front-office product. "OneDesk" is inferred from a domain name only.
- SOXO's ownership (DKH-owned, JV-owned or independent vendor) is not confirmed. Registry details were blocked.
- No screenshots or documentation of the staff-facing (reception/billing) console. Everything here comes from the patient-facing side.
- I could not open the original Fujifilm 2022 Japanese release on QR wristbands; only a secondary summary was available.
- Vendor names for in-center queue displays or kiosks, if any, were not found.

---

## Q2. Which laboratory system (LIS) or lab partner handles blood and urine tests? Which HIS/EMR?

### Takeaway
NURA runs **its own in-house lab at each center**, and that lab is what makes same-day (≤120 min) results possible. I found no public source naming an LIS product or an external reference-lab partner. SOXO advertises "Equipment Interfacing" and EHR, so lab analyzer interfacing and the EMR are most likely part of the same SOXO-built system (inference).

### Cited Findings
- "採取した血液・尿・便潜血を測定するラボは、各施設内に整備されている。そのため、生化学検査の結果も含めた結果フィードバックが基本的に120分以内で可能だ" (the lab that measures blood, urine and fecal occult blood is set up inside each facility, so feedback including biochemistry results is basically possible within 120 minutes) — [JETRO, 26 Mar 2026](https://www.jetro.go.jp/biz/areareports/2026/ac822db52064c952.html)
- The stool sample container is handed over the day before and brought in on the day ("前日に採便容器を渡され当日に持参") — [JETRO, 26 Mar 2026](https://www.jetro.go.jp/biz/areareports/2026/ac822db52064c952.html). The portal has a matching **"Home Kit Delivery"** feature ("We'll send a simple home kit for sample collection…") with a `/bookings/homekit-address` endpoint **[observed in public site code, 2026-10-04]** — [nura.in/portal](https://nura.in/portal/auth/login)
- SOXO's listed healthcare offerings include "Electronic Health Records" and "Equipment Interfacing", alongside appointments, billing, inventory and medical-report tracking — [soxo.in](https://soxo.in/)
- In Vietnam, the partner T-Matsuoka Medical Center runs the facility, and the menu adds tests not offered in India (ultrasound, ENT) — [JETRO, 26 Mar 2026](https://www.jetro.go.jp/biz/areareports/2026/ac822db52064c952.html)

### Inferences
- "Equipment interfacing" in a SOXO-type HIS normally means analyzer↔LIS interfaces (ASTM/HL7). Together with in-house labs, this suggests SOXO's system also acts as the LIS. I found no vendor LIS name (for example CrelioHealth/LiveHealth, Labcare or Orchard) in any NURA web asset I checked.
- In partner-operated countries (Vietnam with T-Matsuoka, Mongolia with Tavan Bogd), the partner may run its own HIS/LIS. However, Vietnam's public booking API follows the same SOXO/OneDesk schema, so at least the patient-facing booking and reports layer is shared.

### Gaps
- No LIS product name, analyzer vendor or NABL/accreditation detail was found.
- No named EMR/HIS vendor at any center. Whether partner countries use local HIS systems is unknown.

---

## Q3. How are reports generated and delivered? Is there a patient app or portal, and who built it?

### Takeaway
Results are delivered the **same day**: first AI-avatar feedback on a monitor, then a doctor consultation. The guest leaves with a **printed ~50-page "Your Annual Health Report"** (A/B/C/D grading) and image analysis sheets. The same data goes out **by email** and appears in the **NURA app or web portal, including images**. Both the iOS and Android apps are published by **FUJIFILM DKH LLP** with SOXO-linked contact details, and the web portal is SOXO's React app.

### Cited Findings
- At the end of screening, results are first given by an **AI avatar on a monitor** ("モニターに映るAIのアバターによる受診結果のフィードバック"), followed by the doctor's detailed explanation and recommendations — [JETRO, 26 Mar 2026](https://www.jetro.go.jp/biz/areareports/2026/ac822db52064c952.html)
- Results are graded A/B/C/D, and the guest receives on the spot a ~50-page booklet, "Your Annual Health Report", plus image analysis documents with doctor comments. The data is also emailed, and results including images can be viewed in the NURA smartphone app — [JETRO, 26 Mar 2026](https://www.jetro.go.jp/biz/areareports/2026/ac822db52064c952.html)
- "a comprehensive digital health report is provided instantly at the end of their 120-minute visit" — [nura.in/corporates](https://nura.in/corporates/)
- Doctors review the actual diagnostic images with each patient — [Fujifilm, 24 Dec 2024](https://www.fujifilm.com/jp/en/news/hq/11974)
- India encourages sharing reports with the patient's "home doctor", and NURA actively builds relationships with home doctors — [JETRO, 26 Mar 2026](https://www.jetro.go.jp/biz/areareports/2026/ac822db52064c952.html)
- **Android app:** "Nura – Ai Health Screening", package `com.nura`, developer FUJIFILM DKH LLP, 10K+ downloads, updated 29 Sep 2026. Stated features: "Book and manage health screening appointments; Access and view your health screening reports; Track your screening history and records…". The Data-safety section declares "No data collected" and "No data shared with third parties" — [Google Play](https://play.google.com/store/apps/details?id=com.nura&hl=en)
- **iOS app:** "Nura App", seller FUJIFILM DKH LLP, bundle `com.nura.ai`, first released 19 Jan 2023, version 1.0.53 released 30 Sep 2026, iOS 14+, Health & Fitness category — [Apple iTunes lookup](https://itunes.apple.com/lookup?id=6444829208&country=in); [App Store](https://apps.apple.com/in/app/nura-app/id6444829208)
- **Web portal** features [observed in public site code, 2026-10-04]:
  - report list and PDF viewer (`/reports/load-reports`, `/files/read-file-pdf`);
  - an "email me my report" action (`/reports/trigger-report-mail`, message "Report sent to your email");
  - image files accepted as JPG/PNG/**DICOM**/TIFF;
  - a WhatsApp help link (`wa.me/…`).
  
  Source: [nura.in/portal](https://nura.in/portal/auth/login)
- Fujifilm (2022) mentioned that examinees can check results on their smartphone at any time and that **blockchain-based data integration** across the three Indian centers was planned. *Secondary source* — [AIsmiley, 2022](https://aismiley.co.jp/ai_news/fuji-film-india-nura/)
- Data platform: under a METI/JETRO "Global South" demonstration project (Dec 2024 – Nov 2027), Fujifilm, working with **FUJIFILM DKH LLP and FUJIFILM DKH HEALTHCARE INVESTMENT L.L.C**, will set up NURA centers in Singapore, Malaysia, Thailand, the Philippines and elsewhere and build a "医療データ利活用基盤" (medical data utilization platform) — [JETRO project sheet, 2024](https://www.jetro.go.jp/ext_images/services/grobal_south/kekka-gs1/pdf/12.pdf)
- Anonymised image data is used, with consent, to train AI — [Fujifilm, 24 Dec 2024](https://www.fujifilm.com/jp/en/news/hq/11974)

### Inferences
- The app, portal, PDF reports and email delivery all appear to sit on SOXO's platform (shared API host). The Bangalore IIS "FileFSLink" server, with its city-code rewriting, suggests report PDFs and images from all Indian centers sit in a central Bangalore file store.
- The AI avatar feedback is most likely a Fujifilm-side component, since Fujifilm's Imaging Informatics Lab was present at the Calicut visit. Who built it is not stated.
- The "No data collected" Play declaration looks inconsistent with an app that handles health reports. This is a compliance observation, not a confirmed fact about data practices.

### Gaps
- No source names who built the AI avatar or the report-generation engine (template/PDF engine).
- No WhatsApp Business API report delivery was confirmed. Only a WhatsApp help link was observed.
- Version histories and release notes are generic ("New updates available").

---

## Q4. What does the website booking flow reveal about the underlying platform (booking engines, payment gateways, CRM), by country?

### Takeaway
Marketing sites are on commodity CMSs: WordPress + Elementor in India and Thailand, Next.js in Vietnam, the Mongolian **Siro.mn** platform in Mongolia, and Framer for the global hub nura.one. Every "Book" action goes into the custom SOXO/OneDesk booking API. Payment gateways observed: **Razorpay** (India), **QPay/PayOn** (Mongolia, from shared code). CRM signals are thin: **Zoho SalesIQ** live chat in Thailand, WordPress **Forminator** forms in India, a **Google Apps Script** lead form in Vietnam, and an **Azure-hosted chatbot** across sites. No Salesforce, LeadSquared or HubSpot was found.

### Cited Findings [observed in public site code, 2026-10-04]
- **Global:** `nura.one` ("NURA Global") is built with Framer (published 29 Sep 2026) and links to nura.in, nurathailand.com, nura.vn and nura.mn — [nura.one](https://nura.one/)
- **India (nura.in):**
  - WordPress + Elementor, with **Forminator** forms (by WPMU DEV/Incsub) for callback and lead forms;
  - Google Tag Manager;
  - app badges for Google Play and the App Store;
  - a chatbot iframe served from `app-ff-nurachatdata-prod0.azurewebsites.net`;
  - booking CTAs pointing to `nura.in/portal/...appointment-slot?package=…&firm=…`;
  - Razorpay checkout in the portal.
  
  Source: [nura.in](https://nura.in/); [nura.in/portal](https://nura.in/portal/auth/login)
- **Thailand (nurathailand.com):** WordPress + Elementor + Yoast, with a **Zoho SalesIQ** widget (`salesiq.zohopublic.in`), LINE (`lin.ee`), TikTok, a chatbot at `app-nurachat-ver2-th-prod0.azurewebsites.net`, and a link to the PWA (UAT) on the SOXO/OneDesk stack — [nurathailand.com](https://nurathailand.com/)
- **Vietnam (nura.vn):**
  - Next.js front end with the API at `api.nura.vn/prod`;
  - contact form posts to a **Google Apps Script** web-app URL;
  - contact links for Zalo, Facebook Messenger and WhatsApp;
  - the same Azure chatbot (`app-ff-nurachatdata-prod0`);
  - the footer cites the partner T-Matsuoka and the MoIT registration (online.gov.vn).
  
  Source: [nura.vn](https://nura.vn/)
- **Mongolia (nura.mn):** built on the **Siro.mn** website platform (assets on cdn.siro.mn / static-storage.siro.mn). It has a "Цаг захиалах / Book appointment" link to `/appointment-slot` and a Login button — [nura.mn](https://nura.mn/)
- QPay and PayOn (Tavan Bogd Finance) payment options appear in the shared front-end code shipped on nura.vn — [nura.vn](https://nura.vn/)
- Operators: Mongolia is operated by the **Tavan Bogd Group**, with FUJIFILM DKH LLP providing support — [Fujifilm, Jul 2024](https://www.fujifilm.com/jp/en/news/hq/11626). Vietnam runs on a partner model with T-Matsuoka, where Fujifilm supplies know-how and the partner handles operations and marketing — [JETRO, 26 Mar 2026](https://www.jetro.go.jp/biz/areareports/2026/ac822db52064c952.html)

### Inferences
- The "ff" in the Azure chatbot hostname very likely stands for Fujifilm. A Fujifilm-hosted conversational layer seems to be shared across countries, separate from the SOXO booking backend.
- India appears to have no dedicated marketing CRM visible on the public site. Lead capture runs through WordPress forms and the corporate callback form, and booking history lives in the SOXO platform.
- Thailand uses Zoho SalesIQ, so at least that market uses Zoho for chat-based lead handling. Whether Zoho CRM sits behind it is unknown.

### Gaps
- I could not reach `nura-in.fujifilm.com` or `discovernura.com` (TLS errors or connection resets), so they were not inspected.
- The Mongolia booking API host was not identified; the Siro.mn page only exposed CMS assets.
- The payment gateway for Thailand's live (non-UAT) flow is unknown. The UAT build still carries Razorpay from India.
- Sites for Dubai and South Africa were not found or inspected.

---

## Q5. What do job postings and LinkedIn profiles reveal about the software stack?

### Takeaway
Public job evidence is sparse. The strongest signal is **SOXO's identity as NURA's IT division**, plus Indeed listings for "Software Support – Soxo" roles in Calicut. I found no NURA job posting naming a commercial HIS, RIS or LIS vendor.

### Cited Findings
- A LinkedIn headline (via search result): "SOXO LLP., Cyberpark, Kozhikode – IT Division of Nura Centres : by Fujifilm-Japan and DKH-India" — [LinkedIn (search-result title)](https://www.linkedin.com/in/ratnan-indian/)
- Indeed India has a results page titled "17 Software Support, Soxo Jobs and Vacancies in Calicut, Kerala – 29 September 2026". Content not retrievable (HTTP 403) — [Indeed (title only)](https://in.indeed.com/q-software-support-,-soxo-l-calicut,-kerala-jobs.html)
- SOXO's careers page has no specific openings (template content) — [soxo.in careers](https://soxo.in/career.html)
- Fujifilm staff named in the JETRO interviews include a member of the **Fujifilm Imaging Informatics Lab** (大坪隆信, Calicut) and the **NURA Head of Operations** (Prashob T C) — [JETRO, 26 Mar 2026](https://www.jetro.go.jp/biz/areareports/2026/ac822db52064c952.html)

### Inferences
- The tech stack seen in public code is React with Ant Design, Next.js, Node/Express (Thai report server), nginx, Firebase, Cloudflare Turnstile, Azure App Service (chatbot), and IIS/ASP.NET (Bangalore report server). That points to SOXO hiring for JavaScript and .NET skills rather than administering a vendor HIS.

### Gaps
- I found no LinkedIn, Naukri or Indeed posting text for NURA centers mentioning HIS/RIS/LIS/PACS product names. LinkedIn and Indeed blocked automated fetches.
- I did not find JobStreet or Vietnamese/Mongolian postings for NURA IT roles.

---

## Q6. Corporate / B2B features: corporate packages, bulk scheduling, aggregated reports

### Takeaway
Corporate business matters: 40% of Hanoi's customers are B2B, India runs a corporate wellness team, and NURA Express provides mobile on-site corporate screening. The booking platform supports **corporate tagging at booking** (pick your company from a corporate master, a "referred by corporate" flag, firm or branch IDs), plus coupons and gift bookings. I found **no public evidence of an employer dashboard or aggregated corporate health report**. NURA states that results go only to the individual employee.

### Cited Findings
- Hanoi: about 40% of customers are B2B (corporate checkups) — [JETRO, 26 Mar 2026](https://www.jetro.go.jp/biz/areareports/2026/ac822db52064c952.html)
- India: **NURA Express** brings CT-based cancer screening and lifestyle-disease checks on a mobile unit to employees at partner companies' offices and factories outside cities, with plans to extend it to municipal screening — [JETRO, 26 Mar 2026](https://www.jetro.go.jp/biz/areareports/2026/ac822db52064c952.html); [Fujifilm India news – NURA Express](https://www.fujifilm.com/in/en/news/hq/12176)
- India's corporate page offers a "Request a callback" form; the corporate wellness team responds within one business day with a tailored proposal. Packages "can be added to your existing benefits or offered as standalone." On privacy: "All screening results are shared securely and directly with the individual employee. Health records remain entirely confidential between the employee and the NURA medical team." — [nura.in/corporates](https://nura.in/corporates/)
- In the booking-state code: `selectedCorporate`, `referredByCorporate`, `firmId`, `coupon_code`, `remark`, a corporate list from `/bookings/customer-list` (fields such as `corporate`, `corporate_pointer`), plus `/bookings/gift` and `/bookings/validate-coupon` **[observed in public site code, 2026-10-04]** — [nura.in/portal](https://nura.in/portal/auth/login)
- A secure-link flow exists (`/bookings/secure-link/verify`, `/secure-link/create-user-account`, `/doctor-appointment/booking-secure-link-details`) **[observed in public site code, 2026-10-04]** — [nura.in/portal](https://nura.in/portal/auth/login)
- Bengaluru: about 30% of visitors are repeat customers, and family-referral promotions are used. A loyalty/rewards module also appears in the portal (`/reward/rewards-lists`, `/reward/redemption`) — [JETRO, 26 Mar 2026](https://www.jetro.go.jp/biz/areareports/2026/ac822db52064c952.html); [nura.in/portal](https://nura.in/portal/auth/login)

### Inferences
- Corporate employees probably book through the same portal: they pick their employer from the corporate master, or follow a pre-generated **secure link** sent by HR or NURA. That would tie the booking to corporate pricing and billing. The secure-link and pre-registration endpoints fit bulk-invited bookings, but this is not documented.
- Aggregated or anonymised corporate reporting, if it exists, would be offline or analyst-produced. The public privacy stance argues against identifiable employer access.

### Gaps
- No documentation of bulk scheduling tools, corporate invoicing or credit billing, or employer-facing aggregated dashboards.
- How NURA Express (mobile) registration and reporting syncs with the center system is undocumented.

---

## Q7. Country and operating-model overview (context for the software layer)

### Takeaway
As of August 2026 there are 13 NURA centers: 6 in India, plus Mongolia, Vietnam, Thailand, Dubai and South Africa. Some are run directly by FUJIFILM DKH (India) and others by local partners (Mongolia: Tavan Bogd; Vietnam: T-Matsuoka). The software evidence shows a **single SOXO/OneDesk patient-facing platform reused across India, Vietnam and Thailand (UAT), and probably Mongolia**, while marketing sites, chat and payment adapters vary by country.

### Cited Findings
- 82,000+ screenings in India and 150,000+ globally; 13 centers worldwide (6 in India: Bengaluru Feb 2021, Gurugram Jul 2022, Mumbai Jan 2023, Hyderabad Nov 2023, Calicut Dec 2024, Chennai May 2026; others in Mongolia, Vietnam, Thailand, Dubai and South Africa); target of 100 locations by FY2030 — [nura.in "Know more"](https://nura.in/know-more-about-nura/)
- 12 centers as of Jan 2026 — [Toyo Keizai](https://toyokeizai.net/articles/-/930724)
- In Dec 2024 there were 8 centers (India 4, Mongolia 2, Vietnam 1) and 77,000+ users. The Calicut Global Innovation Center serves as training hub, **centralised remote interpretation center** for images from Indian NURA centers, and AI development hub — [Fujifilm, 24 Dec 2024](https://www.fujifilm.com/jp/en/news/hq/11974)
- FUJIFILM DKH LLP is a JV with Dr. Kutty's Healthcare, set up in 2019. Hanoi opened Jul 2024 and Ho Chi Minh City Nov 2025 under the T-Matsuoka partner model — [JETRO, 26 Mar 2026](https://www.jetro.go.jp/biz/areareports/2026/ac822db52064c952.html)

### Inferences
- Because Calicut hosts both the training/remote-reading hub and (per the Play listing address) the app developer contact, Kozhikode looks like NURA's operational IT center. SOXO is in Kozhikode's Cyberpark as well.
- The likely way NURA scales to new countries is to deploy a new country instance of the SOXO/OneDesk backend (`api.<country-domain>/prod`) and plug in local payment gateways. Thailand's UAT is the clearest example.

### Gaps
- No software evidence was gathered for the Dubai and South Africa (Cape Town) centers.
- Whether partner operators (Tavan Bogd, T-Matsuoka) also run SOXO's staff-side HIS, or only the patient-facing layer, is unconfirmed.
