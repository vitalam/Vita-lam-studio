# vitalam.org — Developer Build Specification (v6)
*Prepared by: project management · For: implementing developer · July 2026*
**v9 ADDENDUM — modular builder (supersedes v8 item 2):**
The pricing configurator is now a MatterUs-style modular system rendered from a JS config (`CFG` in index.html): each block 01/02/02B/03/04/05/06 expands into component checkboxes (e.g. 02B: extra gateways, inventory, shipping, manufacturers hub, supplier management, coupons). Rules: **04 requires 03** (checking 04 auto-checks 03 and pulses it; unchecking 03 unchecks 04). 04B is removed as a block — inside 04 there is an API KEY choose-one pair (BYOK = free / managed via OpenRouter) and, for managed only, an AI-model choose-one trio (標準 +HK$780/月 · 進階 +HK$1,480/月 · 頂配 +HK$2,280/月). All selections accumulate in a sticky shopping list with live one-off + monthly totals; 「⚡ 產生報價單」 opens a print-ready quotation (quote number VL-YYYYMMDD-HHMM, itemized table, totals, includes/founding/14-day-validity notes); the WhatsApp CTA carries the itemized build. Subscription (06) now includes **4 hrs of changes monthly** and **latest AI model upgrades** for subscribers.

**v8 ADDENDUM (superseded item 2 struck; rest stands):**
1. **Services** — six services, each landing-page card links to its own mini page under `/services/`: 01 web-design · 02 admin-auth · 03 data-integration · 04 ai-integration · 05 visual-editorial · 06 subscription. Nav 服務 is a hover dropdown listing all six. Each mini page: hero (stacked display type), exactly 3 non-repeating "why me" feature cards, includes+price bar, related-work links, CTA back to the builder. IDs on the landing cards stay svc-site/svc-app/svc-data/svc-ai/svc-copy/svc-care (chooser depends on them).
2. **Pricing is a DIY block builder, NOT tiers** (§13 tier table is retired). Checkbox blocks with live totals: 01 網站 HK$28,000 · 02 後台會員 +HK$28,000 · 02B 付款電商 +HK$22,000 · 03 數據 +HK$16,800 · 04 AI +HK$19,800 · 04B 受管 API +HK$780/月 · 05 視覺編采 +HK$8,800 · 06 部署訂閱 HK$1,880/月. CTA composes a WhatsApp message with the selected blocks and totals. Founding offer = first 6 months of Subscription free (worth HK$11,280) + portfolio/testimonial rights, auto-renews, cancel anytime, 2 slots/month.
3. **Display type** — line-height tightened for the slight-overlap look: ZH h1 1.02 / h2 1.06, sizes up to 5.2rem/3.3rem.
4. **Notes tool** — export button label is 「📋 複製評論」.
5. **About** — facts list renamed 履歷; order: founder+fullstack combined first, SFC second, artist/languages third, then MSc (Southampton 2018–19, Merit, Dean's List), BBA (CUHK 2014–18), and three separate cert lines (HKCGI AML/CFT 2025 · HKCGI Sustainability 2025 · WIX Accessibility 2024).

*Read this document top to bottom. Build exactly what it says. Where any doubt exists, the reference implementation `index.html` included in this package is the final authority — open it and copy what it does.*

---

## 0. What you are building

ONE self-contained landing page (`index.html`) plus an `assets/` folder. Single page, long-scroll, twelve sections in a fixed order (§8). Language: Traditional Chinese (Hong Kong) is the DEFAULT; English is a toggle. Dark theme, "Liquid Glass" material. No frameworks. No build step. Vanilla HTML/CSS/JS in one file. Deploy target: Netlify (drag-and-drop).

**Definition of done:** every checklist item in §15 passes.

## 1. File & folder inventory

```
/index.html          ← the entire site (HTML + CSS + JS inline)
/assets/
   iccc.jpg          ← screenshots, see §2 (12 files)
   matterus.jpg
   carboncopy.jpg
   batjik.jpg
   taiji.jpg
   gem.jpg
   humanrights.jpg
   proxy.jpg
   hoho.jpg
   moderndesign.jpg
   codepen.jpg
   handwriting.jpg
   og.png            ← social share image, see §2.2
```
Nothing else. No node_modules, no separate .css/.js files.

## 2. Assets to produce

### 2.1 Project screenshots (12)
Capture each URL in a desktop browser. Viewport exactly **1280×800**. Wait for the page to fully render (some are JS apps — wait ~6 s). Save as JPEG quality ~72, filename EXACTLY as listed (lowercase, no spaces). Do not crop, do not add borders.

| # | Filename | URL |
|---|---|---|
| 1 | `iccc.jpg` | https://iccc.dev |
| 2 | `matterus.jpg` | https://matterus.com.hk |
| 3 | `carboncopy.jpg` | https://carboncopy.one |
| 4 | `batjik.jpg` | https://batjik.com |
| 5 | `taiji.jpg` | https://taiji.game.carboncopy.one |
| 6 | `gem.jpg` | http://gem.portfolio.demo.carboncopy.one |
| 7 | `humanrights.jpg` | https://humanrights.com.hk |
| 8 | `proxy.jpg` | https://proxy.matterus.com.hk |
| 9 | `hoho.jpg` | https://hoho.portfolio.demo.carboncopy.one |
| 10 | `moderndesign.jpg` | http://moderndesign.demo.carboncopy.one |
| 11 | `codepen.jpg` | https://codepen.io/gokucrew/pen/EaxWjaO |
| 12 | `handwriting.jpg` | https://bolt.new/p/66919367 |

Only files 1–4 are currently displayed (flagship cards). Files 5–12 are captured now for future use; store them in `assets/` anyway.

**Fallback behaviour (already implemented — do not remove):** each `<img>` loads `assets/<name>.jpg`; on error it swaps to `https://s0.wordpress.com/mshots/v1/<urlencoded-target>?w=1024`; on second error it hides its container. This means the page works even before screenshots exist. Keep this exact `onerror` chain.

### 2.2 Social image
`og.png`, 1200×630, dark background #050506, gold headline 「贏得客人。不只贏得讚美。」+ VITA LAM wordmark. Referenced by `<meta property="og:image" content="https://vitalam.org/og.png">` — upload to site root.

### 2.3 Brand logos (BLOCKED — waiting on client)
Carbon Copy®, G Entertainment, MatterUs logo files are pending. Placeholder comment `<!-- LOGO-PLACEHOLDERS -->` marks the insertion point in the 更多作品 panel. Do nothing until files arrive.

## 3. Design tokens (copy exactly)

**v7 NOTE — design system replaced.** The Liquid Glass skin is retired. The site now follows the Modern Design language defined in `vitalam-design-playbook.md` (lime `#D9FF3F` on black `#0A0A09`, drafting-grid background, sharp 3–6px corners, hairline borders, hard-offset hover shadows, 【VITA LAM】bracket logo, marquee ticker). The token block below is superseded by the playbook; the reference `index.html` implements the current system.

```css
--bg:#050506;             /* page background */
--ink:#F5F5F7;            /* primary text */
--ink-2:#C9C9CE;          /* secondary text */
--ink-3:#8E8E93;          /* tertiary text */
--accent:#E8B84B;         /* gold — the ONLY accent */
--accent-2:#F6D488;       /* gold gradient end */
--r:28px;                 /* card corner radius */
--max:1120px;             /* content max width */
```
Fonts: Google Fonts `Inter` (400/500/600/700/800) + `Noto Sans TC` (400/500/700/900). Chinese headlines use weight 900, letter-spacing normal. English headlines weight 700–800, letter-spacing −0.02…−0.028em.
WhatsApp green `#22C55E` is used ONLY on WhatsApp buttons. No other colours anywhere.

**Glass material (every card/panel):** background `linear-gradient(135deg,rgba(255,255,255,.09),rgba(255,255,255,.03))`; `backdrop-filter:blur(22px) saturate(1.7)`; border `1px solid rgba(255,255,255,.14)`; inner top highlight `inset 0 1px 0 rgba(255,255,255,.16)`; shadow `0 24px 48px -24px rgba(0,0,0,.6)`; radius `var(--r)`.

**Ambient background:** fixed, z-index −1, three blurred radial orbs — gold top-right, indigo `rgba(88,86,214,.38)` left-middle, violet `rgba(191,90,242,.22)` bottom-right — each `filter:blur(90px)`, animating a slow 36 s drift. Honour `prefers-reduced-motion` (stop animation).

## 4. Language system (critical — get this right)

- Every piece of text exists twice, wrapped in `<span class="zh-only">…</span><span class="en-only">…</span>`.
- Default = Chinese: `<html lang="zh-Hant-HK">`, body WITHOUT class. CSS: `body:not(.lang-en) .en-only{display:none}` / `body.lang-en .zh-only{display:none}`.
- Nav button `#langBtn` shows `EN` by default; on click toggle `body.lang-en`, set `html[lang]` to `en` / `zh-Hant-HK`, and swap the button label to `中文` / `EN`.
- Both languages stay in the DOM (SEO requirement). Never lazy-load a language.

## 5. Iconography

One inline SVG sprite in `<body>` (23 `<symbol>`s, viewBox 0 0 48 48, stroke-only, `stroke-width:2.2`, round caps): `i-brush i-compass i-stack i-phone i-store i-key i-pulse i-eye i-ear i-blueprint i-hammer i-rocket i-shield i-infinity i-cube i-home i-drop i-ink i-spark i-scale i-coin i-stamp i-wa`. Use via `<svg class="ico"><use href="#i-name"/></svg>` inside a `.ico-chip` (56px rounded glass square, gold stroke). Copy the sprite verbatim from the reference file. Do NOT substitute an icon font or emoji.

## 6. Global components

- **Nav:** fixed floating capsule, top 14px, centered, width min(1080px, 100%−28px), glass, radius 999px. Contents left→right: logo `VITA LAM` (LAM in gold) → links 服務 #services · 作品 #work · 流程 #process · 收費 #pricing · FAQ #faq → `#langBtn` → gold-on-white pill CTA 免費 20 分鐘健檢 → #contact. Below 860px width: hide text links, keep logo + langBtn + CTA.
- **Buttons:** `.btn-primary` gold gradient pill; `.btn-glass` glass pill; `.btn-wa` WhatsApp green pill with `i-wa` icon. Hover: lift 2px + glow.
- **WhatsApp float:** fixed bottom-right 20px, 58px green circle, `i-wa` icon, links `https://wa.me/85266033707`, aria-label="WhatsApp". On every viewport.
- **Reveal animation:** elements with `.reveal` fade/slide in on first intersection (threshold .1). JS adds `html.js` class ONLY when IntersectionObserver exists; without JS all content must be visible. Never ship content that is invisible when JS fails.

## 7. Contact data (single source of truth)

- WhatsApp / phone: **+852 6603 3707** → `https://wa.me/85266033707`
- Email: **vita.lam@icloud.com** (mailto link in contact section)
- Form: Netlify Form, `name="enquiry"`, `data-netlify="true"`, honeypot `bot-field`, hidden `form-name` input. Fields: name (text, required) · email (email, required) · project-type (select: 新網站 / 登入・管理後台 / AI 功能 / 急救現有網站 / 長期維護 / 其他) · message (textarea, required). Submit button = primary CTA copy.

## 8. Page skeleton — sections in this EXACT order

| # | Section id | Heading (ZH) | Notes |
|---|---|---|---|
| 1 | hero (`#top`) | 贏得客人。不只贏得讚美。 | centered; sub-line; 2 CTAs (primary + WhatsApp); no-strings note |
| 2 | chooser | 你想做啲乜？三秒搵到你要嘅嘢。 | 4 tiles, see §9 |
| 3 | proof strip | — | one glass bar, 4 items, see §10 |
| 4 | `#ai` | AI 不能做嗎？能。那電話響的時候呢？ | 4 cards (審美/判斷/餘下的80%/問責) + banner 「AI 壓縮的是打字的時間。壓縮不了責任。」 + stack-disclosure line (Bolt.new, Netlify, Supabase) |
| 5 | `#services` | 先講你的問題。再講我的技能。 | 6 cards, grid-3, ids svc-site / svc-app / svc-data / svc-ai / svc-copy / svc-care |
| 6 | `#work` | 我創辦生意。包括我自己的。 | chips + 4 flagship cards (WITH screenshots) + 更多作品 panel (7 rows), see §11 |
| 7 | acumen (no id) | 你坐的那張椅子，我也坐過。 | 3 cards: 前 SFC 持牌代表 / 你的預算是資本 / 合規與認證 |
| 8 | `#process` | 五個步驟。零神秘感。 | 6 cards: 聆聽/藍圖/建造/上線/看守 + gold 不變的原則 card |
| 9 | `#deliverables` | 你會收到什麼？白紙黑字。 | 6 cards, see §12 |
| 10 | `#pricing` | 誠實的價格。真的公開。 | anchor line + 3 price cards + promo note + 3 mini-panels (AI 整合 / 看守 / 附加服務), see §13 |
| 11 | `#about` | AI 之前在創作。之後，依然。 | glass split panel: story + quote + headline demo 「苦盡遍體鱗傷，演出塵世甘來。」 + facts list (§10 order) |
| 12 | `#faq` | 問題，直接回答。 | 8 `<details>` accordions |
| 13 | `#contact` | 二十分鐘。三個建議。零綑綁。 | split panel: pitch + WhatsApp + email / Netlify form |
| 14 | footer | — | © year (JS) · wa.me phone · links to 4 ventures · tagline 親手建造。AI 是工具箱一員。一如承諾。 |

All copy strings (both languages) are in the reference `index.html`. Transcribe verbatim — do not paraphrase, do not "improve", do not translate freshly.

## 9. Chooser behaviour (interaction spec)

Four glass tiles. Click behaviour:

| Tile | data-choose | href | On click |
|---|---|---|---|
| 我要一個網站 | `site` | `#svc-site` | scroll to card, pulse it, filter work grid to `site` |
| 我要登入・後台 | `app` | `#svc-app` | same, filter `app` |
| 我要 AI 功能 | `ai` | `#svc-ai` | same, filter `ai` |
| 先睇作品 | `work` | `#work` | reset filter to `all`, scroll to work |

"Pulse" = restart CSS animation `pulse-ring` (gold box-shadow ring, 1.1s ×2) on the target card.

## 10. Credential ordering (POLICY — do not reorder)

Developer-identity FIRST, finance second, art last. Proof strip items in order: ① 全端開發者 · 大數據・商業分析專業 ② 親手創辦 ICCC® · MatterUs · Carbon Copy® · 沉墨 ③ 前 SFC 持牌代表 · 交易總額達數億港元 ④ AI 前後都在創作的藝術人. About facts list mirrors this order (fullstack → MSc/Dean's List/analytics → founder of four → SFC → HKCGI/accessibility certs → artist/languages).

## 11. Work section data

**Filter chips:** 全部 `all` · 網站 `site` · 應用・後台 `app` · AI `ai`. Clicking toggles `.hide` on every element carrying `data-cat` (both flagship cards and 更多作品 rows). An item matches if its space-separated `data-cat` contains the filter.

**Flagship cards (grid-2), each = icon chip + tag + h3 + SCREENSHOT (`.shot-wrap`) + 3 rows 問題/做了/成績 + external link:**

| Card | data-cat | Screenshot | Link |
|---|---|---|---|
| ICCC® | `app` | assets/iccc.jpg | https://iccc.dev |
| MatterUs | `site` | assets/matterus.jpg | https://matterus.com.hk |
| Carbon Copy® | `site` | assets/carboncopy.jpg | https://carboncopy.one |
| 沉墨 Batjik | `app ai` | assets/batjik.jpg | https://batjik.com |

**更多作品 rows (one line each: name + tag + one-liner + link):**

| Row | data-cat | Link |
|---|---|---|
| 太極 Taiji Game | `ai` | https://taiji.game.carboncopy.one |
| GEM 業務革新 | `site` | http://gem.portfolio.demo.carboncopy.one |
| Modern Design 設計示範 | `site` | http://moderndesign.demo.carboncopy.one |
| humanrights.com.hk 公益 | `site` | https://humanrights.com.hk |
| Proxy by MatterUs 商業頁面 | `site` | https://proxy.matterus.com.hk |
| HOHO 快速作品集 (contains the headline 苦盡遍體鱗傷，演出塵世甘來。) | `site` | https://hoho.portfolio.demo.carboncopy.one |
| 手寫分析 App | `ai app` | https://bolt.new/p/66919367 |
| App 客製化 UI | `app` | https://codepen.io/gokucrew/pen/EaxWjaO |

All external links: `target="_blank" rel="noopener"`.

## 11B. AI Logic Firewall (POLICY — wording is legally gated)

The phrase **AI Logic Firewall（專利申請中）/ (patent pending)** appears in exactly four places: ① svc-ai service card ② ICCC® flagship card 做了 row ③ AI 整合 pricing mini-panel note ④ its own FAQ entry 「植入 AI，會唔會亂講嘢？」. Rules:
- Copy the four strings verbatim from the reference file. Do NOT add the phrase anywhere else (no hero, no proof strip).
- ⚠️ 「專利申請中」may only be displayed while a patent application is actually FILED and pending. If the client says it is not yet filed, replace every instance of 「專利申請中」/"(patent pending)" with 「自研專有技術」/"(proprietary)". Ask; do not guess.
- NEVER describe how the firewall works internally (architecture, rules, prompts). Benefit language only: "the AI only says what you've approved." Pre-filing disclosure of the mechanism can jeopardize the patent.

## 12. Deliverables manifest (six cards, grid-3)

1. 全部源代碼 (i-cube) — complete, readable, no traps, no tethers
2. AI-ready 設計手冊 (i-brush) — colours/type/spacing/component specs; any AI tool or developer can continue the design
3. 模組化架構 (i-stack) — embedded apps always separable from major content
4. 名下帳戶 (i-stamp) — domain/hosting/analytics registered to the client
5. 文檔＋交接教學 (i-blueprint)
6. GOLD card 一個標準 (i-infinity) — 「你唔再需要我，先至係我做得好。」

This section sits AFTER process, BEFORE pricing. It is a policy section — copy must not be softened.

## 13. Pricing data (display EXACTLY these numbers)

**Anchor line first:** 同等範圍，香港代理公司報價 **HK$65,000–588,000**。…「據說這樣很前衛。」

| Card | Badge | List (strikethrough) | Displayed price | Sub-label | USD line |
|---|---|---|---|---|---|
| Launch | 起步之選 (dim) | HK$22,000 | **HK$12,800** | 創始客戶價 | ≈US$1,640 · 原價 ≈US$2,820 |
| Business | 最多人選 (gold, featured) | HK$58,000 | **HK$38,000** | 創始客戶價 | ≈US$4,870 · 原價 ≈US$7,440 |
| Platform | 完整產品 (dim) | — | **由 HK$98,000** | 定範圍後提供固定報價 | ≈US$12,560+ |

Feature bullets per card: transcribe from reference. Launch includes 「網域、部署、SSL・保安標準配備」.

**Promo note:** 每月兩個名額 · 預付 50% · 授權作品集及推薦語 · 原價是真實價格。

**Mini-panel 1 — AI 整合 (gold border):** 訂製整合 由 HK$19,800 · 創始價 HK$11,800 ｜ 受管 API（經 OpenRouter）由 HK$780/月 · 創始 HK$480/月 ｜ 自備 API key 由 HK$21,800 · 創始價 HK$13,800. Note: 月費含用量額度；超額按 OpenRouter 成本加固定手續費，設支出上限；深度整合由 HK$42,800 起。

**Mini-panel 2 — 看守（一個價錢全包）:** **HK$1,880/月** — 寄存・SSL・備份・監測・保安修補・系統更新・每月 2 小時修改・月度報告・真人回應（一個工作天內）。超出 HK$650/hr。隨時取消。 Gold line: 「保安唔係加購項目。係標準配備。」 ⚠️ There is NO security add-on anywhere on the page and NO tiered care plans. Do not add them back.

**Mini-panel 3 — 附加服務:** 網域+DNS HK$500/yr（.hk 由 HK$1,800）· 部署設定 HK$3,500 · 數據整合・儀表板 由 HK$16,800 · 登入模組（加裝）由 HK$28,000 · 時薪 HK$650–850/hr.

## 14. SEO / meta (head block)

- `<title>` Vita Lam｜贏得客人的網站 — 香港全端網站及網頁應用開發・設計
- meta description: ZH-first, mentions 標準網站/整合應用/數據整合/AI 植入/收費公開/永久擁有 (copy from reference)
- canonical `https://vitalam.org/`; og:type/url/title/description/image; twitter card summary_large_image
- JSON-LD `ProfessionalService`: email vita.lam@icloud.com, telephone +852 6603 3707, areaServed Hong Kong/Worldwide, priceRange "HK$12,800 - HK$150,000+"
- Static HTML only — every string server-rendered. NO client-side content injection for copy.

## 15. Acceptance checklist (QA — all must pass)

1. Page loads with Chinese content by default; `html[lang]="zh-Hant-HK"`.
2. EN toggle swaps every visible string; toggling back loses nothing.
3. With JavaScript disabled: all sections and text fully visible (no blank reveals), both languages NOT shown simultaneously is waived — ZH shows (CSS-only default).
4. All 4 chooser tiles work per §9 table; pulse visible; work grid filters correctly per §11 data-cat map.
5. All 12 external project links open in new tabs and are correct per §11.
6. Flagship screenshots render; delete `assets/` locally and confirm the mshots fallback appears; block both and confirm containers hide with no broken-image icon.
7. WhatsApp: hero button, contact button, floating bubble → all `wa.me/85266033707`.
8. Netlify form posts successfully on the deployed site (test one submission).
9. Prices on page match §13 exactly — every digit.
10. No security add-on, no tiered care plans anywhere.
11. Credential order per §10 in both the proof strip and About facts.
12. Mobile 390px: no horizontal scroll; grids collapse to 1 column; nav collapses per §6.
13. Reduced motion: orbs and reveals stop animating.
14. Lighthouse (deployed): Performance ≥ 90, SEO ≥ 95, Accessibility ≥ 90.
15. Console: zero errors on load and after clicking every interactive element once.

## 15B. Review-notes tool (temporary scaffold)

`index.html` contains a review annotation tool fenced by `REVIEW-NOTES-TOOL START/END` comment markers (plus a matching CSS block marked the same way). It adds a 「✎ 筆記 Notes」toggle (bottom-left); in notes mode every section shows a note tab, notes autosave locally, and 「📋 複製 Bolt.new 指示」compiles all notes into a per-section markdown brief (also downloadable as bolt-notes.md). This is a review-phase scaffold for the client: keep it during Bolt.new calibration, DELETE both fenced blocks before final production launch.

## 16. Open items (not blockers)

| Item | Owner | Status |
|---|---|---|
| 12 screenshots per §2.1 | client/developer | pending (sandbox capture blocked by network egress allowlist — capture from any normal browser, or add the domains to the workspace allowlist for automated capture) |
| Brand logo files ×3 | client | pending |
| og.png | designer | pending |
| Testimonials (2–3, named, with results) | client | collect post-launch |
| Bolt.new calibration | client | after this build is accepted |
