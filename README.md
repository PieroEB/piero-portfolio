# Piero Espinoza — Portfolio

Personal portfolio website: Computer Science @ FIU · Data, Python & Applied AI.

**Live site:** https://pieroeb.github.io/piero-portfolio/

Plain HTML + CSS + a few lines of JavaScript. There's no build step and no framework, so any change you save goes live the next time you push.

## Project structure

```
index.html          All page content (sections: hero, about, experience, work, awards, skills, process, contact)
styles.css          Design tokens (colors, fonts, spacing) at the top, then styles per section
assets/
  piero.jpg         Profile photo (hero)
  Piero_Espinoza_Resume.docx   Résumé linked by the "Download résumé" buttons
  icons/            Tool logos used in "What I work with"
serve.js            Tiny local server for previewing (node serve.js)
DESIGN.md           Visual style reference the design follows
```

## Preview locally

```bash
node serve.js
```

Then open http://localhost:5173 in your browser.

## Common edits

- **Change text:** edit `index.html`. Each section starts with a comment such as `<!-- 03 Work -->`.
- **Change the photo:** replace `assets/piero.jpg` (keep the same name, portrait 3:4 works best).
- **Update the résumé:** replace `assets/Piero_Espinoza_Resume.docx`. A PDF is better for recruiters: add `assets/Piero_Espinoza_Resume.pdf` and update the `href` links in `index.html`.
- **Add a skill icon:** put an `.svg` in `assets/icons/` and copy one `<li class="tile">…</li>` line in the Skills section.
- **Change colors or fonts:** edit the variables in `:root` at the top of `styles.css`.

## Publish changes

```bash
git add .
git commit -m "Describe your change"
git push
```

GitHub Pages redeploys automatically in about a minute.
