# NextTierAthlete

Recruiting websites, video & photography capture, and highlight reels for youth athletes (ages 12–18).

This project builds and manages three things for each athlete client: (1) a personal recruiting website (stats, highlight film, academics, coach contacts, schedule) that can be sent directly to college coaches, (2) on-site video and photography capture of games and practices, and (3) edited highlight reels — a short recruiting-cut reel plus regularly refreshed clips — so the website's film section never goes stale.

The **real, live company site is https://nexttierathlete.com** — a separate,
self-hosted deployment, not this repo. [`site/index.html`](site/index.html)
here is a standalone pricing-page mockup used to visualize Section 6; it
isn't deployed anywhere and doesn't need to be. See
[`docs/live-site-setup.md`](docs/live-site-setup.md) for how the real site
is actually built, hosted, and routed.

## Background

Originally scoped under the working name "Prospect Path" and later
rebranded to NextTierAthlete. Flagship client: Maxwell Preasha, live at
`maxwellpreasha.nexttierathlete.com` (migrated off `preasha-home.com` on
2026-09-12).

## Contents

| File | Description |
|---|---|
| [`docs/live-site-setup.md`](docs/live-site-setup.md) | How the real, live site is actually hosted, routed, and deployed — current URLs and known gaps |
| [`site/index.html`](site/index.html) | A standalone pricing-page mockup, not the live site |
| [`docs/business-plan.md`](docs/business-plan.md) | Full business plan — market, pricing, operations, financials, roadmap |
| [`docs/template-case-study.md`](docs/template-case-study.md) | Case study and reusable site-build spec based on Maxwell's recruiting site |
| [`docs/business-plan-agent-prompt.md`](docs/business-plan-agent-prompt.md) | The original agent prompt used to generate the business plan |
| [`docs/conversation.md`](docs/conversation.md) | Planning conversation history, including the Prospect Path → NextTierAthlete rebrand |
| [`docs/site-intake-form.md`](docs/site-intake-form.md) | Minimal client intake form to kick off a new athlete's site build |

## Pricing (current model — see `docs/business-plan.md` Section 6)

Scoped to three deliverables only: website builds, video & photography capture, and highlight reels. No social media posting/management or NIL package.

| Package | Live site name | One-Time Website Build | Monthly Retainer | What's Included |
|---|---|---|---|---|
| Website Only | — | $299 (template) / $499 (custom domain) | — | Website build only, no retainer |
| Starter | Rookie | $299 | $99/mo | Website + 1 game capture session/mo + 1 highlight clip/mo |
| Growth | Varsity | $399 | $199/mo | Website (custom domain) + 2 capture sessions/mo + monthly clips + quarterly full highlight reel |
| All-Access | Elite | $499 | $349/mo | Website (custom domain) + up to 4 capture sessions/mo + a full highlight reel every month + priority turnaround |

These numbers are **live now** on the real site (nexttierathlete.com) under
the "Live site name" column above — Content Capture (the à la carte tier
below) is also live as **$75–$225/session, no retainer**.

À la carte capture and standalone highlight reels are also available — see `docs/business-plan.md` Section 6.

A separate, unvalidated reference pricing model for a future self-serve *software* product (vs. the founder-fulfilled service above) is sketched in `docs/business-plan.md` Section 13, per the plan's Phase 3 roadmap.

A sourced competitive pricing benchmark (NCSA, SportsRecruits, Prospect Pages, sports videographers) is in `docs/business-plan.md` Section 14 — pricing sits at or below market in nearly every category.

## Status

**Live**, not just planning — the company homepage and four athlete
subdomains are up on `nexttierathlete.com` as of 2026-09-12 (see
`docs/live-site-setup.md`). This repo's business plan and its validation
priorities (`docs/business-plan.md` Section 12, Appendix D) still apply
going forward — pricing and messaging are live, but the plan's pilot/
validation steps haven't been separately marked complete.
