# Srijith Balan: website source

Built with [Quarto](https://quarto.org), published on GitHub Pages.

## Weekend 1: get it live (about 2–3 hours)

### 1. Install the tools (once)
- **Quarto**: download the installer from https://quarto.org/docs/get-started/
- **Git**: https://git-scm.com/downloads (or GitHub Desktop if you prefer clicking)
- An editor: VS Code with the Quarto extension, or RStudio/Positron.

### 2. Preview locally
Unzip this folder, open a terminal in it, and run:

    quarto preview

Your browser opens the site and reloads as you edit.

### 3. Put it on GitHub
1. On GitHub, create a new **public** repository named exactly `rook-prog.github.io`. Don’t add a README.
2. In the project folder:

        git init
        git add .
        git commit -m "First version of the site"
        git branch -M main
        git remote add origin https://github.com/rook-prog/rook-prog.github.io.git
        git push -u origin main

### 4. Publish

    quarto publish gh-pages

This renders the site and pushes it to a `gh-pages` branch. Then on GitHub: **Settings → Pages → Source: Deploy from a branch → `gh-pages` / root**. The site appears at `https://rook-prog.github.io/` within a few minutes.

Every later update is the same command: `quarto publish gh-pages` (and `git push` to keep the source backed up).

## Weekend 1 or 2: your own domain

1. Buy the domain (e.g. srijithbalan.com or .in) from any registrar.
2. Create a file named `CNAME` (no extension) in this folder containing only your domain, e.g. `srijithbalan.com`.
3. At your registrar’s DNS settings, add the GitHub Pages records. Check the current values in GitHub’s docs (“Managing a custom domain for your GitHub Pages site”); at the time of writing they are four A records for the bare domain (185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.153) and a CNAME for `www` pointing to `rook-prog.github.io`.
4. Update `site-url` in `_quarto.yml`, run `quarto publish gh-pages`, then tick **Enforce HTTPS** under Settings → Pages once it’s available.

## Weekend 3: comments and newsletter

**Comments (giscus).** On your repo: Settings → General → Features → tick **Discussions**. In the Discussions tab, create a category called `Explorations` (Announcement type keeps the category for comments only). Install the giscus app from https://github.com/apps/giscus on that repo. Then in `gisventure/_metadata.yml`, remove the leading `# ` from the comments block (the repo name is already set).

**Newsletter (Buttondown).** Create an account at https://buttondown.com (it has a free tier; check current limits). Replace `YOUR-BUTTONDOWN-USERNAME` in `index.qmd`. Check that their embed form address still matches; their settings page shows the current snippet.

## Placeholders to fill (search the project for these)
- `YOUR-BUTTONDOWN-USERNAME` in `index.qmd` (newsletter block, currently hidden)
- Items styled as `{.todo}` show in amber on the site; none are left at the moment

## Adding a new exploration (about 30–60 minutes beyond writing)
1. Copy `_exploration-template/` into `gisventure/` and rename it, e.g. `gisventure/sabarmati-ndwi/`.
2. Put your figures in that folder and fill in the front matter, including `shows` and `notshown`.
3. `quarto preview` to check, then `quarto publish gh-pages`.
4. Post a shorter version on LinkedIn linking back to the page.

You can also write an exploration directly as a Jupyter notebook (`index.ipynb`) with the same front matter in a first raw cell; Quarto renders it the same way.

## Structure

    _quarto.yml               site settings, navigation, theme
    styles/theme.scss         colours, type, the "Shows / Doesn’t show" styling
    styles/dark.scss          dark-mode colours
    _ejs/explorations.ejs     listing layout used on home and GISVENTURE pages
    index.qmd                 homepage
    gisventure/               explorations (one folder each) + comments config
    research.qmd projects.qmd mentoring.qmd about.qmd
    _exploration-template/    copy this for new posts (ignored by Quarto)
    images/  files/
