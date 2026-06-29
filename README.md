# Nic's Birthday

A single static page, built to match the Figma design at **iPhone 15 Pro width (393px)**. It presents the restaurant booking as a Jay Rayner–style review of *Other* in Bristol — a full-bleed hero photo, headline, byline and intro, then alternating food photos and review paragraphs on a white page.

No build step, no framework. Just `index.html`, the photos in `assets/`, and fonts loaded from Google Fonts (Playfair Display + Source Serif Pro).

## Files

```
index.html        the page
assets/            the six photos (JPEG)
netlify.toml       publishes the repo root, caches photos
.gitignore
```

## Preview locally

Open `index.html` in a browser. For an exact phone view, open your browser's device toolbar (in Chrome: ⌘+⌥+I → the phone icon) and pick **iPhone 15 Pro**. The page is centred in a 393px column; on a real phone it fills the screen.

If you want to serve it locally over http (so fonts/caching behave like production):

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Put it on GitHub

```bash
cd nics-birthday
git init
git add .
git commit -m "Nic's birthday page"
# create an EMPTY repo on github.com first (no README), then:
git remote add origin https://github.com/<your-username>/<repo-name>.git
git branch -M main
git push -u origin main
```

## Deploy on Netlify

**Option A — connect the GitHub repo (auto-deploys on every push):**
1. Log in to Netlify → **Add new site** → **Import an existing project**.
2. Choose **GitHub** and pick the repo you just pushed.
3. Leave the build command empty and set **Publish directory** to `.` (the repo root). `netlify.toml` already specifies this.
4. **Deploy**. You'll get a `*.netlify.app` URL you can send to her.

**Option B — drag and drop (no GitHub needed):**
1. Netlify dashboard → **Sites** → drag the whole `nics-birthday` folder onto the upload area.
2. Done — it's live.

To use a custom domain, add it under **Domain settings** on the site.

## Editing later

- **Text**: it's all in `index.html`, in plain `<p>` tags — edit directly.
- **Photos**: replace the files in `assets/` (keep the same filenames), or change the `src` paths. Heights are fixed in the CSS (`.hero` 326px, `.photo.wide` 314px, `.photo.tall` 699px) with `object-fit: cover`.
- **Type / spacing**: all in the `<style>` block at the top of `index.html`.
