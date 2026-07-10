# DTech IT Solutions — Website

A fast, dependency-free static website for DTech IT Solutions. No build step, no
framework — just HTML, CSS and vanilla JavaScript. Drop the folder on any web host
and it works.

## Files

```
dtech-site/
├─ index.html        Main one-page site
├─ 404.html          Custom "not found" page
├─ robots.txt        Search-engine directives
├─ css/styles.css    All styling (design tokens at the top)
├─ js/main.js        Menu, scroll animation, contact form
└─ assets/
   └─ favicon.svg    Browser tab icon
```

## Deploy it

Pick whichever host you use — no configuration needed.

**Netlify / Vercel / Cloudflare Pages (drag & drop)**
1. Zip the `dtech-site` folder (or connect a Git repo containing it).
2. Drag the folder into the host's "deploy" area.
3. Set the publish/output directory to the folder root. Done.

**GitHub Pages**
1. Push these files to a repo.
2. Settings → Pages → deploy from branch → `/root`.

**cPanel / shared hosting / VPS (Apache or Nginx)**
1. Upload the contents of `dtech-site` into `public_html` (or your web root).
2. Make sure `index.html` sits at the root of the domain. That's it.

The site is fully static, so it also runs by simply opening `index.html` locally —
though a tiny local server avoids browser file-path quirks:
```
cd dtech-site
python3 -m http.server 8080     # then visit http://localhost:8080
```

## Things to change before going live

All are quick find-and-replace edits:

| What | Where |
|------|-------|
| Contact email | `index.html` (mailto link) **and** `CONTACT_EMAIL` in `js/main.js` |
| Phone number | `index.html` — the `tel:` link in the Contact section |
| Company legal status | footer note in `index.html` |
| Colors / fonts | CSS variables at the top of `css/styles.css` |

## Making the contact form land in an inbox

By default the form opens the visitor's email app with everything pre-filled
(works everywhere, needs no server). To collect submissions automatically instead:

1. Sign up for a form service such as **Formspree** or **FormSubmit** (free tiers exist).
2. In `index.html`, give the `<form>` an `action="https://formspree.io/f/XXXX"` and
   `method="POST"`.
3. In `js/main.js`, remove the `e.preventDefault()` / mailto block so the browser
   posts the form normally (or use the service's fetch/AJAX snippet).

## Notes

- Responsive down to mobile, keyboard-accessible, and honors "reduced motion".
- Fonts load from Google Fonts; if you prefer zero external requests, download the
  three families (Space Grotesk, Inter, JetBrains Mono) and self-host them.
- Content is drawn from the DTech IT Solutions business proposal.
