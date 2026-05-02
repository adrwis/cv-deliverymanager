# CV: Adriana Guściora · Delivery Manager (FinTech)

Standalone GitHub Pages site with bilingual (PL/EN) CV for the role of **Delivery Manager · Financial Services & FinTech**.

🌐 **Live**: https://adrwis.github.io/cv-deliverymanager/

## Features
- Bilingual (PL/EN) toggle
- Light / dark theme toggle
- Cert lightbox (PRINCE2, SQL, Power BI, Six Sigma, UX, Project Management, diplomas)
- Success stories per company
- Responsive (mobile + desktop)
- Print-friendly
- WCAG accessible (skip link, ARIA, keyboard navigation)

## Files
- `index.html`: main page (markup + i18n + JS)
- `cv-deliverymanager.css`: styling (light/dark variables, success-story block)
- `ada2.jpg`: header photo
- `edukacja/`: certificate images and PDFs (lightbox source)
- `.github/workflows/deploy.yml`: auto-deploy to GitHub Pages

## Deploy
Push to `main` → GitHub Actions deploys to Pages.

## Updates
Content lives in two places:
1. Inline HTML markup (default text)
2. JS `translations` object at the bottom of `index.html`

Keep both in sync when editing copy.
