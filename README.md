# Lumina Support Site

Static support, privacy, and license pages for Lumina, an online collection game with a tarot / mystic theme. No build step and no dependencies: HTML files, one logo, and inline CSS/JS.

Repository: https://github.com/SimbioLabs/lumina-support

## Hosting

GitHub Pages serves `main` from the repository root. This repo has no Pages workflow. A push to `main` is what publishes.

The custom domain is the root [`CNAME`](./CNAME) file (`65b2492`). The file is one line: `support.lumina.cards`. DNS for that name is a CNAME to `simbiolabs.github.io`.

Checked 2026-10-29:

| URL | Response |
|-----|----------|
| `http://support.lumina.cards/` | **200** from GitHub Pages. Title is `Lumina - Suporte`. |
| `https://support.lumina.cards/` | TLS fails. The certificate subject is `CN=*.github.io` (SAN includes `*.github.io` and `github.io`). It does not include `support.lumina.cards`. |
| `https://simbiolabs.github.io/lumina-support/` | **301** to `http://support.lumina.cards/` (plain HTTP). |

`lumina-web` `src/components/site-footer.tsx` sets `SUPPORT` to `https://simbiolabs.github.io/lumina-support` on both `main` and `stage`. Terms, privacy, refunds, and the support home are that prefix plus `terms.html`, `privacy.html`, `refund.html`, and `/`. A click follows the 301 onto `http://support.lumina.cards/`.

Links inside these HTML files are relative (`terms.html`, `privacy.html`, `refund.html`), so they stay on the host that loaded the page.

Re-check before changing the footer:

```bash
curl -sI http://support.lumina.cards/
curl -sI https://simbiolabs.github.io/lumina-support/
curl -svI https://support.lumina.cards/
```

The third command is the handshake. When that certificate lists `support.lumina.cards` and a browser accepts `https://support.lumina.cards/`, the footer can use the custom domain. Until then the `github.io` HTTPS URL is a redirect onto HTTP.

## Pages

| File | Purpose |
|------|---------|
| `index.html` | FAQ, contact, about, language toggle |
| `terms.html` | Terms of Service (website + app, Paddle as Merchant of Record) |
| `privacy.html` | Privacy Policy (PT / EN / ES, LGPD/GDPR) |
| `refund.html` | 30-day refund policy for web (Paddle) and store purchases |
| `license.html` | End User License Agreement (app stores) |
| `app_icon.png` | Circular brand brooch (512×512 RGBA) used as favicon and header mark |

Each page links the others in the footer. Contact is
`feedback@simbiolabs.com.br`.

## Languages

All three pages ship Portuguese, English, and Spanish in the same file.

- Visible copy is wrapped in `.lang-pt`, `.lang-en`, or `.lang-es`.
- Default render is Portuguese (`<html lang="pt-BR">`, EN/ES start `.hidden`).
- `setLanguage(lang)` toggles `.hidden`, marks the active button, and stores
  `lumina-lang` in `localStorage`.
- On load, a saved `pt` / `en` / `es` value is reapplied by clicking the
  matching language button.

There is no framework i18n. Adding a sentence means adding three sibling
`<span>` / `<p>` / `<div>` nodes.

The header mark is the circular brand brooch (`app_icon.png`): dark-purple coin, skeletal hand holding one purple/gold card back, transparent outside. Replace that file with the same shipped brooch; do not invent a second design or clip the PNG to a squircle.

## Editing the FAQ

FAQ items live in `index.html` as repeated `.faq-item` blocks, one block per
language column (the PT, EN, and ES FAQ lists are separate, not one item with
three spans).

When you add a question:

1. Add the item to the Portuguese list, the English list, and the Spanish list.
2. Keep the three lists in the same order.
3. Do not introduce a new language without also updating `privacy.html`,
   `license.html`, the toggle buttons, and the `localStorage` allow-list
   `['pt', 'en', 'es']`.

Theme colors are CSS variables at the top of each file (`--twilight-shadow`,
`--amethyst-glow`, `--virtue-ember`, …). Change them in all three pages if you
retint the site.

## Local preview

```bash
cd lumina-support
python3 -m http.server 8080
# open http://127.0.0.1:8080/
```

Confirm language toggle, footer links between the three pages, and the mailto
button. There is no automated test suite.

## Deploy

Push to `main`. GitHub Pages publishes the repository root on the host in [Hosting](#hosting). The `CNAME` file is the custom domain.

Do not add a bundler, environment file, or backend call to these pages. They
are public legal/support content and must stay static.
