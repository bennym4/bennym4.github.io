# Bowls Hornby Website — Project Context

This file is read automatically at the start of every Claude Code session.
It replaces the need to re-explain project history in chat.

## What this is
A static website (plain HTML/CSS/JS, no framework) for Bowls Hornby, a
lawn bowls club in Hornby, Christchurch, NZ. Hosted free on GitHub Pages.

## Repos
- **Live site**: `bennym4/bennym4.github.io` → serves `bowlshornby.org.nz`
  Cut back to a two-page site (Home + How to Join). This is the repo that
  is published — treat every change here as going straight to the public.
- **Draft site**: `bennym4/bh-preview-m4` → the full nine-page site, kept
  intact as the working draft. Renamed from an obvious name for privacy —
  do not rename it back to anything with "bowls" or "hornby" in it, and
  do not link to it from the live site.

**The two repos are deliberately out of step.** The draft holds the full
site; the live site holds the trimmed public version. Do not "sync" them
or copy the draft's extra pages across without being asked.

## Workflow
1. Make changes in the **draft repo** first (`bh-preview-m4`)
2. Get sign-off (from committee or self)
3. Copy across to the **live repo** (`bennym4.github.io`) only the pages
   that belong on the trimmed public site
4. Always confirm with the site owner before pushing to the LIVE repo —
   draft repo changes are lower stakes and can be pushed more freely

## Site structure (live repo)
2 pages, sharing one stylesheet:
- `index.html` — Home. **No nav bar, on purpose** — the header is the
  brand only. Sections: hero, Life at the Club (photos), New Players,
  Find Us. Two buttons link to `join.html`.
- `join.html` — How to Join. Nav trimmed to a **single Home link**; keep
  it that way. Sections: hero, Three Steps, membership-fees note.
- `styles.css` — shared design system, both pages import this
- `CNAME` — `bowlshornby.org.nz`
- `club-green.jpg`, `club-deck.jpg` — real club photos, in the repo root
  (not in an `images/` folder), shown on the Home page
- `README.md`, `CLAUDE.md` — housekeeping, not part of the site

**No other pages exist here.** `about.html`, `news.html`, `members.html`,
`contact.html`, `tournaments.html`, `hire.html` and `links.html` were all
removed. Never link to them from the live site — the links would 404.
Anything that needs a contact route should use the `tel:` or `mailto:`
links already on the pages.

## Design system (do not deviate without asking)
- Deep turf green `#1E4630` — header/footer
- Mid green `#3F6B4A` — accents
- Warm parchment `#F2EFE6` — page background
- Clubhouse maroon `#8A2E35` — buttons/CTAs
- Brass gold `#C99A2E` — dividers, highlights
- Fonts: Fraunces (headings), Public Sans (body), Space Mono (small labels)
- Signature motif: thin horizontal "rink lines" (Google Fonts imported in styles.css)

## Live data — Google Sheets
Not on the live site. The draws/notices Google Sheets feed lived in
`news.html`, which no longer exists here. The feed and its CSV URLs are
still in the draft repo — do not rebuild it, and do not hardcode draws or
notices into the live HTML.

## Domain / DNS
- Domain: `bowlshornby.org.nz`, registered via domains.co.nz
- DNS: 4 A records at root (@) → GitHub Pages IPs
  (185.199.108/109/110/111.153), 1 CNAME (www → bennym4.github.io)
- HTTPS **not enforced yet** — waiting on GitHub's DNS check to pass.
  Once it does, tick "Enforce HTTPS" in Settings → Pages.

## Club facts (use these, don't invent others)
- Address: 521 Main South Road (on Hornby Domain), Hornby, Christchurch 8042
- Email: hornbydbc@gmail.com
- Coach: Dave Vincent — 021 070 1862
- Club has TWO full-size greens (not one — this was corrected once already)
- New players welcome any time of season, no experience/equipment needed

## Design system (do not deviate without asking)
- Deep turf green `#1E4630` — header/footer
- Mid green `#3F6B4A` — accents
- Warm parchment `#F2EFE6` — page background
- Clubhouse maroon `#8A2E35` — buttons/CTAs
- Brass gold `#C99A2E` — dividers, highlights
- Fonts: Fraunces (headings), Public Sans (body), Space Mono (small labels)
- Signature motif: thin horizontal "rink lines" (Google Fonts imported in styles.css)

## Explicitly deferred / not yet built
- Real member login (would need Cloudflare Access — free up to 50 users,
  discussed but not yet set up)
- Membership fees (join.html has a placeholder note flagging this)
- Enforcing HTTPS, once GitHub's DNS check passes

## House style for any new copy
Warm, community-club tone. Not corporate. Short sentences. This club is
run by volunteers for a small NZ town — write like it.
