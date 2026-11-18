# Route Map Travel · Dubai tour packages

A single-page website for Route Map Travel (UAE) with an animated 3D Dubai background that changes from sunrise to night as you scroll.

Open `index.html` in a browser, or host it as a static site (for example GitHub Pages: Settings → Pages → Deploy from branch → `main` / root).

## What is in it

- Animated 3D Dubai skyline (three.js): Burj Khalifa, Burj Al Arab, Dubai Frame, marina towers, road with traffic, water, desert camp. Falls back to a 2D scene if WebGL is not available.
- Package cards with a **Details** window (overview, highlights, itinerary, included / not included, notes) and WhatsApp enquiry buttons.
- Places, "Why us", auto-rotating story gallery, enquiry form that opens WhatsApp with the details filled in.
- Responsive layout with a bottom navigation bar on phones.
- Admin panel (`#admin`) for editing every text, package, place, story, the WhatsApp number and contact details.

## Editing the content without the admin panel

All content lives in one JSON block near the top of `index.html`:

```html
<script type="application/json" id="site-data"> ... </script>
```

Edit it with any text editor: `whatsapp` (country code + number, digits only, for example `971501234567`), `contact`, `links`, `texts`, `packages`, `places`, `why`, `stories`.

## About the admin panel

The admin panel saves by publishing a new version of the page through Claude's artifact API, so **it only works when the page is hosted as a Claude artifact and you are signed in to Claude as the owner**. On GitHub Pages or any other host it opens a notice instead of the editor. If you self-host, edit the JSON block above. The `id="tpl"` block is only used by the admin panel's save and can be removed when self-hosting.

The admin password is stored as a salted SHA-256 hash in `site-data` (`adminHash`, `salt`). It is empty in this repository; the first time the panel is opened by the owner it asks you to create one.

## External libraries (loaded from CDNs)

- three.js r128 (cdnjs) and its Reflector / post-processing examples (jsDelivr)
- anime.js 3.2.2 (jsDelivr)
- Google Fonts: Playfair Display, Inter
