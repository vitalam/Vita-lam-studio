# vitalam.org — Website Revamp Strategy
*Vita Lam · July 2026 · companion document: `vitalam-pricing-rationale.md`*

## 1. Objective

Turn vitalam.org from a self-describing developer portfolio into a **customer-side selling machine**: a visitor should grasp Vita's professionalism, find their own path, and see the exact deliverables — all within seconds. Positioning: **premium freelancer, below every agency**, differentiated by verifiable business acumen, artistic taste, radical pricing transparency, and a no-lock-in handover ethic.

## 2. Audience & first impression (the 10-second test)

Every visitor arrives asking four questions: *What do you do? Are you good? Who do you help? Why should I trust you?* The landing page answers all four above the fold: outcome headline (贏得客人。不只贏得讚美。), identity kicker (全端開發者), the chooser (who it's for), and the proof strip (why trust). Credentials are ordered **developer-first**: 全端開發者・大數據/商業分析專業 leads; venture-builder record second; SFC/finance credential third as the differentiator; artist identity fourth as the memorable close.

## 3. Site architecture (v6 — one-pager canonical)

**Revision (client decision, v6):** the multi-page split tested worse than the original one-pager. The canonical build is the single long-scroll landing (skeleton per the v4.1 structure) with in-page anchors; the works/pricing/about subpages are archived and may be reintroduced later during Bolt.new calibration if page-level SEO becomes a priority. The table below is retained for that future option only.

One-pager retired in favour of a small multi-page site — faster landing, page-level SEO targeting, and cleaner mental model. To be calibrated in Bolt.new; all pages share one design system and are self-contained HTML.

| Page | Job | SEO target (ZH-first) |
|---|---|---|
| `index.html` | Efficient landing: hero → chooser → proof → AI objection → services ladder → deliverables manifest → work teaser → contact form | 香港網站開發・網頁應用・AI 整合 |
| `works.html` | Full gallery, **segmented by audience** | 網站開發實例・香港 |
| `pricing.html` | Full pricing + deliverables manifest + process + FAQ | 網站開發收費・香港・價錢 |
| `about.html` | The person: art, credentials, acumen | Vita Lam・全端開發者 |

Landing stays lean: no full gallery, no pricing tables, no FAQ — links out instead. Traditional Chinese (HK) is default; EN toggle on every page; both languages live in the DOM (crawlable).

## 3B. v8 revision — services architecture & DIY pricing

Six services, calibrated names: 01 專業網站設計 (backbone-ready, CMS incl.) · 02 後台・會員系統 · 03 數據整合系統 (ICCC-grade) · 04 AI 整合 (Logic Firewall) · 05 視覺・編采 (incl. the collaborative annotation interface as a sellable specialty) · 06 部署訂閱. Each has a mini page under /services/ with exactly three unique "why me" features; nav has a Services dropdown. Pricing is a DIY block builder (see pricing-rationale §0) with a WhatsApp handoff carrying the selected build. Display type tightened to the Modern Design slight-overlap leading. About facts renamed 履歷 with full academic details.

## 4. Customer flow

1. **Hero** — one outcome sentence, two CTAs (primary + WhatsApp).
2. **Chooser** — 「你想做啲乜？三秒搵到你要嘅嘢。」 Four tiles: 網站 / 登入・後台 / AI 功能 / 先睇作品. Tiles pulse the matching service card; the works tile routes to works.html. Self-segmentation replaces making everyone read everything.
3. **Works page segregation** — three audience lanes, each with its own promise line: 中小企・品牌老闆 (sites that sell: MatterUs, Carbon Copy, GEM, Proxy, HOHO) · 創辦人・產品團隊 (operable products: ICCC, Batjik, handwriting app, CodePen) · 學校・機構・公益 (ideas that land: Taiji game, humanrights.com.hk).
4. **Contact** — one repeated CTA (free 20-minute review, three improvements guaranteed either way), WhatsApp button + floating bubble, Netlify form, email vita.lam@icloud.com.

## 5. Positioning pillars

1. **The AI objection, met head-on** — "Couldn't AI build this? Sure. Then who answers the phone?" Full stack disclosure (Bolt.new, Netlify, Supabase). Sells taste (pre-AI art practice), judgment, the other 80%, accountability. Tagline: *AI 壓縮的是打字的時間。壓縮不了責任。*
2. **Capability ladder** — 標準網站 → 整合式應用（共用入口・分身份登入・一頁後台，如 batjik.com）→ 數據整合・儀表板 → AI 植入; supported by 文案・命名 and 全包看守. Data consolidation is deliberately the rung between apps and AI: "AI is only as smart as your data is tidy."
3. **The deliverables manifest（交付清單）** — the anti-lock-in answer, itemized: all source code (complete, readable, best effort — no traps); **AI-ready design playbook** (colours, type, spacing, component specs — any AI tool or developer can carry the design forward); **modular architecture** (embedded apps always separable from major content — removable/replaceable independently); accounts in the client's name; docs + handover training. Closing standard: 「你唔再需要我，先至係我做得好。」
4. **Security as standard equipment** — never a paid add-on (a liability if sold separately). 「保安唔係加購項目。係標準配備。」
5. **Ownership philosophy** — 一次購買，永久擁有。 No hostage hosting.
6. **AI Logic Firewall（專利申請中）** — the trust layer of the AI service, placed where the fear lives (AI service card, ICCC case, AI pricing panel, dedicated FAQ 「植入 AI，會唔會亂講嘢？」) rather than as a vanity badge. Benefit-level language only — the mechanism is never described publicly pre-filing. Wording is legally gated: "patent pending" only while an application is actually filed; otherwise switch to 「自研專有技術」/proprietary.

## 6. Copy voice

Apple-editorial: precise, punchy, humorous-but-professional. Short sentences. Fragments. One dry joke per section maximum ("Radical, apparently"). Second-person outcomes everywhere except buttons, which use the customer's first person ("預約**我的**免費健檢" — tested +90% clicks). Cantonese-flavoured 書面語 for warmth (係/嘅 in headers and quotes, standard written Chinese in body). Copywriting is itself a sold service — proof shown, not claimed: 苦盡遍體鱗傷，演出塵世甘來。(HOHO headline, displayed in About).

## 7. Design system (v7 — Modern Design language; Liquid Glass retired)

**Revision (client decision, v7):** the site is reskinned to Vita's own Modern Design demo language — authenticity over pastiche. A portfolio in the designer's own system is self-evidence, and the site now doubles as a live sample of the sold「AI-ready 設計手冊」deliverable. Full tokens and rules: `vitalam-design-playbook.md`. Summary: black #0A0A09 + drafting grid, single lime accent #D9FF3F (violet as rare secondary), Noto Sans TC 900 stacked display type with lime key-line, sharp corners + hairline borders, hard-offset hover lifts, marquee ticker, numbered kickers, 【VITA LAM】bracket logo.

*(Superseded description below, kept for history.)*

Hierarchy > Harmony > Consistency. Dark base #050506 with three drifting colour orbs (gold/indigo/violet); every surface is glass (backdrop blur + saturation, specular top edge, 28px radii); floating capsule nav; tight-tracked Inter + Noto Sans TC 900 for Chinese headlines; single gold accent #E8B84B; WhatsApp green reserved for WhatsApp only. Hand-drawn-style inline SVG icon set (23 symbols) — no image files. Scroll-reveal with reduced-motion fallback; content never hidden if JS fails.

## 8. Technical & SEO/SMO checklist

- Static, self-contained HTML per page (the old site was a client-rendered SPA invisible to crawlers — the revamp is itself the case study).
- Unique title/description per page; canonical URLs; JSON-LD ProfessionalService on landing; og: tags on all pages (**og.png 1200×630 still needed** for social sharing/SMO).
- Netlify Forms contact (enable notifications post-deploy); wa.me links; lang toggles `html[lang]` between zh-Hant-HK and en.
- Performance: no JS frameworks, no external images, fonts via Google Fonts only.
- Accessibility: aria-labels on icon buttons, semantic sections, reduced-motion support — backs the Certified Accessibility Developer credential; consider adding a skip-link and visible focus states during Bolt.new calibration.

## 9. Launch checklist

1. Calibrate pages in Bolt.new (keep the design tokens and copy; this package is the reference).
2. Embed real brand logos when files are provided (`LOGO-PLACEHOLDERS` comments mark the spots).
3. Create og.png; replace placeholder reference.
4. Deploy to Netlify; enable form notifications; point vitalam.org DNS.
5. Post-launch: collect 2–3 named, result-bearing client testimonials (biggest missing trust element — interleave them once real).

## 10. Key research findings this strategy rests on

- Client-converting portfolios lead with client outcomes, curate 3–5 case studies, name a process, and repeat one CTA (HubSpot, Hostinger, Flux Academy, Cloudways).
- "You"-language beats "I"-language except on buttons (Copyhackers; ContentVerve +90% test).
- Hidden pricing loses shortlist spots (TrustRadius 2025; Gartner: 61% of buyers don't want to talk to sales first). Anchoring: show agency range first, premium visible, middle tier highlighted.
- Even 2–3 specific testimonials materially de-risk hiring an unknown (Northwestern Spiegel; BrightLocal-class survey data).
