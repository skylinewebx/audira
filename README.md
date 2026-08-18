# AUDIRA — Premium Headphone Store

A single, fully self-contained `index.html`. No build step, no npm, no framework, no server.
All CSS and JavaScript are inline. Cinematic dark‑luxury (bronze‑on‑black) theme with a warm light theme, animated 3D‑style hero, product detail, cart, wishlist, demo checkout, and a demo login.

---

## 1. Run it locally
Just double‑click `index.html` (or open it in any browser). That's it.

## 2. Deploy to GitHub Pages
1. Create a new GitHub repository.
2. Upload **`index.html`** to the repository root (the `images/` folder too, if you add photos — see below).
3. Go to **Settings → Pages**.
4. Under **Build and deployment → Source**, choose **Deploy from a branch**.
5. Branch: **main**, folder: **/ (root)**. Save.
6. Wait ~1 minute, then open the URL GitHub gives you (e.g. `https://yourname.github.io/audira/`).

The site will look **identical** to local because there are **no external CSS/JS files** — everything is inline. The only remote requests are Google Fonts and a few cinematic photos, all loaded over HTTPS from stable CDNs, each with a built‑in fallback so nothing ever renders broken.

> ✅ Nothing uses Windows/local file paths. Nothing depends on a backend.

---

## 3. Use your OWN headphone photos (optional)
By default each product uses a built‑in premium **SVG render** (this is also what powers the live colour‑switch). To use your own product photography instead:

1. Next to `index.html`, create a folder: `images/products/`
2. Drop your image files in (PNG with transparent background looks best), e.g.
   `a1-black.png`, `a1-blue.png`, `a2-white.png`, …
3. In `index.html`, find the block near the top of the `<script>` called
   **`OPTIONAL REAL PRODUCT PHOTOS`** and fill in the map:

```js
const PRODUCT_PHOTOS = {
  a1: { black:'images/products/a1-black.png', grey:'images/products/a1-grey.png', blue:'images/products/a1-blue.png' },
  a2: { white:'images/products/a2-white.png', black:'images/products/a2-black.png', grey:'images/products/a2-grey.png' },
  a3: {}, a4: {}, a5: {}, a6: {}
};
```

- Paths are **relative** → GitHub‑Pages safe.
- You can also paste full `https://…` image URLs instead of local paths.
- **Any missing or broken image automatically falls back to the SVG render** — so you can add images one at a time and the site never breaks.
- When a colour has a photo, selecting that colour on the product page swaps to it automatically.

## 4. Swap the big lifestyle photos (optional)
Find the **`IMAGES`** object in the `<script>` (hero / immersive / brand). Replace the URLs with your own (local paths or HTTPS). Each has a gradient fallback if the image fails.

```js
const IMAGES = {
  hero:      'images/hero.jpg',
  immersive: 'images/immersive.jpg',
  brand:     'images/brand.jpg'
};
```

---

## 5. What works (all demo, no backend)
- Hamburger drawer navigation, dark/light theme toggle (saved to `localStorage`)
- Product grid with search, category / colour / price filters, sorting
- Product detail with colour selector, quantity, tabs, related items
- Quick View modal
- Cart (add / remove / quantity / totals / empty state)
- Wishlist
- Login / Sign‑up / account dashboard (simulated with `localStorage`)
- Demo checkout — **Card** (with live card preview) or **Cash on Delivery**, then an order‑success screen
- Fully responsive (desktop / tablet / mobile), smooth animations, scroll reveals

> 💳 The checkout is a **demo only** — no real payment is processed and no card data is stored or sent anywhere.

---

## 6. Editing content
All product data lives in the `PRODUCTS` array inside the `<script>` (names, prices, colours, specs, descriptions). Reviews are in `REVIEWS`. Edit those arrays to change the catalogue — no other changes required.
