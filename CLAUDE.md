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
style.css                       shared dark theme styles
resume.pdf                      not added yet; the "Download resume" button links to it
projects/seabot.html
projects/crazyflie.html
projects/cricket-bowling-machine.html
projects/ev-conversion.html
images/                         for CAD renders, photos, plots (create when needed)
wrangler.jsonc, .assetsignore   deploy config
```
Project pages load the stylesheet as `../style.css` and link home as `../index.html`. The home page links to `projects/<name>.html`.

## KNOWN PROBLEM TO FIX FIRST
The four project pages were uploaded to the repo root instead of `projects/`, so project links currently 404 and the pages lose their styling. Move them into `projects/` with `git mv`, then check every internal link (home to projects, projects back to home, stylesheet paths). Show Sahil the result before pushing.

## Content that still needs Sahil's input (leave TODO comments, never invent)
- `index.html` Contact section: placeholder email (`you@example.com`), LinkedIn and GitHub URLs. His GitHub username is `sahilaggarwaleng-dev`. His email is sahil.aggarwal.eng@gmail.com. Ask before using it publicly.
- `resume.pdf`: ask him to place it in the repo root.
- Every project page has TODO placeholders for his specific role, results and numbers, and images.
- Crazyflie page: embed the presentation video (ask for the YouTube link).
- Cricket bowling machine page: almost entirely empty. Ask him for details.
- EV conversion page: check what he is allowed to share about employer work before adding details or photos.

## Facts about Sahil (safe to use in site copy)
- Mechanical engineering graduate student at Stony Brook University, expected 2027. Based in Hicksville, Long Island, NY.
- Junior Mechanical Engineer at Unique Technical Services since February 2026.
- Senior Intern at Unique Electric Solutions, January 2024 to January 2026, on Ford E450 and school bus EV conversion projects.
- Skills: SolidWorks (CAD), FEA, MATLAB, Python, mechatronics, fabrication, control systems.
- Looking for robotics and mechatronics roles.

### Projects
- **SeaBot**: autonomous underwater drone to trace nitrogen pollution in Long Island coastal waters (Suffolk County cesspool runoff). Four-person team, Sahil co-leads. Phase 0 design uses thrust-vectoring impeller locomotion and a live camera feed on a tethered power system. Phases are named SeaBot 0.1, 1.0 and so on.
- **Crazyflie autonomous navigation** (MEC 569, Stony Brook): Crazyflie quadcopter navigates an arena, avoids obstacles, lands on pads and returns. Python script based on `logandfly.py`. Team of three.
- **Automated Cricket Bowling Machine**: mechatronics and fabrication project. Details to come from Sahil.
- **Ford E450 and school bus EV conversions**: industry work at Unique Electric Solutions.

## Rules
1. Never invent results, metrics, dates, employers or claims. If a detail is missing, leave a visible TODO and ask Sahil.
2. Keep it plain HTML and CSS. No frameworks, build tools or dependencies.
3. Keep the design clean, dark, responsive and fast. Compress images. Use descriptive `alt` text.
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
