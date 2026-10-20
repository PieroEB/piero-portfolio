# AGENTS.md — Piero Espinoza Portfolio

Context for any AI coding agent (Claude, Codex, Copilot, etc.) working in this repository. Read this file fully before making changes.

---

## 1. What this project is

The personal portfolio website of **Piero Espinoza**, a Computer Science student at Florida International University (FIU). It's aimed at **recruiters** for data, analytics, software engineering, and applied AI roles.

- **Live site:** https://pieroeb.github.io/piero-portfolio/
- **Repository:** https://github.com/PieroEB/piero-portfolio (public)
- **Hosting:** GitHub Pages, deployed from branch `main`, folder `/` (root). Every push to `main` goes live in about a minute.
- **Owner's GitHub:** [PieroEB](https://github.com/PieroEB)

### Working with Piero
- Piero writes in **Spanish**. Reply in Spanish unless he writes in English. The **website content is in English** (for US recruiters).
- He wants to **collaborate**: you make the changes, he reviews them in VS Code and in the browser, and he decides when to publish.
- **Do not push to GitHub unless he asks** ("publícalo", "súbelo", "push"). Edit locally, show him, then commit and push on request.

### Identity: do not confuse
Piero Espinoza (Computer Science) is **not** Hernán Espinoza (Economics). Never mix their education, experience, or projects.

---

## 2. Tech stack and structure

Plain **HTML + CSS + a little vanilla JavaScript**. No framework, no build step, no package manager. Keep it that way unless Piero explicitly asks for a framework.

```
index.html        All page content. Sections are marked with comments: <!-- 01 About --> … <!-- Contact -->
styles.css        Design tokens in :root at the top, then styles per section, responsive rules at the bottom
assets/
  piero.jpg                    Profile photo (hero). Portrait 768x1024
  Piero_Espinoza_Resume.pdf    Résumé linked by every "Résumé / Download résumé" button (3 places)
  icons/*.svg                  Tool logos for the Skills section (self-hosted; no CDN)
  projects/gridlock.webp       Real screenshot of the GridLock web app (built from the GridLock repo, local-preview mode)
serve.js          Local static server: `node serve.js` → http://localhost:5173
README.md         Human guide for common edits and publishing
DESIGN.md         Visual style reference (see §4). Source of truth for design decisions
.nojekyll         Tells GitHub Pages to serve files as-is
.gitignore        Excludes private notes (see §8)
```

The only JavaScript is inline at the bottom of `index.html`: nav highlighting for the active section, the footer year, and the mobile menu toggle.

External resources: Google Fonts only (Playfair Display, Inter Tight, Inter, JetBrains Mono). Everything else is local.

---

## 3. Page sections (in order)

| # | id | Content |
|---|---|---|
| — | `.nav` | Floating glass nav: name, section links (hidden ≤1080px → "Menu" button with dropdown), black "Résumé" button |
| Hero | `.hero` | Dark stage. Eyebrow, display name "Piero *Espinoza*", tagline, CTAs, **profile photo** with a "B.S. Computer Science · Dec 2026" badge. On ≥1024px: text left, photo right, vertically centered, hero height capped at `min(100svh, 1040px)` and photo height tied to the viewport (avoid empty black areas on big screens: Piero flagged this). On smaller screens: stacked and centered |
| — | `.spectrum` | Animated rainbow gradient line (used **once** per page only) |
| 01 | `#about` | Story + quick facts list (Miami, FIU, Dec 2026, GPA 3.5, Dean's List, languages, focus) |
| 02 | `#experience` | Lime band. Numbered steps (BBVA Peru, FIU Math Lab) + BBVA "AI Adoption Analytics" case-study card with 3 stats |
| 03 | `#work` | Two large feature cards with "My role" boxes and a browser-window frame at the bottom: **GridLock** shows a real screenshot of its web app; **CipherQ** shows an HTML/CSS bar chart (built by inline JS from real counts) of one Policy Lab Grover run, where 489 of 512 shots (95.5%) landed on violation `1111` vs. a 6.25% random baseline. Then "More data projects" (E-commerce pipeline, Spotify analysis) |
| 04 | `#awards` | Saffron band. HSI Battle of the Brains 1st place (black card), Dean's List, ALPFA, Hackathons |
| 05 | `#skills` | Icon tiles in 4 groups (Languages, Data & analytics, Cloud & databases, AI & engineering) + "Methods" pills |
| 06 | `#process` | Understand → Build → Validate |
| 07 | `#contact` | Dark footer: email, GitHub, LinkedIn, résumé |

---

## 4. Design system (from DESIGN.md)

The style is an editorial, Dia-browser-like system: a **dark hero stage** opening onto a **light editorial page**. Piero chose this design. Keep it consistent.

**Colors** (all in `:root`): `--void #020204` (hero and footer), `--bone #f8f8f8` (page canvas), `--paper-white #fff` (cards), `--linen #efefef` (pills), `--lime #f2fcb3` and `--saffron #ffdc5c` (the only color washes, used as full-width section bands), and `--spectrum` (the rainbow gradient, used once only). Text colors: `#000`, `--carbon #636363`, `--slate #888`.

**Type:**
- Display: Playfair Display 400, tight tracking (-0.03em), line-height ~0.95.
- Section headings: Inter Tight 650, -0.05em.
- Body: Inter.
- Eyebrows and step numbers: JetBrains Mono, 12–13px, uppercase, 0.1em tracking (`01 — About`).

**Rules:**
- Border radius only from this set: **12, 16, 20, 24, 9999px**.
- Cards get a **1px border, not shadows**. Shadows are reserved for the floating nav, the white hero button, and the browser-window mockups.
- **No hover transforms** (no scale or translate). Transitions change color, background, border, or opacity only, at 0.2s ease.
- No bold weights (600–700+) on display headlines.
- No colored buttons. Use black on white/linen or white on black.
- Section gap is about 80px. Generous whitespace.
- The page must adapt to every screen size and must never scroll horizontally. Breakpoints: `1080px` (nav → menu, work and experience go single-column), `860px` (about, awards, and skills go single-column), `600px` (phone tweaks). Test at **1440, 1280, 820, and 375 px**.

---

## 5. Content rules: accuracy first

The portfolio must be **truthful and verifiable**. Never invent metrics, results, awards, roles, or technologies. Don't present planned work as finished.

### Verified facts you can use
- **Education:** FIU, B.S. Computer Science, expected **Dec 2026**, GPA **3.5/4.0**, Dean's List **Fall 2024 – Spring 2026**.
- **Location and languages:** Miami, FL. English (fluent), Spanish (native).
- **BBVA Peru, Data & Analytics Enable Summer Intern** (May–Aug 2026):
  - Built dashboards and reports in Excel, Looker, and QuickSight; used AWS S3 and SageMaker.
  - AI Adoption Analytics: ~3,022 employees, 56 variables screened, logistic regression and segmentation, a gap from 28% adoption to a 35% target.
- **FIU Math Lab Learning Assistant** (Oct 2024 – present).
- **GridLock** (ShellHacks 2026, team of 4: Piero, Boris Steeven Mino, Adrian Perez, Diego Rios). Piero did **data and frontend**. The original team repo (https://github.com/StBoris04/SperryTech_Hackathon_2026-PDSA-, 16 commits by Piero, PR #8 `piero/frontend`) shows he authored `src/App.jsx` (React + Leaflet map, project details, comparison with the 25-mile check, recommendation views, agent connection, offline fallback), plus the Gemini PDF extraction with a JSON schema, OSM/HIFLD geolocation, and validators that keep source references. Diego wrote the recommendation agent engine; Boris wrote the database and backend. Verified numbers (used on the site): **252** PDF project candidates and **45** validated records. The **166** projects figure is in the team docs and the résumé, but the public repo dataset (and the screenshot) shows 78, so the site doesn't use 166. Repo: https://github.com/PieroEB/GridLock
- **CipherQ** (Qollab × IonQ Global Quantum Hackathon 2026, team: Adrian Perez Galindo, Boris Steeven Mino, Piero).
  - **Policy Lab:** Piero wrote the exact classical evaluator (merged PR #2, 10 passing tests); it checks all 16 assignments. https://github.com/AdrianRPG/cipherq-policy-lab · https://qollab.xyz/u/bmino/cipherq-policy-lab-2
  - **Channel Detective:** BB84 simulator and evidence lab with confidence intervals. https://github.com/PieroEB/CipherQ_Channel_Detective-
  - The chart on the site is real output of one local Policy Lab run (`main.py --scenario 0 --iterations 3 --shots 512`, Qiskit 2.5.2, BasicSimulator): 489 of 512 shots on `1111`. Counts live in the inline script at the bottom of `index.html`. Keep the counts in an **array**: object keys like "1000" get reordered as integers.
- **AI-Powered Stock Market Predictor** (AI4ALL Ignite Summer '25 team project, repo owned by AyomideOlumideAttah): https://github.com/AyomideOlumideAttah/AI-Powered-Multifactor-Stock-Market-Predictor. Piero's commit `f04a238` added `stockapp.py` (359 lines), a Streamlit app that pulls yfinance prices and 12 FRED macro series, engineers features (returns, volatility, MAs, RSI, 1- and 7-day lags), trains Random Forest vs. logistic/linear models on a chronological 80/20 split, and predicts next-session direction and return with feature importance and CSV export. Teammates built the notebook and the original `app.py`.
- **CS Capstone, Arena Shooter** (Godot/GDScript, TRI-ADIC/arena-shooter-capstone-i): Piero's public contribution is a health-bar feature (merged PR #6). **Not on the site yet**; Piero will share more.
- **From the résumé only** (no public repo yet): E-commerce Analytics Pipeline (in progress; Azure SQL, SQL, Python, Power BI), Spotify Track Data Analysis (Jan 2025; 100,000+ songs, pandas, Matplotlib).
- **Awards and leadership:** HSI Battle of the Brains, **1st place in the technology category among 18 universities** (he built the team's web app on his own in 24 hours); ALPFA Tech Group Analyst (Jan 2024 – May 2025).

### Open questions: do not add these claims until Piero confirms
1. ~~GridLock frontend~~: resolved. The team repo commit history confirms Piero built it (now on the site).
6. AI4ALL Ignite: confirm Piero was a cohort member (his commit is in the cohort project). Don't list AI4ALL under Awards until confirmed.
2. BBVA: whether the internal figures (3,022 / 56 / 28%→35%) are cleared for public use. They're on the site because they're on his résumé.
3. Battle of the Brains: year, team, what the app did, and its stack.
4. ShellHacks and Qollab results or placements: unknown. Don't claim any.
5. Target roles and job-search status: not stated on the site.

### Other public repos (checked Oct 2026)
The public GitHub repos with portfolio-quality work are already featured (GridLock, CipherQ). The rest are excluded on purpose (below). If Piero adds new repos, review the code and README before adding a card: only real, working projects.

### Deliberately excluded from the site
- **AI-created** repo: a workshop template by another author with unfinished TODOs. Don't feature it.
- **CreditGuard** repo: only a README and requirements so far. Add it only once it has real code.
- Early 2024 web exercises (Calculator, Timer, To-do list), `Demo`, `Music-files`.
- His **phone number**: never put it in the HTML. (The downloadable PDF résumé does contain it. That's Piero's choice; offer a phone-free version if he asks.)

---

## 6. Common tasks

- **Edit text:** `index.html`, find the section comment.
- **Add a project card:** copy an `<article class="more-card">` block (small) or `<article class="feature">` (large, 2-up) in `#work`.
- **Add a skill:** save an SVG logo into `assets/icons/` (self-host it; good sources are Devicon, Simple Icons, and Iconify's `logos` set) and copy one `<li class="tile">` line.
- **Replace the résumé:** overwrite `assets/Piero_Espinoza_Resume.pdf` with the same name. If you convert from Word: open the .docx in Word and save it as PDF (format 17 via COM works on this machine).
- **Change the photo:** replace `assets/piero.jpg`, keeping a 3:4 portrait.

## 7. Workflow

1. Preview locally: `node serve.js`, then open http://localhost:5173. Use `node`, not `npx`. For real screenshots at exact sizes, headless Chrome works: `chrome.exe --headless=new --window-size=1920,1080 --screenshot=out.png http://localhost:5173/`.
2. Check desktop and phone widths, and confirm there's no horizontal overflow and no console errors.
3. Show Piero the change. **Wait for his OK.**
4. Publish:
   ```bash
   git add .
   git commit -m "Short description"
   git push
   ```
   Then confirm the change is live at https://pieroeb.github.io/piero-portfolio/

Commit messages: short, imperative, in English (e.g. `Add CreditGuard project card`).

## 8. Files that must stay private

`PORTFOLIO_RESEARCH.md` (detailed research notes, including evaluations and open questions) and `Piero_Espinoza_Resume-2026_Oct.docx` (the original résumé copy) live in this folder but are **git-ignored**. Never commit them, and never remove them from `.gitignore`. `PORTFOLIO_RESEARCH.md` is the most complete source of facts about Piero; read it locally when you need more detail.
