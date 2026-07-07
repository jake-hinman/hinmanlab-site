# Maintaining the site

The whole point of this setup: **you don't hand-edit HTML.** You tell Claude Code what changed, it
edits the files, commits, and pushes. GitHub Pages redeploys automatically (~1 minute). This file
documents the common updates so anyone (including Claude) can make them quickly.

## The update loop

1. Tell Claude what changed (e.g. "add a new grad student named …", "we published a new paper …").
2. Claude edits the relevant `.html` file.
3. Commit and push:
   ```
   git add -A
   git commit -m "Update people: add …"
   git push
   ```
4. Wait ~1 minute; the live site updates.

## Adding a member photo

Photos live in `assets/img/people/` and are named `firstname-lastname.jpg` (all lowercase,
hyphenated). Each person's card already points at their expected filename. Until a photo file
exists, the card shows a clean initials placeholder automatically — **no code change is needed to
add a photo. Just drop the correctly named file into `assets/img/people/` and commit.**

Examples of expected filenames:
- `jake-hinman.jpg`
- `yadong-dai.jpg`
- `becky-burch.jpg`
- `md-rashed-al-mahfuz.jpg`
- `kaylyn-castillo.jpg`

Square images look best (they're cropped to a square). ~600×600px JPG is plenty.

To find the exact filename a card expects, open `people.html` and look at that person's
`<img ... src="assets/img/people/NAME.jpg">`.

## Adding / removing a lab member

Edit `people.html`. Copy an existing `.person` block within the right section
(Principal Investigator / Graduate Students / Undergraduate Students), change the name, role,
detail, the `src` filename, and the `data-initials`. To move someone to Alumni, cut their block
and add a line to the `.alumni-list`.

## Adding a publication

Edit `publications.html`. Find (or add) the `<h2 class="pub-year">` for the year, then copy an
existing `<li class="pub">` block. Fill in:
- authors (wrap `Hinman JR` in `<strong>…</strong>`),
- title, venue,
- the PubMed link, and
- the PDF link.

For a hosted PDF, save the file into `assets/pdf/` (a short name like `lastname_journal_year.pdf`)
and point the PDF link at `assets/pdf/that-file.pdf`. If there's no PDF, leave the `<span
class="links">` with only the PubMed link (or empty for book chapters).

## Editing research descriptions

Edit `research.html`. Each research area is a `<section class="area">` with a heading, a narrative
paragraph, and a `.projlist` of current projects. Edit the text directly.

## Changing colors / design

All styling is in `styles.css`. The palette is defined once at the top under `:root`
(`--ink` = Illini blue, `--accent` = Illini orange). Change those variables to re-theme the
whole site.
