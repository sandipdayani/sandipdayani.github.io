# sandipdayani.github.io

Source for [sandipdayani.github.io](https://sandipdayani.github.io). Built with [Quarto](https://quarto.org) and deployed to GitHub Pages via GitHub Actions.

---

## Project structure

```
.
├── _quarto.yml              # Site config (nav, theme, metadata)
├── index.qmd                # Home page
├── research.qmd             # Research overview with extracted figures
├── publications.qmd         # Publications list
├── cv.qmd                   # CV (inline + PDF download)
├── news.qmd                 # News feed
├── styles.scss              # Theme (fonts, colors, custom components)
├── styles.css               # Empty extension file
├── assets/img/              # Profile photo + research figures
├── files/                   # CV PDF goes here
└── .github/workflows/       # Auto-deploy workflow
```

---

## First-time setup

### 1. Create the repo on GitHub

Create a **new public repository** named `sandipdayani.github.io` (must match your GitHub username exactly for a user site).

### 2. Push this code

```bash
cd sandip-website
git init
git add .
git commit -m "Initial site"
git branch -M main
git remote add origin https://github.com/sandipdayani/sandipdayani.github.io.git
git push -u origin main
```

### 3. Enable GitHub Pages

In the repo on GitHub: **Settings → Pages → Source: GitHub Actions**.

The workflow in `.github/workflows/publish.yml` will run on every push to `main`, render the site, and deploy it. First deploy takes ~2 minutes. After that the site is live at `https://sandipdayani.github.io`.

---

## Local preview

Install Quarto from <https://quarto.org/docs/get-started/>, then:

```bash
quarto preview
```

This opens the site at `http://localhost:4848` with live reload.

To do a one-off render without preview:

```bash
quarto render
```

The generated site lands in `_site/` (gitignored — only the source is committed, GitHub Actions handles rendering).

---

## Content notes

| File / Location | What to do |
|---|---|
| `files/Resume_Sandip_Dayani.pdf` | Replace when the CV PDF is updated. Referenced from `cv.qmd`. |
| `assets/img/research/` | Research page visuals extracted from the IJP paper, MSc thesis, master research project, and bachelor CFD report. |
| `_quarto.yml` &nbsp;`site-url:` / `repo-url:` | Already set to `sandipdayani.github.io`. If you use a different repo name later, update both. |
| `index.qmd` thesis-defense news item | Update the month once defense is scheduled / completed. |

### Figure attribution

If you reuse figures from your IJP paper, add a short citation under the figure in `research.qmd`, e.g.:

```markdown
![Damage field on a polycrystalline RVE...](assets/img/cp_damage.png)

*Reproduced from Dayani et al., Int. J. Plasticity, 2025.*
```

You hold author rights to reuse your own figures on a personal academic page under Elsevier's standard agreement, but citing the source is correct practice.

---

## Adding new content

**New publication** &nbsp;·&nbsp; Edit `publications.qmd`. Copy the `.pub-entry` div block, fill in details, add a BibTeX block. Optionally add a one-line entry to `news.qmd` and the home page news list.

**New research project** &nbsp;·&nbsp; Add a section to `research.qmd` matching the existing pattern (heading, figure, description, optional output line).

**News item** &nbsp;·&nbsp; Add a `.news-item` block at the top of `news.qmd`. Mirror it to the home page if it's significant.

---

## Design notes

- **Fonts:** Fraunces (display serif) + Source Sans 3 (body). Loaded from Google Fonts.
- **Palette:** Warm off-white background, deep charcoal text, steel-blue accent.
- **Theme base:** Bootstrap `cosmo` via Quarto, heavily overridden in `styles.scss`.

To change the accent color globally, edit `$primary` and `$link-color` at the top of `styles.scss`.
