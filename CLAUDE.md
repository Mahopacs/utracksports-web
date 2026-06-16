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

## Notes / future work
- Replace demo-data screenshots in screenshots/ with real-name app screenshots before App Store submission (capture manually on iPhone, drop into the folder, commit + push)
- Privacy policy (privacy.html) will need updating when the future v3/v4 cloud-sync feature ships (plays syncing to cloud and appearing on the website)
