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

## Features

- Dark mystical theme matching Lumina app
- Multi-language support (Portuguese, English, Spanish)
- Contact email link
- FAQ section
- Responsive design for mobile
- No dependencies, pure HTML/CSS/JS

## Customization

Edit `index.html` to:
- Update contact email
- Add/modify FAQ items
- Change branding colors (CSS variables at top)

---

Built for Simbio Labs
