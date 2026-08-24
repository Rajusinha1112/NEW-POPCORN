# PopFuel — Static Storefront (Plain HTML/CSS/JS)

No build step, no npm, no framework, no folders to keep together. Every page is a single
self-contained `.html` file — CSS and JS are inlined directly inside each file. Open any file
directly in a browser, or upload it anywhere (FireFunnels, Hostinger, Netlify, GitHub Pages) —
nothing will break from paths or missing folders.

## Files
```
index.html               Homepage — all 12 sections
shop.html                All flavours + category filter (?category=spicy etc.)
product.html              Product detail (?slug=pickle-tickle etc.)
cart.html                 Cart — quantity controls, subtotal
checkout.html              Shipping form + order placement
order-confirmation.html    Order confirmed + tracking UI (?id=PF12345678)
```
Each file has its own `<style>` block and `<script>` block near the bottom — everything needed
to render that page is inside that one file.

## How the cart works
Pure `localStorage` — no server needed. Add to Cart on any page, it persists across pages and
reloads on the same browser. Checkout currently **simulates** placing an order (generates an
order ID, clears the cart, redirects to the confirmation page) — it doesn't email/log the order
anywhere yet. Wire the `handleCheckoutSubmit()` function inside `checkout.html` to a real
endpoint (e.g. a Google Apps Script web app posting to a Sheet, matching your usual form →
WhatsApp/Sheets pattern) when ready.

## Editing product data
Product data is duplicated inside every file's `<script>` block (near the top, a `PRODUCTS`
array) so each page works standalone. **When you update a price or tagline, update it in all 6
files** — search for the product's `slug` (e.g. `sea-salt-classic`) to find it fast in each file.

## What's real vs. placeholder (do not treat as final)
- **Prices/taglines**: only Pickle Tickle ($8.99), Onion Cream & Sour ($8.49), and Spicy
  Cheddar ($9.49) are real. The other 4 flavours show TBD everywhere — nothing was invented.
- **Photography/logo**: none provided yet — every image is a dashed "photo pending" placeholder.
  Search for `img-placeholder` in each file and swap for a real `<img src="...">` tag once
  photos are ready.
- **Customer reviews**: empty dashed slots on the homepage, no fabricated testimonials.
- **Marketplace logos** (Amazon/Flipkart/etc. in the "Available On" strip on the homepage):
  illustrative placeholder list — confirm actual listings before publishing.

## Deploy
Just upload the `.html` files as-is — no folders, no build step:
- **FireFunnels / your usual hosting**: upload all 6 files directly.
- **Netlify**: drag the files onto app.netlify.com/drop.
- **GitHub Pages**: push the files to a repo, enable Pages in Settings.
