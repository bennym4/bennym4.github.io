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
1. Changes to THIS two-page site are made **here, directly** — not staged in
   the draft repo first. The draft is a different, nine-page site and the two
   have deliberately diverged. **Do not copy files between them.**
2. Show the owner a screenshot of the change before pushing. For design
   changes, show mockups of the options first.
3. **Always confirm before pushing** — everything here is public the moment
   GitHub Pages rebuilds (about a minute).
4. Claude pushes with git directly. After pushing, check the "pages build and
   deployment" workflow run actually succeeded before reporting it as live.
5. Claude cannot load this site over the network from its sandbox (egress is
   blocked), so "the deploy is green" is not the same as "the page looks
   right" — ask the owner to confirm the visual.
6. Style: ELI5, structured, one step at a time. Flag honest catches.

## Site structure (live repo)
2 pages, sharing one stylesheet:
- `index.html` — Home. Sections: hero, Life at the Club (photos), New
  Players, Find Us. Two buttons also link to `join.html`.
- `join.html` — How to Join. Sections: hero, Three Steps,
  membership-fees note.
- `styles.css` — shared design system, both pages import this
- `CNAME` — `bowlshornby.org.nz`
- `club-green.jpg` — the Home hero photo. Shown ONCE: it was removed from
  the "Life at the Club" section so it does not appear twice on the page.
- `club-deck.jpg` — the remaining "Life at the Club" photo
- `README.md`, `CLAUDE.md` — housekeeping, not part of the site

**Both pages share the same nav: `Home` · `How to Join`.** The current
page carries `class="active"` (maroon pill) and `aria-current="page"`.
The homepage used to have no nav at all and join.html only a single Home
link; that was changed on purpose, because a nav that appeared on one
page and only pointed backwards could not actually navigate. Keep the two
navs identical — if a page is ever added, it goes in both.

**No other pages exist here.** `about.html`, `news.html`, `members.html`,
`contact.html`, `tournaments.html`, `hire.html` and `links.html` were all
removed. Never link to them from the live site — the links would 404.
Anything that needs a contact route should use the `tel:` or `mailto:`
links already on the pages.

## Design system (do not deviate without asking)
- **Nav bar**: deep turf green `#1E4630`, with a gold bottom border
- **Hero**: clubhouse maroon `#8A2E35`, white text
- **Body**: warm parchment `#F2EFE6`
- **Footer**: clubhouse maroon `#8A2E35`
- Mid green `#3F6B4A` — accents; green also stays in h2/h3 headings
- Brass gold `#C99A2E` — dividers, highlights, badge, borders
- This matches the scheme signed off by the members on the draft site. The
  live site ran a green hero/footer until Sept 2026, when it was brought
  into line. Hero and footer colour is controlled by the `.hero` and
  `.site-footer` backgrounds — changing those two re-colours every page.
- `.btn-primary` is maroon, which is invisible on the maroon hero, so
  `.hero .btn-primary` is brass gold with dark text. Do not remove that
  override: without it the main call to action has no button at all.
- Fonts: Fraunces (headings), Public Sans (body), Space Mono (small labels)
- Signature motif: thin horizontal "rink lines" (Google Fonts imported in styles.css)
- Hero text widths are deliberate: `.hero h1` is `max-width: 22ch` and
  `.hero p.lede` is `56ch`. They were 14ch/46ch, which broke the headline
  into five narrow lines. Do not reduce them without asking.
- The Home hero is split: the photo (`.hero-media`) runs off the right
  edge at 46% width, and the text sits in `.hero-text` (max 30rem) on the
  left. A left-to-right gradient dissolves the photo's edge into the hero
  colour, so it uses the maroon `rgba(138, 46, 53, …)` — if the hero colour
  ever changes, that gradient has to change with it or a hard seam appears.
  The rink-lines motif is deliberately NOT drawn over the photo — on a
  photo it reads as scan lines. It still runs behind the plain parts of the
  heroes via the `.rink-lines` class.
- Under 860px the photo becomes a band above the text. It carries
  `margin-top: -64px` to cancel the generic `section { padding: 64px 0 }`;
  without that it floats in a green gap below the header.
- This was chosen over a full-bleed photo behind the whole hero: the
  members are all in the left of the frame, which is where the text sits,
  so a wash hid them and left only empty turf visible.

## Live data — Google Sheets
Not on the live site. The draws/notices Google Sheets feed lived in
`news.html`, which no longer exists here. The feed and its CSV URLs are
still in the draft repo — do not rebuild it, and do not hardcode draws or
notices into the live HTML.

## Domain / DNS
- Domain: `bowlshornby.org.nz`, registered via domains.co.nz
- DNS: 4 A records at root (@) → GitHub Pages IPs
  (185.199.108/109/110/111.153), 1 CNAME (www → bennym4.github.io)
- HTTPS **enforced** — GitHub's DNS check passed and "Enforce HTTPS" is
  ticked in Settings → Pages. The site serves over https://.

## Club facts (use these, don't invent others)
- Address: 521 Main South Road (on Hornby Domain), Hornby, Christchurch 8042
- Email: hornbydbc@gmail.com
- Coach: Dave Vincent — 021 070 1862
- Club has TWO full-size greens (not one — this was corrected once already)
- New players welcome any time of season, no experience/equipment needed

## Search engines / Google
As of Sept 2026 the site was **not indexed at all** — `site:bowlshornby.org.nz`
returned nothing. Nothing was blocking it (no noindex); Google had simply never
discovered the site. It is new (first published 24 Aug 2026) and nothing links
to it. The repo now carries `robots.txt`, `sitemap.xml`, canonical tags,
`lang="en-NZ"` and SportsClub structured data on the Home page.

Those files help Google understand the site once it arrives; they do not by
themselves get it discovered. The things that actually do:
- **Google Search Console** — verify, submit `sitemap.xml`, then URL Inspection →
  Request indexing. This is the direct "please crawl me" signal.
- **Google Business Profile** — for "bowls hornby" the map listing is what people
  see, and it is separate from the website.
- **A few real links** — a club listing on Bowls Canterbury / Bowls NZ, and the
  club Facebook page. Google finds sites by following links.

Search Console was set up under Stephen's personal Google account
(`stephenbennisonnz@gmail.com`) because the club Gmail password was not to hand.
**TO DO: once the `hornbydbc@gmail.com` password is available, add it as an Owner**
(Settings → Users and permissions) so access belongs to the club, not one person.
The same applies to the Google Business Profile when it is created.

The structured data deliberately omits a phone number: the only club phone is
Dave Vincent's personal mobile, and listing it there would make it the club's
official number in Google's eyes. Ask before adding it.

## Explicitly deferred / not yet built
- Real member login (would need Cloudflare Access — free up to 50 users,
  discussed but not yet set up)
- Membership fees (join.html has a placeholder note flagging this)

## House style for any new copy
Warm, community-club tone. Not corporate. Short sentences. This club is
run by volunteers for a small NZ town — write like it.
