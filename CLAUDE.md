# Sahil Aggarwal: Engineering Portfolio

Read this file first. It is the full handoff from a planning chat, so you do not need that conversation.

## Goal
A personal engineering portfolio for Sahil Aggarwal, hosted at his own domain, https://sahilaggarwal.dev, with no site builders. The audience is recruiters and hiring managers for robotics, mechatronics and mechanical engineering roles.

## How it is built and deployed
- Plain HTML and CSS only. No frameworks, no build step, no package manager.
- Source: GitHub repo `sahilaggarwaleng-dev/portfolio`, branch `main`.
- Hosting: Cloudflare Workers with static assets, connected to the repo. Every push to `main` auto-deploys in about a minute. Deploy command is `npx wrangler deploy`, with no build command.
- Deploy config lives in `wrangler.jsonc` and `.assetsignore`. Do not delete or rename them. `.assetsignore` keeps config files and `.git` out of the published site. (If either file is missing from the repo, recreate it: `wrangler.jsonc` with name `portfolio`, a recent `compatibility_date`, and `assets.directory` set to `./`; `.assetsignore` listing `wrangler.jsonc`, `.assetsignore`, `.git`.)
- Temporary URL: https://portfolio.sahil-aggarwal-eng.workers.dev
- Custom domain `sahilaggarwal.dev` (and `www`) is added in Cloudflare under the project's Settings, Domains & Routes. Check whether it shows Active. This part is done in the Cloudflare dashboard by Sahil, not in this repo.

## Intended file structure
```
index.html                      home: intro, projects, skills, experience, contact
style.css                       shared light theme styles (colors are CSS variables in :root)
Sahil-Aggarwal-Resume.pdf       public resume (version WITHOUT phone number)
projects/pangolin-robot.html
projects/f16-flight-control.html
projects/injection-molding.html
projects/crazyflie.html
projects/ev-conversion.html
projects/icorps-customer-discovery.html
images/headshot.jpg             home-page portrait
images/<project>/               compressed figures per project
images/cards/                   16:9 home-card thumbnails (640x360)
images/og-image.jpg             1200x630 link-preview image
favicon.svg, favicon-32.png, apple-touch-icon.png
404.html                        served via "not_found_handling": "404-page" in wrangler.jsonc
sitemap.xml, robots.txt         update sitemap when adding a page
wrangler.jsonc, .assetsignore   deploy config
```
Project pages load the stylesheet as `../style.css` and link home as `../index.html`. The home page links to `projects/<name>.html`.

## Status
- Project pages live in `projects/` (fixed). Contact email, LinkedIn and resume are done. No GitHub link (Sahil's choice).
- SeaBot and the cricket bowling machine were removed: they never left design ideation. Do not re-add them.
- Job title is "Mechanical Engineer" (not Junior). FEA is intentionally NOT listed as a skill.
- Skills stays ABOVE Projects on the home page (Sahil's explicit choice, overrides the upgrade guide).
- No "looking for a role" line in the hero (Sahil removed it).
- Hidden TODO comments only; never show empty headings or placeholder boxes on the live site.
- Crazyflie stats use the event log numbers (230 s, 4 obstacles, 2/2 pads); Sahil confirmed, keep them.

## Content that still needs Sahil's input (leave TODO comments, never invent)
- Crazyflie page: video is a Google Drive link. Sahil has an MP4 but will add it another time (unlisted YouTube link or MP4 under 25 MB in images/crazyflie/).
- Analytics: deferred by Sahil. When he sends the Cloudflare Web Analytics snippet, add it to every page (index, projects/*, 404).
- EV conversion page: check what he is allowed to share about employer work before adding details or photos.

## Facts about Sahil (safe to use in site copy)
- Mechanical engineering graduate student at Stony Brook University, expected 2027. Based in Hicksville, Long Island, NY.
- Mechanical Engineer at Unique Technical Services since February 2026.
- Senior Intern at Unique Electric Solutions, January 2024 to January 2026, on Ford E450 and school bus EV conversion projects.
- Skills: see resume.pdf; SolidWorks, Fusion 360, Altium, MATLAB, Python, fabrication, control systems. No FEA.
- Experience bullets: Sahil supplied a detailed list (Nov 2026) that supersedes the resume where they differ. Build count is 15+ (Sahil confirmed). Never mention the FUZO program or any client/partner names (e.g. SCS) on the site. Sahil handled much of the procurement at both UES and UTS (vendors, orders, cheapest options, hard-to-find parts). Dropped as minor: tool evaluation, shop-floor organization, machine cleaning.
- Looking for robotics and mechatronics roles.

### Projects
- **Pangolin-inspired magnetic soft robot** (MEC 520 Smart Materials and Structures, Prof. Yao, May 2026): team of four (Sahil Aggarwal, Ishaan Jain, Omar Khan, Andrew Yancovitz). Kite-shaped scale redesign of Soon et al. 2023 for multi-axis bending. Source: Group 7 design report. Sahil wrote the bulk of the report (not all of it), did the calculations, helped with prototyping.
- **F-16 longitudinal flight control** (MEC 560 Advanced Control Systems, Prof. Amin Fakhari, May 2026): individual project. Source: final report PDF (MEC560FinalProject). Numbers on the page are verified against the final report: tracking error 0.3702 deg, robustness 4/28 eigen-stable and 2/28 sim-stable, saturated final theta 9.0567 deg, FL 2.89 deg vs LQR 16.44 deg peak.
- **Desktop PLA recycling injection molding machine** (MEC 440/441 senior design, 2025-2026): team of four plus faculty advisor. DO NOT name teammates or the advisor (Sahil said no). Based on Buster Beagle 3D MK3; attribution banner and home-card tag are mandatory, never claim original design, never use Buster Beagle images. Confirmed by Sahil: 15 kg/year waste, 51.7 psi final injection pressure, 15 g into the mold. Unknown: who did pneumatic force calc (credit "the team"). Near-miss safety story: Sahil said do NOT include. The Buster Beagle vs ours table still needs Sahil's review. Figures added from the report (team photos/CAD only). Table checked against report text.
- **Crazyflie autonomous navigation** (MEC 569, Stony Brook): team Sahil Aggarwal, Isaac Lalicic, Benny Wen. Python state machine (logandfly, sim_room, map_replay). Source: presentation deck. Sahil wrote the flight/mission code and a sensor test script; a teammate did logging and graphs.
- **I-Corps customer discovery** (NY I-Corps Lean Bootcamp, Spring 2023, part of the LIHTI fellowship): team of three, Sahil was Co-Entrepreneurial Lead. 20 interviews in three weeks (resume). Do NOT name teammates, interviewees or companies. Do not quote the technology's performance claims. Pending from Sahil: his personal contributions and "what I learned about working with people"; whether the technology can be described publicly (currently described generically).
- Home page has a "Beyond the technical work" section; each item links to its proof.
- **Ford E450 and school bus EV conversions**: industry work at Unique Electric Solutions.

## Rules
1. Never invent results, metrics, dates, employers or claims. If a detail is missing, leave a visible TODO and ask Sahil.
2. Keep it plain HTML and CSS. No frameworks, build tools or dependencies.
3. Keep the design clean, bright, warm, responsive and fast. Light theme chosen by Sahil (was dark). Compress images. Use descriptive `alt` text.
4. Before every commit, check that all internal links and image paths resolve.
5. Show Sahil a summary of the changes and ask before pushing. A push goes live on his public site.
6. Commit messages should be short and descriptive.
7. Do not add tracking, analytics or third-party scripts without asking.
8. Before publishing any employer-related content (EV conversion page), confirm with Sahil that he is cleared to share it.

## Planning docs (kept outside the repo, Sahil has them)
- portfolio-upgrade-guide.md: audit and upgrade plan. Done: SEO/OG/favicon/sitemap/robots/404, card images, print CSS, focus states, experience grouping, resume rename, last-updated line, EV page from resume facts.
- injection-molding-project.md: MEC 440 senior design page. The Buster Beagle 3D attribution banner is mandatory at the top of that page and on its home card. Never claim original design. Needs the report PDF for figures.
- f16-control-project.md: done; numbers verified against the final report.

## Suggested order of work
1. Move the project pages into `projects/` and fix links. Verify, then push.
2. Replace the contact placeholders and add `resume.pdf`.
3. Walk Sahil through each project page, asking him for role, approach, results and images, and fill in the TODOs.
4. Add an `images/` folder and place CAD renders, FEA plots and photos with captions.
5. Add basic SEO: page titles, meta descriptions, Open Graph tags, `favicon`, a `sitemap.xml` and `robots.txt` once the domain is live.
6. Confirm `https://sahilaggarwal.dev` and `https://www.sahilaggarwal.dev` both load over HTTPS.
