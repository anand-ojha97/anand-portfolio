# Anand Ojha — Portfolio

A premium, dark-mode, single-page portfolio for **Anand Ojha**, WordPress Developer.
Built with plain HTML5, CSS3, and vanilla JavaScript — no framework, no backend, no build step.

**Design concept:** the site is staged like a code editor. The hero is a mock VS Code
window with a live "developer" JS object, and the experience section is rendered as a
`git log`, both because that's the medium a WordPress developer actually works in.

## Tech stack

- HTML5 / CSS3 / Vanilla JavaScript
- [Bootstrap 5](https://getbootstrap.com/) — grid & utilities
- [AOS](https://michalsnik.github.io/aos/) — scroll reveal animations
- [GSAP](https://gsap.com/) + ScrollTrigger — parallax & entrance sequencing
- [Typed.js](https://github.com/mattboldt/typed.js/) — rotating role text in the hero
- [Font Awesome 6](https://fontawesome.com/) — icons
- Google Fonts: Space Grotesk (display), Inter (body), JetBrains Mono (code/labels)

All libraries load from CDN, so there is nothing to install locally.

## Folder structure

```
portfolio/
├── index.html
├── css/
│   ├── style.css          # design tokens + all component styles
│   └── responsive.css     # breakpoints (desktop / laptop / tablet / mobile)
├── js/
│   ├── app.js              # nav, preloader, contact form, Typed.js init
│   └── animation.js        # AOS/GSAP setup, counters, tilt effects
├── assets/
│   ├── images/
│   └── icons/
├── resume/
│   ├── resume.pdf           # generated from the resume data below
│   └── build_resume.py      # regenerate resume.pdf (requires `pip install reportlab`)
├── robots.txt
├── sitemap.xml
└── README.md
```

## Running locally

No build step is required. Either:

1. Open `index.html` directly in a browser, **or**
2. Serve it locally for accurate relative-path behavior:
   ```bash
   cd portfolio
   python3 -m http.server 8000
   # visit http://localhost:8000
   ```

## Customization

- **Colors / type / spacing** — all design tokens live at the top of `css/style.css` under `:root`.
  Change `--bg`, `--accent`, `--accent-2`, fonts, or radii there to re-theme the whole site.
- **Copy** — all section text lives directly in `index.html`; no CMS or JSON layer.
- **Projects** — duplicate a `.project-card` block inside `#projects` and edit the icon, title,
  description, tags, and links.
- **Resume** — edit `resume/build_resume.py` and re-run `python3 build_resume.py` to regenerate
  `resume.pdf`, or simply replace the file with your own PDF export.
- **Contact form** — the form currently opens the visitor's email client via a `mailto:` link
  (see `js/app.js`). Swap this out for a real form backend such as
  [Formspree](https://formspree.io/) or [EmailJS](https://www.emailjs.com/) if you want
  submissions delivered without opening a mail client.
- **Domain** — update the canonical URL, Open Graph URLs, and the `Sitemap:` line in
  `robots.txt` / `sitemap.xml` once you have a real domain.

## Deployment — GitHub Pages

1. **Initialize git and make the first commit**
   ```bash
   cd portfolio
   git init
   git add .
   git commit -m "Initial Portfolio"
   ```

2. **Create the GitHub repository** (via [github.com/new](https://github.com/new)), name it
   `anand-portfolio`, and leave it empty (no README/license, since you already have one).

3. **Connect and push**
   ```bash
   git branch -M main
   git remote add origin https://github.com/<your-username>/anand-portfolio.git
   git push -u origin main
   ```

4. **Enable GitHub Pages**
   - Open the repository on GitHub → **Settings** → **Pages**.
   - Under **Build and deployment → Source**, choose **Deploy from a branch**.
   - Set **Branch** to `main` and folder to `/ (root)`, then **Save**.
   - After a minute or two, your site will be live at:
     `https://<your-username>.github.io/anand-portfolio/`

5. **(Optional) Custom domain** — under the same Pages settings, add your domain in the
   **Custom domain** field, then point a `CNAME` record from your DNS provider at
   `<your-username>.github.io`. Update `robots.txt`, `sitemap.xml`, and the canonical/Open
   Graph URLs in `index.html` to match.

## Accessibility & performance notes

- Respects `prefers-reduced-motion` — animations are disabled for users who request it.
- All interactive elements have visible keyboard focus states.
- Semantic HTML landmarks (`header`, `nav`, `section`, `footer`) throughout.
- Images use `alt`-ready markup; add descriptive `alt` text once real project screenshots
  replace the icon placeholders in `assets/images/`.
- Fonts and libraries load from CDN with `display=swap` to avoid blocking text render.
