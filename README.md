# caferbakac.github.io — Quarto site

Built in the same structure and styling as
[mustafaslancoto.github.io](https://github.com/mustafaslanCoto/mustafaslanCoto.github.io):
Quarto website, `cosmo` theme, the same `styles.css` / `index.css` / `publications.css`,
and the same GitHub Action that renders the site on push. Content is yours.

## Fill these in before publishing

Search the project for `REPLACE_ME` — there are four, all links:

| Where | What |
|---|---|
| `_quarto.yml` (navbar tools) | Google Scholar, LinkedIn URLs |
| `index.qmd` (about links) | the same two |

Also replace `images/profile.jpg` with a square headshot. The current file is a
placeholder with your initials.

## Publishing

The included workflow renders the site on GitHub and pushes the output to a `gh-pages`
branch — you never need Quarto installed locally.

1. Copy these files into your `caferbakac.github.io` repo, replacing the old Jekyll site:

   ```
   git rm -r --cached .
   # delete the old Jekyll files from the folder, copy these in, then:
   git add -A
   git commit -m "Replace Jekyll site with Quarto site"
   git push
   ```

2. The first push triggers the **Quarto Publish** action (see the Actions tab). It creates
   the `gh-pages` branch.
3. Repo **Settings → Pages → Build and deployment**: source = *Deploy from a branch*,
   branch = **gh-pages**, folder = **/ (root)**. Save.

After that, every push to `main` re-renders and redeploys automatically.

## Working locally (optional)

If you install [Quarto](https://quarto.org/docs/get-started/) you get live preview:

```
quarto preview      # opens a browser, reloads as you save
quarto render       # writes the site into docs/
```

Rendering is not required before pushing — the Action does it for you. `docs/` is not
committed here for that reason.

## Where content lives

| Page | File |
|---|---|
| Homepage / bio | `index.qmd` |
| Publications | `publications/index.qmd` |
| Talks (one file per talk) | `talks/presentations/*.qmd` |
| Workshops | `workshops/trainings/*.qmd` |
| Teaching | `teaching/index.qmd` |
| Blog posts | `blog/posts/*.qmd` |
| CV page + PDF | `CV/index.qmd`, `CV/Cafer-Bakac-CV.pdf` |
| Navbar, site title, social links | `_quarto.yml` |

### Adding a publication

In `publications/index.qmd`, copy a whole `<div class="pub-card"> … </div>` block and edit
it. If the paper has a DOI, put it in both `href` and `data-href` and the button links
straight to it. If not, leave `data-href=""` and write a short `data-msg` — clicking then
shows that message inline.

### Adding a talk, workshop, or blog post

Copy any existing file in the relevant folder, rename it, and edit the front matter
(`title`, `description`, `date`, `categories`). The listing page picks it up automatically
and sorts by date. Adding an `image:` field gives it a thumbnail in the listing — the
original site uses this heavily, and it does make the listings look better.

## Things to check

- **Talk dates are approximate.** The CV gives months for some presentations and only years
  for others. Where the day was unknown I used the first of the month, and where the month
  was unknown I used a plausible one. Dates drive listing order, so correct any that matter.
- **Three talks are listed as invited** (Stony Brook, Bamberg, Bilkent). The two R workshops
  are on the Workshops page instead.
- Same content corrections as before: the fear-motives paper is dated 2023 (its DOI and
  issue say 2023, the CV says 2022); "Psychological papital" → "capital"; "Manuel, L." →
  "London, M."; "Bemberg" → "Bamberg".
- The CSS files are taken from the original site. If you want to shift the palette, the
  teal is `#20808D` with `#20B8CD` on hover, defined at the top of `styles.css`.
