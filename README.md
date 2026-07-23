# Wheel Good Bicycle Repair Co. — Website

A simple static site (plain HTML/CSS/JS, no build step) with a retro-futurism
look based on the shop logo.

## Structure

```
index.html       Home page
services.html    Services & pricing
book.html        Online booking (Square Appointments embed)
about.html       Shop story
contact.html     Contact info, form, map
assets/
  css/style.css  All styling
  js/main.js     Mobile nav toggle
  images/        Logo, favicon, photos
```

Every page shares the same header/nav and footer markup (copy-pasted, since
there's no build tool) — if you edit the nav or footer, update it in all five
`.html` files.

## Things to plug in before launch

1. **Logo** — save your logo file as `assets/images/logo.png`. It's already
   referenced in the header and homepage hero; nothing else to change. If the
   file is missing, the `<img>` tags just hide themselves so the layout still
   looks fine in the meantime.

2. **Square Appointments booking** — in your Square Dashboard go to
   **Appointments > Booking Site > Share** and copy your booking site URL
   (looks like `https://book.squareup.com/appointments/book/XXXXXXXX/LXXXXXXXXXXXXX`).
   Open [book.html](book.html) and replace every `SQUARE_BOOKING_URL` with that
   link. Some browsers block Square's page inside an iframe — if the embed box
   stays blank, just delete the `<iframe>` element and keep the "Open Booking
   Page" button, which opens Square's page in a new tab and works regardless.

3. **Square payments** — Square Appointments already handles deposits/payment
   at booking time once the link above is wired up. If you also want a "buy a
   gift card" or pay-a-deposit button elsewhere on the site, create a
   **Checkout Link** in your Square Dashboard (Payments & Items > Checkout
   Links) and drop it into a `<a class="btn btn-primary" href="...">` anywhere
   you like.

4. **Contact form** — [contact.html](contact.html) posts to Formspree
   (`https://formspree.io/f/YOUR_FORM_ID`). Create a free form at
   [formspree.io](https://formspree.io) and swap in your real form ID, or
   replace the whole `<form>` with a different provider if you prefer.

5. **Map embed** — in [contact.html](contact.html), replace the map iframe's
   `src` with your own: Google Maps → search your address → Share → Embed a
   map → copy the iframe `src`. No API key needed for the basic embed.

6. **Placeholder text** — address, phone, email, hours, and pricing are all
   placeholders. Search each `.html` file for `123 Main Street`,
   `(555) 123-4567`, `hello@wheelgoodbikes.com`, and the price tables in
   [services.html](services.html), and update with your real details.

## Previewing locally

No build step needed — just open `index.html` in a browser. For a closer-to-
production preview (so relative links and fonts behave the same as when
deployed), run a tiny local server from this folder:

```
npx serve .
```

or, if you have Python installed:

```
python -m http.server 8000
```

then visit `http://localhost:8000`.

## Deploying

Any static host works. Two easy free options:

- **Netlify** — drag-and-drop this whole folder onto [app.netlify.com/drop](https://app.netlify.com/drop),
  or connect a git repo for auto-deploys.
- **GitHub Pages** — push this folder to a GitHub repo and enable Pages in the
  repo settings (Settings > Pages > Deploy from branch).

No environment variables or server config needed since it's all static files.
