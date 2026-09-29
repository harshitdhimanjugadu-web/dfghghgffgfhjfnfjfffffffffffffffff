# SYAHI FILMS website

Static site for GitHub Pages. No build step.

## Structure
- `index.html` main page, `offline.html` offline fallback, `sw.js` service worker, `manifest.webmanifest`
- `css/style.css` all styles. `js/config.js` **all settings**, `js/effects.js` animations, `js/app.js` portfolio, form, analytics
- `data/content.json` portfolio and all real content. `legal/` policy pages. `tools/` helper scripts
- `assets/img/` (put `logo.png` here), `assets/video/` (put videos here)

## Before launch (required)
1. Copy `logo.png` to `assets/img/`, then run `tools/make-icons.sh` (creates PWA icons).
2. Compress each video: `tools/compress-videos.sh file.mp4 name`. Then edit `data/content.json`: real title, category, poster (`assets/img/name.jpg`), video (`assets/video/name.mp4`), optional `webm`, description, client, year, tools. Categories: reels, youtube, shorts, motion, amv, commercial, typography, thumbnails. Thumbnail projects can use `"image"` instead of `"video"`.
3. Inquiry form storage: create a free Formspree or Web3Forms form and put its URL/key in `form` inside `config.js`. Submissions then arrive in your email and that service's dashboard. Empty = form opens WhatsApp instead. File upload needs a paid plan on those services: set `allowUpload:true` only if yours supports it.
4. Analytics (optional): set `analytics` in `config.js` (Plausible or GoatCounter). Off by default, honors Do Not Track.
5. Legal pages: fill every `[bracket]` and have them reviewed by a legal professional.
6. Real content only: add testimonials, case studies, team, about, and verified stats to `content.json`. Empty sections stay hidden.
7. Update `budgets` in `config.js` to your real pricing.

## Keep in sync
Email and phone numbers live in `config.js`. The JSON-LD block in `index.html` also holds them, so update it if they change.

## Notes
- If you use a custom domain, update canonical/OG URLs, `sitemap.xml`, `robots.txt` and `config.js`. On a `github.io/repo` path, search engines only read `robots.txt` at the domain root, so submit `sitemap.xml` in Google Search Console instead.
- Content-Security-Policy is in the `<meta>` tag. If you use another form/analytics host, add it to `connect-src`.
- Lenis loads from jsDelivr. For strict security, download it into `js/` and change the script tag.
