# Live site — current setup (as of 2026-09-12)

This repo's `site/` folder is a **standalone demo/mockup** used to visualize
the pricing in Section 6 — it is not deployed anywhere and doesn't need to
be. The actual live business site is a separate, self-hosted setup,
documented here for reference.

## Live URLs

| Site | URL | Status |
|---|---|---|
| Company homepage | https://nexttierathlete.com | Live |
| Maxwell Preasha | https://maxwellpreasha.nexttierathlete.com | Live, full content |
| Luke Dellwo | https://lukedellwo.nexttierathlete.com | Live, placeholder template content |
| Evan Dellwo | https://evandellwo.nexttierathlete.com | Live, placeholder/stub content |
| Lylian Kirkelie | https://lyliankirkelie.nexttierathlete.com | Live, full content |

All five moved from the original `*.preasha-home.com` domain to
`*.nexttierathlete.com` on 2026-09-12, same subdomain-per-athlete pattern.

## Hosting architecture

- Each site is a separate **static nginx container** (`nginx:alpine`) on a
  home server, one `docker compose` service per athlete/site, source files
  mounted read-only from a `site/` folder.
- Ports in use on the server (`127.0.0.1` only, not exposed directly):
  Maxwell 3100/3110, Luke 3120, Evan 3130, Beckham 3140 (see note below),
  SPM/Athlete Operations 3150, Lylian 3160, company homepage 3170.
- Public routing is **Cloudflare Tunnel**, but split across more than one
  tunnel in the same Cloudflare account:
  - `ubuntu-apps-tunnel` — config-file-managed
    (`/etc/cloudflared/config.yml` on the server), handles the old
    `*.preasha-home.com` hostnames plus unrelated home-server apps
    (Nextcloud, Immich, n8n, Jellyfin, etc.). **Not** used for
    `*.nexttierathlete.com`.
  - A separate tunnel (managed through the Cloudflare Zero Trust dashboard's
    Public Hostname UI, not a local config file) handles
    `*.nexttierathlete.com`. **Gotcha:** there's also an unrelated
    `nextcloud-tunnel` in the same account — adding a hostname there does
    nothing useful. Always add new `nexttierathlete.com` subdomains to
    whichever tunnel already lists `maxwellpreasha.nexttierathlete.com`.
- The company homepage's local source bundle (not in this repo) lives at
  `C:\Users\marcu\Documents\Agents\nexttierathlete-company-site-bundle\` —
  `site/index.html`, `site/styles.css`, `site/img/`. A content-only change
  is a single `scp` re-upload of the changed file(s), no restart needed. A
  fresh deploy needs `mkdir` + `scp -r` + `chmod -R 755` (scp creates
  directories as mode 700, which blocks nginx) + `docker compose up -d`.

## What's actually live on the company homepage

- Hero section with a real game-film still (Kansas-game highlight cut cover
  frame) as the background, scrimmed for legibility, credited as real
  footage rather than stock photography.
- Roster grid linking to all four athlete subdomains above.
- Pricing — matches this repo's Section 6 numbers under different tier
  names: **Rookie** = Starter ($299 + $99/mo), **Varsity** = Growth ($399 +
  $199/mo), **Elite** = All-Access ($499 + $349/mo), **Content Capture** =
  à la carte ($75–$225/session, no retainer).
- A "How it works" process graphic (raw footage → edit → finished cut →
  posted, across Instagram/TikTok/YouTube/X/Facebook/LinkedIn).
- Contact routed to **preashamv@nexttierathlete.com** (Cloudflare Email
  Routing → Gmail, plus Gmail "send mail as" configured for outgoing).

## Known gaps

- Luke's and Evan's own subdomains are live but not filled in — Luke shows
  an unedited placeholder template (bracket fields still visible), Evan
  shows a near-empty stub. Real copy exists and just hasn't been pasted in.
- **"Beckham" (port 3140) is not a confirmed client.** A site container and
  an SPM database record exist for that name (full name found in server
  config: Beckham Scribner), but there's no guardian relationship, consent,
  or client record establishing an actual business relationship. Excluded
  from the company homepage roster on that basis — don't add him without
  separately confirming the relationship is real.
- Content cadence per pricing tier isn't finalized (pricing/scope are
  locked; posting frequency isn't yet mapped to each tier specifically).

## Relationship to this repo

This repo is documentation and business-planning only — the pricing
rationale in `docs/business-plan.md` (Sections 6 and 14) is the source
those live numbers came from, and this file is where the actual deployed
state gets recorded so the two don't drift apart silently. The `site/`
folder here and its GitHub Pages workflow remain an independent,
undeployed mockup — no changes needed there to keep this repo useful as a
record.
