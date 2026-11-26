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
resume.pdf                      public resume (version WITHOUT phone number)
projects/pangolin-robot.html
projects/f16-flight-control.html
projects/crazyflie.html
projects/ev-conversion.html
images/headshot.jpg             home-page portrait
images/<project>/               compressed figures per project
wrangler.jsonc, .assetsignore   deploy config
```
Project pages load the stylesheet as `../style.css` and link home as `../index.html`. The home page links to `projects/<name>.html`.

## Status
- Project pages live in `projects/` (fixed). Contact email, LinkedIn and resume are done. No GitHub link (Sahil's choice).
- SeaBot and the cricket bowling machine were removed: they never left design ideation. Do not re-add them.
- Job title is "Mechanical Engineer" (not Junior). FEA is intentionally NOT listed as a skill.
- Crazyflie stats use the event log numbers (230 s, 4 obstacles, 2/2 pads); Sahil confirmed, keep them.

## Content that still needs Sahil's input (leave TODO comments, never invent)
- Every project page has a "My contribution" TODO for his specific role.
- Crazyflie page: video is a Google Drive link; confirm it is shared publicly.
- EV conversion page: check what he is allowed to share about employer work before adding details or photos.

## Facts about Sahil (safe to use in site copy)
- Mechanical engineering graduate student at Stony Brook University, expected 2027. Based in Hicksville, Long Island, NY.
- Mechanical Engineer at Unique Technical Services since February 2026.
- Senior Intern at Unique Electric Solutions, January 2024 to January 2026, on Ford E450 and school bus EV conversion projects.
- Skills: see resume.pdf; SolidWorks, Fusion 360, Altium, MATLAB, Python, fabrication, control systems. No FEA.
- Resume (resume.pdf) is the source of truth for experience bullets, including LIHTI and Energy Terminal.
- Looking for robotics and mechatronics roles.

### Projects
- **Pangolin-inspired magnetic soft robot** (MEC 520 Smart Materials and Structures, Prof. Yao, May 2026): team of four (Sahil Aggarwal, Ishaan Jain, Omar Khan, Andrew Yancovitz). Kite-shaped scale redesign of Soon et al. 2023 for multi-axis bending. Source: Group 7 design report.
- **F-16 longitudinal flight control** (MEC 560 Advanced Control Systems, Prof. Amin Fakhari, May 2026): individual project. Source: final report PDF (MEC560FinalProject). Numbers on the page are verified against the final report: tracking error 0.3702 deg, robustness 4/28 eigen-stable and 2/28 sim-stable, saturated final theta 9.0567 deg, FL 2.89 deg vs LQR 16.44 deg peak.
- **Crazyflie autonomous navigation** (MEC 569, Stony Brook): team Sahil Aggarwal, Isaac Lalicic, Benny Wen. Python state machine (logandfly, sim_room, map_replay). Source: presentation deck.
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

## Suggested order of work
1. Move the project pages into `projects/` and fix links. Verify, then push.
2. Replace the contact placeholders and add `resume.pdf`.
3. Walk Sahil through each project page, asking him for role, approach, results and images, and fill in the TODOs.
4. Add an `images/` folder and place CAD renders, FEA plots and photos with captions.
5. Add basic SEO: page titles, meta descriptions, Open Graph tags, `favicon`, a `sitemap.xml` and `robots.txt` once the domain is live.
6. Confirm `https://sahilaggarwal.dev` and `https://www.sahilaggarwal.dev` both load over HTTPS.
