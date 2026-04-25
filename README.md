# Taku Harbor — Static Website

Historical and natural history resource for Taku Harbor State Marine Park, southeast Alaska.

## Structure

```
taku-harbor/
├── index.html          # Landing page / overview
├── history.html        # Four eras of history with timeline
├── photos.html         # Photo gallery (drone + ground + illustration)
├── resources.html      # Sources, archives, further reading
├── css/
│   └── style.css       # Shared stylesheet
├── images/             # Put your photos here (see below)
├── docs/               # PDFs and downloadable documents
├── CNAME               # Your custom domain for GitHub Pages
└── .gitignore
```

## Adding Photos

1. Compress photos with [Squoosh](https://squoosh.app) — aim for under 400KB per image
2. Save to the `images/` folder (e.g. `images/drone-01.jpg`)
3. In `photos.html`, replace the placeholder `<div class="photo-item">` blocks with:

```html
<div class="photo-item">
  <a href="images/drone-01.jpg" class="glightbox" data-gallery="drone" data-description="Your caption here">
    <img src="images/drone-01.jpg" alt="Descriptive alt text" loading="lazy">
    <div class="photo-caption">Your caption here</div>
  </a>
</div>
```

The `glightbox` class enables the click-to-enlarge lightbox viewer automatically.

## Adding PDFs

Save PDFs to `docs/` and link from `resources.html`:

```html
<a href="docs/your-document.pdf" target="_blank">Document title</a>
```

## Deploying to GitHub Pages

1. Create a new GitHub repo (e.g. `taku-harbor`)
2. Push this folder to the repo:
   ```bash
   git init
   git add .
   git commit -m "Initial site"
   git remote add origin https://github.com/yourusername/taku-harbor.git
   git push -u origin main
   ```
3. In GitHub repo Settings → Pages → Source: deploy from `main` branch, `/ (root)` folder
4. Edit `CNAME` to contain your actual domain name (one line, no `https://`)
5. At your domain registrar, add a CNAME DNS record:
   - Name: `www` (or `@` for apex domain)
   - Value: `yourusername.github.io`
6. DNS propagation takes a few minutes to a few hours

## Fonts

The site uses Google Fonts (Playfair Display + Source Serif 4) loaded via CSS import. These load from Google's CDN — no local files needed. If you want fully self-hosted fonts for offline use, download them from [Google Fonts](https://fonts.google.com) and update the `@import` in `style.css`.
