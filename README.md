# Portfolio Voice Widget Host

This folder is the separate hosted widget project for the portfolio-only HeyNaj voice experience.

## Files

- `loader.js` - short bootstrap script pasted on the site
- `widget_embed.html` - full widget payload loaded by `loader.js`

## How it works

This host stays centralized, while the portfolio brain remains isolated through the Apps Script webhook URL.

Paste this snippet on the portfolio site:

```html
<script async src="https://YOUR-PAGES-DOMAIN/loader.js" data-heynaj-webhook="YOUR-PORTFOLIO-APPS-SCRIPT-EXEC"></script>
```

If the page already has a dedicated mount node, use:

```html
<script async src="https://YOUR-PAGES-DOMAIN/loader.js" data-heynaj-container="real-widget-container" data-heynaj-webhook="YOUR-PORTFOLIO-APPS-SCRIPT-EXEC"></script>
```

The loader:

1. downloads `widget_embed.html`
2. replaces the hardcoded `WEBHOOK_URL` inside it
3. injects the full widget into the site

## Portfolio voice additions

This version keeps the original chat UI and adds:

- a top-right phone action with hover text `Talk to AI`
- a dedicated voice screen with animated waveform visuals
- the existing speech-to-text plus TTS flow behind the new voice UI

## Deploy to Cloudflare Pages

1. Create a new GitHub repo for this folder only.
2. Push `loader.js`, `widget_embed.html`, and this `README.md`.
3. In Cloudflare Pages, create a new project from that repo.
4. Use the repo root as the static output.
5. After deploy, your install URL will look like:

```html
<script async src="https://YOUR-PORTFOLIO-WIDGET.pages.dev/loader.js" data-heynaj-container="real-widget-container" data-heynaj-webhook="YOUR-PORTFOLIO-APPS-SCRIPT-EXEC"></script>
```

## Why this stays isolated

The hosted files can be shared, but the portfolio brain is still separate because the snippet points to the portfolio webhook.

That means the portfolio keeps its own:

- knowledge base
- memory bank
- leads
- voice settings
- alerts
- branding choices
