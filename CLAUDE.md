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

## Notes / future work
- Replace demo-data screenshots in screenshots/ with real-name app screenshots before App Store submission (capture manually on iPhone, drop into the folder, commit + push)
- Privacy policy (privacy.html) will need updating when the future v3/v4 cloud-sync feature ships (plays syncing to cloud and appearing on the website)
