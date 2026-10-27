# Repository Instructions

## Project
- This is a bilingual Arabic/English coffee storefront and order-management app.
- It uses plain HTML, CSS, and browser JavaScript with a dependency-free Node.js server (Node.js 18+). Do not introduce a framework or runtime dependency without a clear need.
- `server.js` owns the HTTP API, static-file allowlist, product catalog/prices, and local JSON persistence. New public assets must be added to its `publicFiles` map.
- `index.html`, `store.js`, and `styles.css` implement the storefront; `admin.html` and `admin.js` implement the admin UI.
- Product IDs and display names are mirrored between `server.js` and `store.js`; the server is authoritative for prices and order totals. Keep the catalog in sync when changing products.
- Preserve the Arabic RTL experience and existing English-language toggle when changing customer-facing UI.

## Data and security
- `.env` and `data/` are git-ignored. Never commit credentials, admin records, or customer orders, and do not overwrite user data in `data/`.
- Admin passwords are stored as hashes and sessions are in memory. Preserve server-side validation and authorization for API changes; do not trust client-provided prices or totals.
- Continue using the existing Node.js built-ins and atomic JSON-file writes unless the architecture is deliberately changed.

## Run and verify
- Start locally with `npm start` or `node server.js`; the default URL is `http://localhost:3000`. Set `PORT` to override the port.
- Run the smoke test with `npm run test:smoke` or `node smoke-test.js` while the server is running. Set `BASE_URL` if the server uses a non-default address. The test requires an admin account to have been configured and creates then removes a temporary order.
- Keep changes focused and verify behavior with the smoke test for server/API changes. For UI-only changes, check both Arabic and English layouts in a browser when available.
