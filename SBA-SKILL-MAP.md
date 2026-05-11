# SBA Skill Relevance Map

Which skills in this fork to use as-is, which to translate, which to skip.

For a Scholar Basketball Academy youth basketball context. Upstream framework assumes SaaS/ecomm.

---

## 🟢 Customized in-fork (read addendum first)

These five skills have a `## SBA Addendum (Youth Basketball Academy)` section appended to their `SKILL.md`. Read the upstream content + the addendum together.

- `page-cro` — translates SaaS funnel CRO to SBA's trial-booking, camp-booking, and article-to-trial funnels
- `copywriting` — voice rules, headline patterns (italic-emphasis on one word), parent-facing vocabulary
- `seo-audit` — Singapore SEO realities, local-pack priorities, schema markup priorities
- `ad-creative` — Meta/TikTok/Xiaohongshu, MOE-calendar seasonality, Singapore creative anchors
- `customer-research` — dual-persona (parent + kid), Singapore parent JTBD framework

## 🟡 Use as-is (academy fits upstream cleanly)

These skills can be used as written. The `.agents/product-marketing-context.md` (i.e. SBA-DATA.md content) provides the SBA framing.

- `content-strategy`
- `social-content`
- `video`
- `image`
- `marketing-ideas`
- `marketing-psychology`
- `ab-test-setup`
- `analytics-tracking`
- `schema-markup`
- `popup-cro`
- `form-cro`
- `referral-program`
- `community-marketing`
- `launch-strategy`
- `copy-editing`
- `paid-ads`
- `ai-seo`
- `site-architecture`
- `lead-magnets`

## 🟠 Translate mentally before use

These skills carry SaaS/ecomm assumptions in their framework. SBA-DATA.md context plus mental translation is enough — no in-file addendum.

- `product-marketing-context` — the master skill; SBA-DATA.md is the pre-filled output
- `programmatic-seo` — useful in moderation; Singapore long-tail volumes are small
- `competitor-profiling` — substitute Singapore academies (SG Basketball, Titans, Greatness, Newton Show)
- `competitor-alternatives` — substitute school CCA, public-court coaching, other sports
- `pricing-strategy` — translate "MRR / tiers" → term-based fees + camp pricing + DSA premium
- `email-sequence` — translate "B2B nurture" → parent welcome / trial follow-up / term-end renewal
- `churn-prevention` — treat as "retention"; signal from Mindbody attendance + term non-renewal

## 🔴 Mostly irrelevant for SBA (skip unless edge case)

These skills are written for B2B SaaS or ecomm patterns that don't apply to a B2C service academy.

- `revops` — B2B revenue operations
- `sales-enablement` — B2B sales team enablement; SBA has no sales team
- `cold-email` — parents don't get B2B cold-emailed
- `free-tool-strategy` — SBA doesn't ship free tools as marketing
- `paywall-upgrade-cro` — no paywall product
- `signup-flow-cro` — SaaS account signup, not trial booking
- `onboarding-cro` — SaaS product onboarding, not basketball-program first-session
- `aso-audit` — no SBA mobile app to optimize
- `directory-submissions` — vendor directories (Product Hunt, G2, Capterra); for parenting directories (KiasuParents, HoneyKids, SassyMama) use `community-marketing` or `paid-ads`
- `co-marketing` — B2B partnership marketing; SBA partnerships are venue/school-level, not co-marketing

---

## Reading order for any SBA marketing task

1. Read `.agents/product-marketing-context.md` (the copied SBA-DATA.md)
2. Identify which skill applies — check this map
3. If 🟢: read the upstream `SKILL.md` AND the SBA Addendum at the bottom
4. If 🟡: read upstream `SKILL.md` as-is
5. If 🟠: read upstream `SKILL.md`, then mentally translate per this map's notes
6. If 🔴: skip; or, if you think there's an edge case, surface it to Kevin before proceeding
