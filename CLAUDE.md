# CLAUDE.md — AI Assistant Guide

## Project Overview

Personal portfolio website for Omer Iny (Software Engineer & Technical Project Manager). Hosted on GitHub Pages at `omer1004.github.io`. Single-page static site — no build system, no package manager, no server-side code.

## Tech Stack

- **HTML5** — Single `index.html` file (entire site)
- **CSS3** — Custom properties for theming, Bootstrap 3 grid
- **JavaScript** — jQuery-based, no modern framework
- **Bootstrap 3** — Bundled locally in `assets/bootstrap/`
- **Font Awesome 4.4.0** — Via CDN
- **Google Fonts** — Inter & Poppins via CDN
- **Animation libs** — WOW.js, Stellar.js (parallax), Magnific Popup, Shuffle.js

## Directory Structure

```
├── index.html              # Entire site (single-page app)
├── README.md               # Basic project info
├── Omer iny CV.pdf         # Downloadable resume
└── assets/
    ├── bootstrap/          # Bootstrap 3 (css/ + js/)
    ├── css/
    │   ├── style.css       # Main stylesheet (~1400 lines, CSS variables)
    │   ├── responsive.css  # Media queries (mobile breakpoint: 766px)
    │   ├── animate.css     # Animation library
    │   ├── magnific-popup.css
    │   └── font-awesome.min.css
    ├── js/
    │   ├── scripts.js      # Main app logic (~278 lines)
    │   ├── jquery.js        # jQuery library
    │   └── [plugin files]   # stellar, sticky, wow, shuffle, etc.
    └── images/
        ├── works/          # Portfolio project screenshots
        └── [site images]   # Photo, backgrounds, etc.
```

## Color Theme (CSS Variables in style.css)

- Primary: `#0d9488` (teal)
- Primary Light: `#14b8a6`
- Primary Dark: `#0f766e`
- Charcoal: `#1f2937`
- Charcoal Dark: `#111827`

## HTML Sections (index.html)

Sections are identified by `id` attributes used for navigation anchors:

1. **Home/Hero** — `#home`
2. **About Me** — `#about` (photo + bio + CV download)
3. **Work Experience** — `#experience`
4. **Technical Skills** — `#skills`
5. **Education & Timeline** — `#education`
6. **Portfolio/Works** — `#portfolio` (filterable grid: Web, Apps, Database)
7. **Footer** — Social links

## Development Workflow

### Local Development

No build step required. Serve static files with any HTTP server:

```bash
python3 -m http.server 8000
# or
npx http-server
```

Then open `http://localhost:8000/`.

### Deployment

Push to `main` branch — GitHub Pages deploys automatically.

## Code Conventions

### CSS
- Use CSS custom properties (variables) defined in `:root` for colors
- Bootstrap 3 grid classes: `col-md-*`, `col-xs-*`, `row`
- Sections are styled by section name (e.g., `#about`, `#portfolio`)
- Responsive styles go in `responsive.css`, not `style.css`

### JavaScript
- jQuery-based — use `$()` selectors and jQuery methods
- Plugin initialization is in `assets/js/scripts.js`
- Each feature block is wrapped in an IIFE: `(function() { ... }());`
- Animation triggers use the `inview` event for scroll-based reveals

### HTML
- Bootstrap 3 markup patterns (not Bootstrap 4/5)
- Font Awesome 4.x icon syntax: `<i class="fa fa-icon-name"></i>`
- All content lives in `index.html` — there are no other HTML pages

## Key Files to Edit

| Task | File(s) |
|------|---------|
| Content changes (text, sections) | `index.html` |
| Styling / colors / layout | `assets/css/style.css` |
| Mobile responsiveness | `assets/css/responsive.css` |
| Interactive behavior | `assets/js/scripts.js` |
| Portfolio images | `assets/images/works/` |

## Important Notes

- **No build tools** — Do not add webpack, Vite, or similar unless explicitly requested.
- **No Node.js dependencies** — All JS libraries are vendored in `assets/`.
- **Bootstrap 3, not 4/5** — Class names and grid system differ from modern Bootstrap.
- **jQuery required** — `scripts.js` depends on jQuery; do not rewrite to vanilla JS unless asked.
- **Single HTML file** — All sections are in `index.html`. Do not split into multiple pages unless asked.
- **Images are large** — The `assets/images/` directory is ~8MB. Optimize new images before adding.
