# BOLT-INSTRUCTIONS — read me first, before touching any file

You are working on a FINISHED production website — G Studio (1069.com.hk; brand renamed from Vita Lam, though 林瀚海/Vita Lam remains the designer's personal name). Your job is to host,
preview, and apply small requested changes — NOT to rebuild, refactor, reformat,
"clean up", or redesign anything.

## What this project is
- `index.html` — the entire landing page (HTML + CSS + JS inline, self-contained)
- `services/*.html` — six service mini pages sharing the same inline design system
- `assets/` — screenshot images (12 planned; page works without them via fallback)
- `vitalam-design-playbook.md` — the design law. Follow it for anything new.

## Hard rules — breaking any of these is a failed task
1. NEVER regenerate a whole file to make a small change. Edit surgically.
2. The bilingual system is sacred: every string exists as
   `<span class="zh-only">…</span><span class="en-only">…</span>`; `zh-Hant-HK`
   is default; `#langBtn` toggles `body.lang-en`. Never remove either language.
3. `pricing.html` is a FIXED, static, TWO-TIER price list — no builder-algorithm,
   no CFG, no formula. Every service shows a STANDARD price (struck) and the
   ELIGIBLE −70% price (pay 30%, `cut(n)=round(n*0.3/10)*10`). `data-p` on each
   `.qbox` is the STANDARD number; the quote sums both tiers. −70% applies to A/B/C
   for four proof-gated groups: 初創(BR/statements) · 低利潤或零利潤(last tax filing)
   · NGO(official doc) · 支持社會權益企業(mission note). Standard prices:
   A 網站核心 $12,800 (+進階SEO $2,200, 網域包 $2,200, 加頁 $1,680/頁 via qty stepper,
   線上AI $4,280, 登入/預約/會員 $9,300, 舊網站接管 = 以上7折); B 後台系統 我哋整$12,800／
   非$19,300, 全訂製 $29,000起, 電商 我哋整$17,600／非$24,000, 訂製購物車+Stripe scoped,
   數據儀表板 $26,000, AI整合+防火牆 $40,000, Stripe default + payment marks; C 品牌視覺
   $12,800–28,800, 文案 $9,300–22,600 (deploy incl. if our site). SiteCare+ is a FLAT
   prepaid add-on for ALL clients (NOT discounted): 1yr $3,000 / 2yr $5,000, member
   revision $140/hr, attach at launch or ≤60 days — and includes free bookkeeping /
   preliminary accounting for young cos WITHOUT audited accounts (framed "experienced
   finance pro, not a licensed accountant/auditor, not a statutory-audit/tax-advice
   substitute"). Free with EVERY plan: 商業策略顧問 · 法律/商業文件協助 · 商業政策同行審視
   (peer/standard-doc help, "not formal legal/financial/investment advice"). NO monthly
   fees anywhere. Change a price by editing the `data-p` / displayed number directly.
   DISPLAY RULE: the −70% eligible price is the MAIN (lime) number everywhere
   (teaser, pricing rows, service price bars); the standard price appears small,
   struck through, labelled 標準. pricing.html also carries: a 30-second
   eligibility quick-check (#eligcheck — 4 questions; eligible → WhatsApp reserve;
   otherwise → Netlify form `eligibility-review`), and every live page carries a
   fixed announcement bar (quota scarcity, links to #eligcheck; keep an actual
   monthly quota so the claim stays true). The Start-up Mentor Programme is
   REMOVED — do not reintroduce it.
4. The REVIEW-NOTES-TOOL review scaffold was REMOVED at launch (2026-07-26) from
   index.html and all 6 service pages. Do not reintroduce it — no `#noteBar`,
   `.note-panel`, `#noteToast`, 「筆記 Notes」 button or 「複製評論」 export.
5. Wording locks: 「AI Logic Firewall（專利申請中）」 on the landing page appears
   in exactly 4 places — do not add it elsewhere or explain its mechanism.
   No security add-on, no care tiers (SiteCare+ is ONE plan with security
   included). No founding offer, no monthly fees. The OLD algorithmic /
   open-pricing model is RETIRED: do NOT reintroduce 開放定價 / 公允下限 /
   行情 / 0.5×floor / weekly-benchmark / TVP-hours-anchor framing anywhere.
   `pricing-methodology.html` and `pricing-benchmark.html` still exist in the
   repo but are UNLINKED (kept for reference only) — never link to them.
   Prices are FIXED and stated directly; every price claim across index /
   services / pricing must match the numbers on `pricing.html`.
6. Design tokens (lime #D9FF3F on #0A0A09, grid background, sharp corners,
   hairline borders, hard-offset hover) come from vitalam-design-playbook.md.
   No new colours, no soft shadows, no rounded pills, no icon fonts.
7. Screenshots use a 3-step fallback (local file → s0.wordpress.com/mshots →
   hide). Keep the exact `onerror` chain.
8. Contact facts: WhatsApp wa.me/85269798969 (+852 6979 8969) · vita.lam@icloud.com ·
   Netlify forms `name="enquiry"` and `name="eligibility-review"`, both with honeypot. Never change these.
9. Content must be visible without JavaScript. (The pricing page is now a
   static price list, so this holds there too — no builder to degrade.)
10. Keep every file self-contained. No frameworks, no build step, no new
    dependencies, no separate .css/.js files.

## How changes will be requested
The owner sends change briefs listing sections by name (and often a CSS
selector) with an instruction; everything unlisted stays unchanged. Apply
exactly that; nothing more. (The in-page notes tool that used to generate these
briefs was removed at launch.)

## After every round of changes
Report: which files changed, their old vs new byte sizes, and one line per
change. If any file shrank significantly without an explicit deletion request,
you removed something — restore it.
