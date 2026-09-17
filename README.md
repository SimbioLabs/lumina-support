# Lumina Support Page

Simple support page for the Lumina tarot reading app.

## Deploying to GitHub Pages

1. Create a new repository on GitHub (e.g., `lumina-support`)

2. Push this code:
   ```bash
   cd ~/SimbioLabs/lumina-support
   git init
   git add .
   git commit -m "Initial commit: Lumina support page"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/lumina-support.git
   git push -u origin main
   ```

3. Enable GitHub Pages:
   - Go to repository Settings → Pages
   - Source: Deploy from a branch
   - Branch: `main` / `root`
   - Click Save

4. Your page will be available at:
   - `https://YOUR_USERNAME.github.io/lumina-support`
   - Or configure a custom domain

## Pages

- **index.html** - Main support page with FAQ
- **terms.html** - Terms of Service (website + app, Paddle as Merchant of Record)
- **privacy.html** - Privacy Policy (LGPD/GDPR)
- **refund.html** - 30-day refund policy for web (Paddle) and store purchases
- **license.html** - End User License Agreement (app stores)

## Features

- Dark mystical theme matching Lumina app
- Multi-language support (Portuguese, English, Spanish)
- Contact email link
- Comprehensive FAQ section
- Privacy Policy with data protection info
- License Agreement covering IAP terms and conditions
- Cross-linked navigation between pages
- Responsive design for mobile
- No dependencies, pure HTML/CSS/JS

## Customization

Edit `index.html` to:
- Update contact email
- Add/modify FAQ items
- Change branding colors (CSS variables at top)

The header mark is the generated app icon (`app_icon.png`), clipped to a squircle in CSS. To change the art, replace `lumina-web/public/brand/logo.png` and run `npm run icons` there.

---

Built for Simbio Labs
