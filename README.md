# Forensic Demo Store — 48436 Digital Forensics

Controlled, static e-commerce simulation for web analytics experiments. No real payments, authentication or personal information collection.

## Run locally
Open `index.html` in Chrome, or run `python -m http.server 8000` in this directory and visit `http://localhost:8000`.

## Publish on GitHub Pages
1. Create a new public GitHub repository named `forensic-demo-store`.
2. Upload `index.html`, `style.css`, `script.js` and `README.md` to the repository root and commit.
3. Navigate to Settings > Pages. Select Deploy from a branch, `main`, `/ (root)` and Save.
4. Wait for deployment. The URL typically looks like `https://YOUR-USERNAME.github.io/forensic-demo-store/`.
5. Open the published site and test all buttons.

## Analytics integration (later step)
1. Create a GA4 Web data stream for the published URL.
2. Create a Google Tag Manager Web container and insert the official GTM snippets into `index.html` as instructed by GTM. Publish the changed site.
3. Create a Google tag in GTM with your GA4 Measurement ID and Initialization - All Pages trigger.
4. For ecommerce actions, create GTM Custom Event triggers matching: `view_item`, `add_to_cart`, `remove_from_cart`, `view_cart`, `begin_checkout`, `purchase`.
5. Configure GA4 Event tags using the appropriate event names and ecommerce parameters from `dataLayer`. Preview in GTM before publishing. Events in the dataLayer are **not automatically sent to GA4**.
6. Install Microsoft Clarity through GTM as a separate tracking integration. Do not install duplicate tracking scripts.
7. Check local privacy/consent requirements before enabling analytics on a publicly accessible site. Use only consenting group members for testing and avoid real personal data.

## Controlled test sequence
1. Open home page; click Explore products.
2. View details for one product (`view_item`).
3. Add the product to cart (`add_to_cart`).
4. Remove one product (`remove_from_cart`) or add another.
5. Open cart (`view_cart`).
6. Simulate checkout (`begin_checkout`).
7. Complete simulated purchase (`purchase`).

## Screenshot checklist
- Published site and repository files
- GA4 property and data stream
- GTM container and preview showing ecommerce custom events
- GA4 realtime and events reports (after tags are configured)
- Chrome DevTools network requests and browser cookies
- Wireshark capture during site visit (HTTPS limits payload visibility)
- Microsoft Clarity dashboard, recordings, heatmaps

## Research limitations
- Site uses fictional products and simulated transactions; no real sales or conversion-rate inference.
- `dataLayer` events are local JavaScript signals until GTM tags are configured.
- No user login, payment gateway, or backend database.
- GitHub Pages hosting is public; do not publish secrets, IDs you consider sensitive, or personal data.
