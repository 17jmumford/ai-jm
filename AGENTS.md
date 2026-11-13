# AGENTS.md

Single-screen landing page for [ai-jm.com](https://ai-jm.com), served by GitHub Pages from `main`.

## Git workflow

- Always commit and push straight to `main`. Do not create feature branches or open pull requests.
- Every push to `main` deploys to production via `.github/workflows/pages.yml`, so verify before pushing.

## Layout

- `index.html` is the whole site. Styles are inline in a `<style>` block; there is no build step or JavaScript.
- `favicon.svg` is the only other asset.

## Verify before pushing

Run the same checks CI runs:

```sh
test -f index.html && test ! -f 404.html \
  && grep -q 'mailto:bookings@ai-jm.com' index.html \
  && grep -q 'Book now' index.html \
  && grep -q 'overflow: hidden' index.html \
  && echo OK
```

Preview locally with `python3 -m http.server 8000` and check desktop, mobile portrait, and mobile landscape. The page must fit one screen with no scrolling.
