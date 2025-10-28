# Salesmap Deal History Viewer

This project contains a standalone HTML page (`deal-history.html`) that helps you call the [Salesmap Deal History API](https://docs.salesmap.kr/developers/api-reference/deal/history). The page stores your API token and cursor locally and provides a friendly interface for triggering the endpoint and inspecting responses.

## Prerequisites

- Salesmap Open API token with permission to read deal history data.
- Any static file server (for local preview) such as Python's built-in `http.server` module, Node's `serve`, or similar.

## Run locally

1. Clone or download this repository.
2. From the project root, start a static file server. For example, with Python installed:
   ```bash
   python3 -m http.server 4173
   ```
3. Open your browser to `http://localhost:4173/deal-history.html`.
4. Enter your API token and the target deal ID, then submit the form to retrieve history results.

## Deploying

Because the site is a single static HTML file, you can deploy it to any static hosting provider. Common options are described below.

### GitHub Pages

1. Push this repository to GitHub.
2. In the repository settings, enable **Pages** and choose the branch (e.g., `main`) and directory (`/` root).
3. After GitHub finishes building the site, visit the published URL (usually `https://<username>.github.io/<repo>/deal-history.html`).

### Netlify (or similar static hosts)

1. Create a new site on Netlify and connect it to your Git repository, or drag-and-drop a ZIP export of the repo into the Netlify dashboard.
2. Set the build command to `none` (since it's static) and the publish directory to the repository root (`/`).
3. Deploy the site and browse to the provided URL.

### Self-hosted / Other CDNs

If you manage your own infrastructure, upload `deal-history.html` (and any accompanying assets) to your web server or CDN (e.g., AWS S3 + CloudFront, Nginx, Vercel). Ensure the server serves the HTML file over HTTPS so that the Salesmap API can be called securely from the browser.

## Environment variables & secrets

All sensitive values (API token) are entered client-side and stored only in the browser's `localStorage`. Make sure you trust the hosting domain because the browser will persist these values locally for the user.

