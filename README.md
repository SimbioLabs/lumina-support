# Lumina Support Site

Static support, privacy, and license pages for Lumina, an online collection game with a tarot / mystic theme. No build step and no dependencies: HTML files, one logo, and inline CSS/JS.

Repository: https://github.com/SimbioLabs/lumina-support

GitHub Pages serves `main` at the repository root:

```text
https://simbiolabs.github.io/lumina-support/
```

## Pages

| File | Purpose |
|------|---------|
| `index.html` | FAQ, contact, about, language toggle |
| `terms.html` | Terms of Service (website + app, Paddle as Merchant of Record) |
| `privacy.html` | Privacy Policy (PT / EN / ES, LGPD/GDPR) |
| `refund.html` | 30-day refund policy for web (Paddle) and store purchases |
| `license.html` | End User License Agreement (app stores) |
| `app_icon.png` | Circular app logo used in the header |

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

The header mark is the generated circular button (`app_icon.png`). To change the art, replace `lumina-web/public/brand/logo.png` (cream square) and run `npm run icons` there.

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

Push to `main`. GitHub Pages serves the repository root.

Do not add a bundler, environment file, or backend call to these pages. They
are public legal/support content and must stay static.
