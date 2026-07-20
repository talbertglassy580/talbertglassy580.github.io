# Tommy Y.C. Wong — Personal Academic Website

A static site with a single source of truth: **all content lives in `content.md`**.
`index.html` is a small viewer that fetches that file and renders it. To change
anything on the site, edit `content.md` — you never need to touch HTML.

## Structure

```
content.md          ALL website content, in structured Markdown  ← edit this
index.html          The viewer (parses content.md, builds tabs, renders pages)
css/style.css       All styling (colors, fonts, layout)
images/             Profile photo (currently a placeholder SVG)
files/              PDFs served from the site (papers, CV, slides, journal issues)
```

## Editing content.md

- Every `# Heading` (single `#`) becomes a **tab** in the navigation.
- `## Heading` is a section inside a tab; `### Heading` a sub-heading (years, project titles).
- Quote blocks (lines starting with `>`) render as bordered **cards** — use them
  for publications and talks.
- Any link pointing into `files/` renders as a **download button**, e.g.
  `[PDF](files/wong-2026-paper.pdf)`.
- Everything else is ordinary Markdown.

To add a paper: drop the PDF into `files/`, then add a quote block under the right
heading in `content.md` with a `[PDF](files/…)` link. Same idea for the CV and
edited journal issues — PDFs always live in `files/` as separate files; the
Markdown links to them.

## Replacing the placeholders

- Anything marked `[Placeholder]` in `content.md` is meant to be rewritten.
- Every PDF in `files/` is a one-page dummy — replace with your real files.
- Replace `images/profile.svg` with a real photo (e.g. `images/profile.jpg`,
  then update the `<img class="portrait">` line at the top of `content.md`).
- The `Google Scholar`, `ORCID`, and `GitHub` links point to `#` — fill in your URLs.

## Previewing locally

Browsers block `fetch` from `file://` pages, so serve the folder over HTTP:

```sh
cd "/Users/wyc.t/Work/HKBU PhD/Persoanl Website"
python3 -m http.server 8000
# open http://localhost:8000/
```

## Deploying to GitHub Pages

1. Create a GitHub repository named `<your-username>.github.io` (public).
2. In this folder:
   ```sh
   git init
   git add .
   git commit -m "Initial site"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<your-username>.github.io.git
   git push -u origin main
   ```
3. On GitHub: Settings → Pages → confirm source is the `main` branch, root folder.
4. The site goes live at `https://<your-username>.github.io/` within a minute or two.

Updating the site later = edit `content.md` (or drop a PDF into `files/`),
commit, push.

## Custom domain (optional)

Buy a domain, add a `CNAME` file containing the domain name to this folder, and set
the DNS records per GitHub's docs (Settings → Pages → Custom domain).
