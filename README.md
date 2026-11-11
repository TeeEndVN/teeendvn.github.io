# teeendvn.github.io

Personal homepage of TeeEndVN, hosted on GitHub Pages at https://teeendvn.com/.

## Projects

- **Mojimo**: scan and learn Japanese from any app.
  [Landing page](https://mojimo.teeendvn.com/) ·
  [Get it on Google Play](https://play.google.com/store/apps/details?id=com.teeendvn.mojimo.prod)

## Structure

- `index.html`: the homepage (plain HTML and CSS, no build step)
- `assets/`: images, including the Mojimo app icon and favicon

## Deploy

GitHub Pages publishes the root of `main` automatically. Push to `main` and the
site updates within a minute or two.

## Local preview

```bash
python3 -m http.server 8000
```

Then open http://localhost:8000.
