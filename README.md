# teeendvn.github.io

Personal homepage of TeeEndVN, hosted on GitHub Pages at https://teeendvn.com/.

## Projects

- **Mojimo**: scan and learn Japanese from any app.
  [Landing page](https://mojimo.teeendvn.com/) ·
  [Get it on Google Play](https://play.google.com/store/apps/details?id=com.teeendvn.mojimo.prod)
- **Kitsunebi** (狐火): a fox spirit idle roguelite of a thousand torii gates.
  [Landing page](https://kitsunebi.teeendvn.com/) ·
  [Get it on Google Play](https://play.google.com/store/apps/details?id=com.teeendvn.kitsunebi.prod) ·
  [Play the free demo](https://kitsunebi.teeendvn.com/play/)

## Structure

- `index.html`: the homepage (plain HTML and CSS, no build step)
- `404.html`: shown for unknown paths (not indexed)
- `robots.txt`, `sitemap.xml`: crawler rules and the list of pages for search engines
- `assets/`: the avatar (`avatar.jpg`, plus `avatar-64.png` favicon and `avatar-180.png` touch icon), the Mojimo and Kitsunebi app icons, and the link preview image
- `.nojekyll`: GitHub Pages serves the files as they are

## Search and link previews

- `index.html` has a canonical URL, Open Graph and X (Twitter) tags, and JSON-LD for the person (with GitHub and X profiles), the website, Mojimo and Kitsunebi. Keep them in line with the page when it changes.
- Update `<lastmod>` in `sitemap.xml` when the page changes, and add any new page to it.
- `assets/og-image.jpg` (1200×630) is the link preview image, built from `assets/og-image.svg`. To regenerate it on macOS (Quick Look can't load the linked avatar, so the render copy embeds it):

  ```sh
  B64=$(base64 -i assets/avatar.jpg | tr -d '\n')
  sed -e '1s/height="630" viewBox="0 0 1200 630"/height="1200" viewBox="0 -285 1200 1200"/' \
      -e "s#href=\"avatar.jpg\" xlink:href=\"avatar.jpg\"#href=\"data:image/jpeg;base64,$B64\" xlink:href=\"data:image/jpeg;base64,$B64\"#" \
      assets/og-image.svg > /tmp/og-square.svg
  qlmanage -t -s 1200 -o /tmp /tmp/og-square.svg
  sips --cropToHeightWidth 630 1200 /tmp/og-square.svg.png -s format jpeg -s formatOptions 90 --out assets/og-image.jpg
  ```

- Search Console covers the whole `teeendvn.com` domain (DNS TXT record). Submit `https://teeendvn.com/sitemap.xml` there.

## Deploy

GitHub Pages publishes the root of `main` automatically. Push to `main` and the
site updates within a minute or two.

## Local preview

```bash
python3 -m http.server 8000
```

Then open http://localhost:8000.
