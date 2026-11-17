# best-homepage

A motion-rich personal homepage for Best (Nutthakit Senphoklang). Static, zero build step,
deployable to GitLab Pages. Doubles as the homepage + privacy policy for publishing the
`nutthakit-space` OAuth app to Production.

## Preview locally
```bash
cd public
python3 -m http.server 8080
# open http://localhost:8080
```

## Deploy to GitLab Pages
1. Create a GitLab project (you'll provide access).
2. Push this folder:
   ```bash
   git init && git add -A && git commit -m "feat: motion homepage"
   git remote add origin <your-gitlab-repo-url>
   git push -u origin main
   ```
3. `.gitlab-ci.yml` runs a `pages` job that publishes `public/`.
4. Settings → Pages shows the live URL after the first pipeline.

No build step — `public/` is the site. Edit `public/index.html` directly.

## Motion stack
- **GSAP 3.13 + ScrollTrigger + SplitText** (all free) — scroll reveals, hero line-rise,
  manifesto word-by-word scrub, progress bar, hero parallax.
- **Lenis** — momentum smooth scroll, wired to ScrollTrigger.
- **Custom WebGL fragment shader** — animated fbm gradient hero with mouse parallax + grain
  (no three.js; raw WebGL, falls back to a CSS gradient if unavailable).
- Custom cursor, magnetic buttons, pointer-follow glow on the role cards.
- Honors `prefers-reduced-motion` (static, no smooth-scroll, cursor off).

All libs load from jsDelivr CDN — no bundler, no node_modules.

## Sections
hero → skills marquee → manifesto → **What I do** (Tech Lead /
Technical PM / Full-stack Developer) → **Collaborate** ("consider me" + GitHub CTA) →
contact, plus a privacy policy page.

## Content to edit
- Contact email `hello@example.com` is a placeholder — set a real one.
- GitHub links point to https://github.com/nutthakitSen (real).
- `privacy.html` contact + entity name (review before OAuth publish).

## Files
- `public/index.html` — the homepage (single file, inline CSS/JS).
- `public/privacy.html` — privacy policy for the OAuth consent screen.
- `.gitlab-ci.yml` — GitLab Pages deploy.
