# Shalom Wellness Network

## What this is

Single-page application (SPA) brochure site for Kemunto Achira's wellness education practice, **Shalom Wellness Network**. Sells the Feel Great Protocol (Unicity affiliate) and collects leads via three forms.

**Live site:** https://shalomwellnessnetwork.netlify.app/ (will move to `shalomwellnessnetwork.com` once Kemunto's domain + Netlify are set up)

**Tagline:** Wholeness for You. Hope for Generations.

## Tech stack

- **Plain HTML/CSS/JS** in a single `index.html` file. No build step. No framework. No npm.
- 6 "pages" implemented as `.page` divs inside the same document, switched via `navigate()` JS function with History API support (browser back/forward works).
- All assets (videos, photos, PDF) sit in the repo root.
- **Hosted on Netlify**, deployed via either:
  - `git push` → Netlify auto-deploys (preferred, once GitHub repo is wired)
  - `netlify deploy --prod --dir .` from this folder (fallback)
  - Drag-and-drop of this folder onto Netlify dashboard (manual fallback)

## Ownership map

| Asset | Owner | Notes |
|---|---|---|
| Source code / GitHub repo | Chelsea | Temporary — will transfer to Kemunto at full handoff |
| Netlify account + site | Kemunto (`mamamboga4life@gmail.com`) | Chelsea is added as Team Owner so her CLI deploys still work |
| Domain registration (Porkbun) | Kemunto | Bought in her name with her payment |
| Form submissions inbox | Kemunto (`mamamboga4life@gmail.com`) | Routes through FormSubmit.co |
| Unicity affiliate (Feel Great Protocol referral) | Kemunto / Josephine | All "Join the Protocol" buttons → `ufeelgreat.com/c/Josephine`. Do NOT change unless Kemunto confirms a new referral code is live in Unicity. |
| Juice Plus+ affiliate | Kemunto | `us.juiceplus.com/?partnerAlias=josephine6` |
| Unicity Shop | Kemunto | `shop2.unicity.com/usa/en/products?referralCode=Josephine` |

## The update workflow (the magic)

```
Chelsea edits index.html locally in Claude Code
  → git push to chelseajobe41/shalom-wellness-network (or whatever the repo is named)
  → Kemunto's Netlify is watching that repo
  → Netlify auto-pulls + deploys (~30 seconds)
  → live at shalomwellnessnetwork.com
```

Chelsea never logs into Kemunto's Netlify. Kemunto never touches the GitHub repo. The public GitHub repo is the bridge.

## What would break the bridge

- Making the repo **private without reconnecting** Netlify with new credentials (private repos need fresh OAuth)
- Disconnecting the Netlify ↔ GitHub link in Netlify's dashboard
- Kemunto's Netlify account closing (free tier, very unlikely)
- Repo deletion (don't)

## File map — what to edit for what

| Want to change... | File |
|---|---|
| Any text on any page | `index.html` (search for the exact phrase, edit in place) |
| Hero video on home | Replace `kemunto-sunset-hero.mp4` (1280×720 H.264, no audio, ≤5MB ideal) |
| Hero video on About / story videos | `kemunto-story.mp4` (her personal story, 720×1280 portrait) |
| Kemunto's portrait | `kemunto.jpg` (Personal Message section on About) |
| Before/after photos | `[client]-before-after.jpg` (Beverly, Johnny, De Landa, Esther, Natacha, Kemunto) |
| Free guide PDF | `why-am-i-always-tired.pdf` (lead magnet) |
| SEO meta / structured data | Top of `index.html` head — title, description, JSON-LD `@graph` block |
| Brand context for AI crawlers | `llms.txt` |
| Search engine crawl rules | `robots.txt` |
| Sitemap | `sitemap.xml` |

## Brand voice / hard rules (from Chelsea's memory)

- **NO em dashes** in user-facing copy. Use commas, periods, or rewrite. (Rule applies sitewide.)
- **NO eyebrow labels** ban does NOT apply here — Kemunto's brand approved the amber "eyebrows" (e.g., "WHOLENESS FOR YOU · HOPE FOR GENERATIONS"). Keep them.
- **NO community / network language** — site is built around individual transformation and the Feel Great Protocol funnel, not a "join our community" pitch.
- **NO clinical-practice language** — Kemunto is a Wellness Nurse Educator, not a licensed clinician offering treatment. No "telehealth practice," no "patients," no "diagnose."
- **NO hormone-treatment language** — she can talk about insulin resistance and lifestyle but is not qualified to assess/treat hormones.
- **NO "Women 40+" framing exclusively** — site features Johnny, Pastor Isaac, Jonathan. Use inclusive language ("the whole family", "women and men").
- **15-minute call**, not 30. (Updated Jun 2026 per Kemunto.)

## Things to never break (bugs we hit + how to avoid)

| Bug | Fix |
|---|---|
| Hero video had audio playing on autoplay despite `muted` attribute | The source `.mp4` was re-encoded with `-an` flag (strip audio entirely). Keep audio stripped on any hero replacement: `ffmpeg -i in.mp4 -an -movflags +faststart out.mp4` |
| All 4 stock background videos downloaded on initial page hit (141MB mobile payload) | Background videos on inactive SPA pages have `preload="none"`. `manageVideos()` in JS promotes preload to `auto` + calls `.load()` only when the user navigates to that page. Don't remove this. |
| Empty `<div id="toast">` left a visible plum pill at the bottom of every page | Removed entirely. Don't reintroduce a toast without giving it explicit `display: none` when empty. |
| Browser back button skipped past the entire SPA | History API integration in `navigate()` pushes a new state on each page change + listens for popstate. Don't tear it out. |
| Lighthouse render-blocking from Google Fonts (~2s) | Fonts load async via `rel="preload" as="style" onload="this.rel='stylesheet'"` pattern. Keep that. |
| Quiz answers weren't emailing Kemunto until user opted in | Quiz now has a mandatory name+email gate AFTER question 10 that posts to FormSubmit. Every submission emails her. Don't break this gate. |

## Forms — how they email Kemunto

All three forms (Contact, Quiz Gate, Free Guide) submit to **FormSubmit.co AJAX endpoint** at `https://formsubmit.co/ajax/mamamboga4life@gmail.com`. No backend code, no API keys. FormSubmit needs a one-time activation: first form submission triggers a verification email; Kemunto clicks Activate once and every submission afterward delivers to her Gmail.

| Form | Trigger | Subject she'll see |
|---|---|---|
| Contact | Visitor fills Contact page form | "New consultation request · Shalom Wellness Network" |
| Quiz Gate | Visitor finishes 10-question quiz + enters name/email | "New quiz submission · Shalom Wellness Network" |
| Quiz "Book My 15-Min Call" | After result, visitor clicks the call button | "⏰ Quiz visitor wants a 15-min call · Shalom Wellness Network" |
| Free Guide | Visitor enters name/email on Home or Quiz page lead magnet | "New free-guide signup · Shalom Wellness Network" |

If a form fails (FormSubmit down, visitor offline), the JS falls back to surfacing her email address `mamamboga4life@gmail.com` so they can reach her directly.

## Local preview

```bash
# From this folder
python3 -m http.server 4488
# Then open http://localhost:4488
```

Or use the Claude Code preview if launched from this directory.

## Deploying

**Preferred (once GitHub bridge is wired):**
```bash
git add .
git commit -m "What you changed"
git push origin main
# Netlify auto-deploys in ~30 seconds
```

**Fallback (direct push, no GitHub):**
```bash
netlify deploy --prod --dir .
```

**Manual fallback (if CLI is broken or you've handed off):**
Drag this entire folder onto Netlify's Deploys panel for the site.

## Client-handling notes

- **Kemunto's email:** `mamamboga4life@gmail.com` — only contact channel
- **Communication style:** plain text, short paragraphs. She's not technical. Skip jargon.
- **Kemunto's name:** her formal/legal name is Josephine Kemunto Achira-Onwonga; she goes by Kemunto in all consumer-facing content. Affiliate URLs use "Josephine" because that's her Unicity account name.
- **Tomorrow morning meeting (Jun 2026):** walk her through SETUP.md, EMAIL-SETUP.md, and the Netlify dashboard. Goal: she leaves understanding how to log in, what form emails look like, who to call for changes.
- **Post-launch support:** unresolved. Adam hasn't formally introduced the new owner yet. Kemunto flagged this; treat it as Chelsea's call to handle directly with her.

## Outstanding items (not blockers)

1. **Unicity affiliate URL** — currently `c/Josephine`. If Kemunto switches to a `c/Kemunto` referral, update 12 instances in `index.html`. Don't touch until she confirms the new code is live in her Unicity account.
2. **Custom email** like `kemunto@shalomwellnessnetwork.com` — Google Workspace would cost $6/mo. Currently using `mamamboga4life@gmail.com`. Defer until she asks.
3. **Newsletter platform** — site uses FormSubmit for lead capture but doesn't push to a newsletter tool. If she wants ongoing email nurture, Mailchimp/ConvertKit integration would be a future add.

---

*Built by Chelsea Jobe. Wholeness for you. Hope for generations.*
