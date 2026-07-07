# Hinman Lab website

Static HTML/CSS site for the Hinman Lab (Department of Psychology, University of Illinois
Urbana-Champaign), hosted on GitHub Pages. No build step, no frameworks, no external dependencies —
just HTML, one stylesheet, and static assets.

## Structure

```
index.html          Home
research.html        Research areas
people.html          Roster (PI, grad students, undergrads, alumni)
publications.html    Publications by year, with PubMed + PDF links
contact.html         Contact info
styles.css           Shared stylesheet (all pages)
assets/
  img/               Logo + research figures
  img/people/        Member photos (firstname-lastname.jpg) — see MAINTAINING.md
  pdf/               Publication PDFs + CV
CNAME                Custom domain (hinmanlab.org)
.nojekyll            Tells GitHub Pages to serve files as-is
```

## Preview locally

From this folder:

```
python -m http.server 8000
```

then open <http://localhost:8000>.

## Updating

See **MAINTAINING.md** — the intended workflow is to tell Claude Code what changed and let it edit
the HTML, then commit and push. GitHub Pages redeploys automatically in about a minute.
