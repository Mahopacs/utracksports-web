# CLAUDE.md — utracksports.com Website

## Overview
Static marketing website for the uTrack Sports iOS app, live at https://utracksports.com. Plain HTML/CSS, no framework. Separate project from the uTrack app.

The uTrack app project (~/Documents/uTrack/) has a "## Related Projects" section near the top of its CLAUDE.md that cross-references this website project.

## Local location
~/Documents/utracksports-web/

## Pages
- index.html (home)
- features.html
- screenshots.html
- how-to.html
- faq.html
- support.html (lists support@utracksports.com)
- privacy.html (App Store privacy policy)
- styles.css
- screenshots/ (folder of app screenshots — currently demo-data images; to be replaced with real-name screenshots before App Store submission)

## Design
- Navy theme (#0E1B33) with pitch-green accents
- Fonts: Barlow Condensed (headings) + Inter (body)
- Responsive

## How it's wired (deployment chain)
1. Files live locally at ~/Documents/utracksports-web/
2. GitHub repo: github.com/Mahopacs/utracksports-web (remote uses SSH, not HTTPS — no tokens needed)
3. Cloudflare Pages is connected to that GitHub repo and auto-deploys on every push to the main branch
4. Custom domain utracksports.com points to the Pages site (DNS managed by Cloudflare, auto SSL)

## How to deploy a change
1. Edit the file(s) in ~/Documents/utracksports-web/
2. Commit and push to GitHub:
   git add -A
   git commit -m "describe the change"
   git push
3. Cloudflare Pages automatically rebuilds and deploys within ~1 minute. No manual Cloudflare step needed.
4. Verify at https://utracksports.com (may need a hard refresh / cache clear to see changes immediately)

## Infrastructure setup (reference)
- Domain registrar: Namecheap (domain registered there; renews there)
- DNS: managed by Cloudflare (nameservers jillian.ns.cloudflare.com / keenan.ns.cloudflare.com set in Namecheap → Custom DNS)
- Hosting: Cloudflare Pages (Free plan), project name "utracksports-web", connected to the GitHub repo
- SSL: automatic via Cloudflare
- Email: support@utracksports.com forwards to tedjyoung@yahoo.com via Cloudflare Email Routing (MX/SPF/DKIM records managed automatically by Cloudflare)

## Positioning / branding direction
- **Multi-sport positioning (decided 2026-06-16):** the app is becoming multi-sport — basketball is planned for Fall 2026. The website's brand/positioning is **de-emphasized away from soccer** at the headline/tagline/meta level. The app currently only does soccer, so soccer is NOT removed everywhere: concrete feature descriptions and screenshots stay soccer-specific for now; only top-level brand/positioning language was neutralized.
- **✅ Brand-level neutralization IMPLEMENTED (2026-06-16):** "youth soccer" → "youth sports" in index.html (`<title>`, `<meta name="description">`, hero eyebrow), features.html (lead), and faq.html ("What is uTrack?" answer). The faq.html "Is it only for soccer?" answer now reads: built for soccer today, architecture supports multiple sports, basketball planned Fall 2026.
- **Intentionally LEFT soccer-specific** (concrete, not brand-level): the faq.html "Is it only for soccer?" question + "built for soccer today" phrasing; concrete terms like "field view"/"match timeline"/"play-by-play"; all screenshots and their alt text.
- **✅ Social share card IMPLEMENTED (2026-06-16):** `images/utrack-social-card.png` (1600×600 PNG) added, plus a fresh Open Graph + Twitter Card block in index.html `<head>` (absolute URLs, `og:image`/`twitter:image` = https://utracksports.com/images/utrack-social-card.png, `twitter:card` = summary_large_image), mirroring the new title/description. These tags previously did not exist; index.html is currently the only page with them.
- **✅ Metadata SHORTENED for share-preview/SEO length (2026-06-16):** an OG inspector flagged the index.html title/description as too long, so all three title tags (`<title>` + `og:title` + `twitter:title`) now read "uTrack Sports — Stats from the sideline" and all three description tags (`<meta description>` + `og:description` + `twitter:description`) now read "uTrack is a youth sports stat-tracking app. Log plays live, build box scores and reports, share in a tap. Coming soon to the App Store." Title tags match each other; description tags match each other. `og:image`/`twitter:image`/`og:url`/`og:type`/`twitter:card` unchanged.
- **Soccer-flavored language sweep (2026-06-16):** beyond the literal word "soccer," soccer-flavored terms remain across the site. **✅ Three brand/headline-level items RESOLVED (2026-06-16):** how-to.html h1 "From kickoff to final in five steps" → "Track a game in five steps" (also dropped the `<br>` since the new headline is one line); screenshots.html h1 "Every angle of the match" → "Every angle of the game"; index.html hero lead "youth match"/"no halftime scramble" → "youth game"/"no post-game scramble". **Still soccer-flavored, intentionally LEFT as concrete feature/screenshot copy** (the (b) items): goals, corners, "a real match clock", match timeline, demo match, "goalkeepers marked", "field view", and the meta/og/twitter descriptions that name "match"/"field". These stay soccer-specific until the app is actually multi-sport.
- **Undo feature copy fix (2026-06-16):** features.html Undo item changed "Logged the wrong player or a goal got called back?" → "…or tapped the wrong stat?" (drops the soccer-specific "goal called back" framing).
- **✅ Screenshots gallery THIRD SECTION ADDED (2026-06-17):** a new **"Your teams & games"** section (`<h2 class="shots-heading">Your teams &amp; games</h2>`) now opens the gallery, placed immediately after the live-game hero (03b) and before "In-game stats." It has 3 cards in order **Teams (14-teams.png) → Roster (15-roster.png) → Games (09-games.png)** (reordered 2026-06-17 from the original Teams → Games → Roster; Games was MOVED out of In-game stats, h3/caption/alt unchanged). As a result **"In-game stats" is now 6 cards** (Games removed): Game Statistics (05), Timeline (06), Play-by-Play (08), Box Score (04), Stats hub (07), Full field view (03). "Season stats" (4 cards) unchanged. No new CSS (reused `.shots-heading`); no files renamed; index.html/features.html untouched.
- **✅ Screenshots gallery RESTRUCTURED (2026-06-17):** screenshots.html's single flat grid was split into TWO labeled sections, each an `<h2 class="shots-heading">` (new gold-accent CSS rule added to styles.css: `color:var(--gold)`, font 1.6rem, margins 46px top / 18px bottom) above its own `.shots` grid. The live-game hero (03b) still opens the page. **"In-game stats"** section (7 items): the new **Games (09-games.png) leads it**, then Game Statistics (05), Timeline (06), Play-by-Play (08), Box Score (04), Stats hub (07), Full field view (03). **"Season stats"** section (4 NEW items): Season Reports (10), Team Season Totals (11), Player Season (12), Team Results (13). The five previously-unused on-disk screenshots (09–13) are now all referenced. Timeline blurb "whole match" → "whole game". Closing caption changed "Screens shown using uTrack's built-in demo game." → **"Screens shown with sample team data."** No image files renamed; index.html/features.html untouched (features.html references no screenshots; index.html still uses 03/03b).

- **✅ Master player list FAQ added (2026-06-17):** faq.html gained a Q&A "Can a player be on more than one team?" (placed after "Do I need to create an account?", before "Where is my data stored?") explaining players are added once to a master list, then assigned to any team's roster, so a player can be on multiple teams without re-entering details.

## Notes / future work
- Replace demo-data screenshots in screenshots/ with real-name app screenshots before App Store submission (capture manually on iPhone, drop into the folder, commit + push)
- Privacy policy (privacy.html) will need updating when the future v3/v4 cloud-sync feature ships (plays syncing to cloud and appearing on the website)
