# LANCA website

Source for the LANCA research group website at [lanca-asu.github.io](https://lanca-asu.github.io).

Built with [Jekyll](https://jekyllrb.com/), hosted on GitHub Pages, no build server needed — GitHub builds and deploys it automatically when you push to `main`.

---

## One-time setup

### Step 1 — Create the GitHub organization

1. Go to https://github.com/account/organizations/new
2. Pick the free plan
3. Name the organization `lanca-asu`
4. This gives you the URL `lanca-asu.github.io` for free

### Step 2 — Create the repository

1. In the new `lanca-asu` organization, create a new repository
2. Name it exactly: `lanca-asu.github.io` (the name must match the organization for GitHub Pages to serve at the root URL)
3. Make it Public
4. Don't initialize with a README — you'll push these files instead

### Step 3 — Push this code

From a terminal in this folder:

```bash
git init
git add .
git commit -m "Initial site"
git branch -M main
git remote add origin https://github.com/lanca-asu/lanca-asu.github.io.git
git push -u origin main
```

### Step 4 — Turn on GitHub Pages

1. Go to your repo on github.com
2. Settings → Pages
3. Source: **Deploy from a branch**
4. Branch: **main**, folder: **/ (root)**
5. Save

Within ~2 minutes, the site will be live at `https://lanca-asu.github.io`.

---

## How to edit

### Edit on github.com (easiest, for small changes)

For one-line edits — adding a news item, fixing a typo, updating a person's affiliation — just edit on github.com:

1. Navigate to the file in the repo
2. Click the pencil icon
3. Make changes
4. "Commit changes" at the bottom
5. Site rebuilds in ~1 minute

### Edit locally (for bigger changes)

Install Ruby (if you don't have it), then:

```bash
cd lanca-site
bundle install        # one-time, installs Jekyll
bundle exec jekyll serve
```

Open http://localhost:4000 to preview. Edit files, save, the browser auto-reloads.

When you're happy:

```bash
git add .
git commit -m "Describe what you changed"
git push
```

---

## Common edits

### Add a news item

Create a new file in `_news/` named like `YYYY-MM-DD-short-slug.md`:

```markdown
---
date: 2025-11-20
---
Short news content here. *Italics* and **bold** work. [Links work too](https://example.com).
```

The homepage shows the 5 most recent automatically.

### Add a publication

Edit `_pages/publications.html`. Find the appropriate year section and add a new `<li class="pub">` block following the existing pattern. Wrap group-member names in `<strong>` to bold them.

If you're adding a paper from a new year, copy a whole `<section class="pub-section">` block.

### Add a person

Edit `_pages/people.html`. Add a new `<div class="person">` block in the appropriate grid:

```html
<div class="person">
  <div class="person-photo-placeholder">XY</div>
  <p class="person-name">Person Name</p>
  <p class="person-role">Role</p>
</div>
```

For real photos: drop a square image into `assets/img/people/`, then replace the placeholder with:

```html
<img src="/assets/img/people/their-photo.jpg" alt="Their Name" class="person-photo">
```

### Add a Glasgow alum (or update one's current position)

Edit `_pages/people.html`. Find the appropriate `alumni-list` and add or modify an `alumni-item`:

```html
<li class="alumni-item">
  <div class="alumni-name">
    Person Name
    <span>PhD, Glasgow</span>
  </div>
  <div class="alumni-current">Current position</div>
</li>
```

### Update site-wide info (your email, office, profile links)

Edit `_config.yml`, the `pi:` section near the top.

### Change the maroon accent color

Edit `assets/css/main.css`, find `--color-accent` near the top.

---

## File structure

```
lanca-site/
├── _config.yml              # Site settings, your contact info
├── Gemfile                  # Jekyll dependencies
├── index.html               # Homepage
├── _layouts/
│   └── default.html         # Master template every page uses
├── _includes/
│   ├── header.html          # Top nav
│   └── footer.html          # Footer
├── _pages/
│   ├── research.html
│   ├── people.html          # Current members + Glasgow alumni
│   ├── publications.html    # Organized by year
│   ├── teaching.html
│   └── join.html
├── _news/
│   └── YYYY-MM-DD-*.md      # One file per news item
└── assets/
    ├── css/main.css         # All styling
    └── img/                 # Photos go here
```

That's the whole thing. ~12 files total.

---

## What to add when you can

- **Photos** of you and the PhD students in `assets/img/people/`, then update `_pages/people.html` to use them instead of the placeholder initials
- **Google Scholar URL** in `_config.yml` under `pi:`
- **GitHub username** in `_config.yml` if you have a personal or lab GitHub
- **Link to the official ASU lab site** once Fulton Engineering provisions it — add it to the footer
- **A favicon** — drop `favicon.ico` in the root directory

---

## Notes

- The maroon accent color matches ASU's brand (`#8C1D40`). To use a different color, change `--color-accent` in `assets/css/main.css`.
- The site uses no JavaScript — pure HTML/CSS for fast loads and zero maintenance burden.
- All pages are responsive and work on mobile.
- SEO meta tags, sitemap, and RSS feed are generated automatically.
