# Howe Home Improvement — POC

Quick proof-of-concept website for a friend's home improvement business. Two pages, static HTML, zero build step.

## Stack
- Static HTML + Tailwind (via CDN)
- Vanilla JS for gallery filter + lightbox
- Unsplash placeholder photography
- Google Fonts (Inter + Fraunces)

## Files
- `index.html` — home page (hero, services, featured work, about, testimonial, contact)
- `gallery.html` — full gallery with category filter and lightbox

## Preview locally
Just open `index.html` in a browser. No server needed.

## Things to swap for the real site
- All copy currently in placeholder voice
- Phone number: `(555) 555-0100`
- Email: `hello@howehome.com`
- All images are Unsplash placeholders — swap for real project photos
- Contact form just shows an alert — wire to Formspree, Resend, or a Vercel function
- Logo is a placeholder "H" tile — drop in a real wordmark/logo
- Project names are made up (Maple Street, Cedar Ridge, etc.)
- Stats (15+ yrs, 300+ projects, 5.0 rating) — verify or replace
