# mijicuet.github.io

Personal research site for **Md Kausar Hamid Miji** — nanophotonics and plasmonics,
FDTD modelling with Meep and Tidy3D.

Live at <https://mijicuet.github.io>

---

## Stack

Deliberately dependency-free: hand-written semantic HTML, one modern CSS file, one
vanilla JS file. No framework, no build step, no npm. GitHub Pages serves it as-is.

| Path | Purpose |
|------|---------|
| `assets/css/main.css` | Entire design system — tokens, layout, components, print styles |
| `assets/js/main.js` | Nav, theme toggle, scroll reveal, gallery filters, hero canvas |
| `assets/img/` | Favicon, Open Graph card |
| `assets/figures/` | **Simulation figures — replace these with your own** |
| `sitemap.xml`, `robots.txt`, `site.webmanifest` | SEO and PWA metadata |

### Features

- Responsive from 320 px to ultrawide; no horizontal scroll
- Light/dark theme, remembered in `localStorage`, respects system preference
- Accessibility: skip link, landmarks, visible focus rings, `aria-current`,
  keyboard-operable nav (Escape closes), alt text throughout
- `prefers-reduced-motion` honoured — the hero animation renders one static frame
- Hero canvas pauses when off-screen or the tab is hidden (battery friendly)
- SEO: canonical URLs, Open Graph + Twitter cards, JSON-LD `Person` schema, sitemap
- Print stylesheet — pages print cleanly without nav, footer or dark backgrounds

---

## Replacing the placeholder simulation figures

The gallery ships with six clearly watermarked placeholder plots so the layout is
visible. To use your own results:

1. Export your figure as PNG (roughly 4:3, at least 1200 px wide, dark background
   suits the design but any background works).
2. Save it into `assets/figures/`, overwriting the matching placeholder:

   | File | Study |
   |------|-------|
   | `fig-nearfield-dimer.png` | Nanoparticle dimer hot-spots |
   | `fig-lspr-spectra.png` | LSPR spectral decomposition |
   | `fig-metasurface-spectra.png` | Metasurface Fano response |
   | `fig-waveguide-mode.png` | Hybrid waveguide mode |
   | `fig-convergence.png` | Convergence &amp; resolution study |
   | `fig-parameter-sweep.png` | Design-space parameter sweep |

3. Open `simulations.html` and edit that card's `<h2>`, description, `alt` text and
   the `<dl class="specs">` block (solver, sweep, output) to match your study.
4. Delete the dashed "Note —" box near the top of `simulations.html` once every
   placeholder is replaced.

To **add** a study, copy an entire `<article class="card ...">` block and update the
`data-tags` attribute so the filter buttons pick it up (`plasmonics`, `metasurface`,
`waveguide`, `method`, `meep`, `tidy3d`).

---

## Filling in publications

`publications.html` is scaffolded with template entries marked
*"Template — replace or delete"*. Replace them with real citations, add DOI/PDF links,
and delete any section you do not need. Also add your Google Scholar, ORCID and
LinkedIn URLs — they are marked `[add link]`.

---

## Editing pages

`index.html` is standalone. The other pages were generated from a shared template so
the header, footer and metadata stay identical across the site.

You can simply edit the generated `.html` files directly — that is perfectly fine for
small changes. If you make a change that affects **every** page (a new nav item, a
footer change), edit it once in the generator instead and re-run:

```bash
python3 build_site.py .
```

The generator (`build_site.py` + `page_bodies.py`) is kept outside the repo. Ask for a
copy if you want to regenerate rather than hand-edit.

---

## Page inventory

| Page | Purpose |
|------|---------|
| `index.html` | Home — hero, research focus, toolchain, selected work |
| `research.html` | Five research threads, methodology workflow |
| `simulations.html` | Filterable FDTD study gallery |
| `publications.html` | Papers, preprints, talks, theses *(scaffolded)* |
| `projects.html` | ML and modelling projects |
| `Work_Experience.html` | Career timeline |
| `about.html` | Biography and full skills matrix |
| `leadership.html` | Fellowships, awards, service |
| `contact.html` | Contact details and message form |
| `404.html` | Not-found page |
| `GHCNd/project_ghcnd.html` | GHCNd project overview |
| `SysID/index.html` | Kolmogorov–Arnold network project overview |
| `Vulnerable_and_outdated_Components/index.html` | Cybersecurity project overview |
| `hero_banner.html` | Legacy URL — redirects to home |

The two Jupyter exports (`GHCNd/ML_With_GHCNd.html`,
`SysID/System_Identification.html`) are left as generated, with a slim
"back to project" bar added at the top.

---

## Verification performed

- All 14 designed pages: valid nesting, exactly one `<h1>`, full landmark set
- Every internal link and image reference resolves on disk
- Every image has `alt` text; every form control has a label; every button an accessible name
- WCAG AA contrast verified for all 13 key colour pairs in **both** light and dark themes
- No fixed-pixel widths; every multi-column grid has a mobile collapse rule
- CSS braces balanced, no undefined custom properties; JS passes syntax check
- `sitemap.xml`, `site.webmanifest` and the JSON-LD schema all parse

---

## Things worth updating

- [ ] Replace the six placeholder figures in `assets/figures/`
- [ ] Add real publications, preprints and talks
- [ ] Add Google Scholar / ORCID / LinkedIn links (`publications.html`, `contact.html`)
- [ ] Add thesis titles in `publications.html`
- [ ] Optionally add a downloadable CV PDF and link it from `about.html`
- [ ] `profile_pic.jpg` (836 KB) is no longer referenced — the pages now use the
      optimised `assets/img/portrait.jpg` (66 KB). Delete the original if you do not need it.

---

## Local preview

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

## Deploying

Commit and push to `master`; GitHub Pages publishes automatically.

```bash
git add -A
git commit -m "Rebuild site around nanophotonics and plasmonics research"
git push origin master
```

---

© Md Kausar Hamid Miji. Banner and decorative graphics generated for this site.
