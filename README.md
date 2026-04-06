# Survey Randomizer

A lightweight static web page that takes multiple Google Survey (or any) URLs and generates a single shareable link. Anyone who visits that link is instantly and randomly redirected to one of the surveys — no server, no database, no tracking.

## How it works

The generated link encodes all your survey URLs directly in its query string as a Base64-encoded JSON array:

```
https://laurent-clouet.fr/google-forms-randomizer/?links=BASE64_ENCODED_URLS
```

When a respondent visits the link, JavaScript in the page decodes the URLs, picks one at random, and calls `window.location.replace()` before the page even renders. The respondent sees no UI — just a brief loading spinner.

## Usage

### As a creator

1. Open [laurent-clouet.fr/google-forms-randomizer](https://laurent-clouet.fr/google-forms-randomizer/)
2. Paste 2–10 survey URLs into the input fields
3. Click **Generate link**
4. Copy the generated link and share it

### As a respondent

Just open the link — you'll be redirected to one of the surveys instantly.

## Features

- **No server or database** — all data lives in the URL itself
- **No flash** — redirect fires before the page renders
- **Equal probability** — each survey has the same chance of being selected
- **Handles up to 10 URLs** — with a warning if the generated link exceeds 2,000 characters
- **Validates inputs** — highlights invalid URLs before generating
- **One-click copy** — clipboard API

## Live page

[https://laurent-clouet.fr/google-forms-randomizer/](https://laurent-clouet.fr/google-forms-randomizer/)

## Project structure

```
index.html        — single self-contained page (CSS and JS inlined)
404.html          — error page
favicon.ico       — multi-size favicon (16, 32, 48px)
icon.png          — 192×192 icon for web manifest
icon.svg          — SVG icon
img/logo.png      — logo displayed on the page
site.webmanifest  — PWA manifest
robots.txt        — allow all crawlers
```

## Local development

No build step needed. Serve the files with any static server:

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000`.
