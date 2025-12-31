# 🌐 Clarke Moyer Static Site

This repository contains the source code for the **Clarke Moyer** website — a pure HTML static site optimized for GitHub Pages hosting.

---

## 🚀 Features

- Pure HTML/CSS/JavaScript - no build process required
- Modular page structure with consistent headers and footers
- Optimized assets (CSS, JS, images)
- SEO-ready (`robots.txt`, `sitemap.xml`)
- Configured for GitHub Pages deployment

---

## 🧩 Project Structure

```
clarkemoyer-html/
├── index.html                  # Homepage
├── certification-guides.html   # Other pages...
├── fun.html
├── cooking.html
├── css/                        # Stylesheets
├── js/                         # JavaScript files
├── imgs/                       # Images and media
├── robots.txt                  # Search engine instructions
├── sitemap.xml                 # Sitemap for SEO
└── .github/
    └── workflows/
        └── deploy-pages.yml    # GitHub Pages deployment
```

---

## 🧭 1. Clone the Repository

You can clone this project using either HTTPS or SSH.

### Using HTTPS:

```bash
git clone https://github.com/clarkemoyer/clarkemoyer-html.git
```

### Using SSH:

```bash
git clone git@github.com:clarkemoyer/clarkemoyer-html.git
```

Then navigate into the folder:

```bash
cd clarkemoyer-html
```

---

## 💻 2. Local Setup & Testing

Since this is a pure HTML site, you can simply open the HTML files in your browser or use a simple HTTP server.

### Option 1 - Open in Browser

Simply open `index.html` in your web browser.

### Option 2 - Use Python HTTP Server

```bash
python3 -m http.server 8000
```

Then visit: `http://localhost:8000`

### Option 3 - Use Node.js HTTP Server

If you have Node.js installed:

```bash
npx http-server -p 8000
```

Then visit: `http://localhost:8000`

---

## 🌍 3. Deploying to GitHub Pages

### Step 1 — Enable GitHub Pages

1. Go to **Settings → Pages**
2. Under **Source**, choose:
   - **Branch:** `main`
   - **Folder:** `/ (root)`
3. Click **Save**

The site will be available at:

`https://clarkemoyer.github.io/clarkemoyer-html/`

### Step 2 — Automatic Deployment

The repository includes a GitHub Actions workflow (`.github/workflows/deploy-pages.yml`) that automatically deploys your site to GitHub Pages whenever you push to the `main` branch.

---

## 🌐 4. Adding a Custom Domain

If you want the site to load from a **custom domain** (like `https://clarkemoyer.com`):

### Step 1 — Add Custom Domain in GitHub Pages

1. Go to **Settings → Pages**
2. Under **Custom domain**, enter your domain (e.g. `clarkemoyer.com`)
3. Save it — GitHub will automatically create a `CNAME` file.

### Step 2 — Configure DNS

In your domain registrar (Namecheap, GoDaddy, Cloudflare, etc.):

- Add **A records** pointing to GitHub Pages servers:
  ```
  185.199.108.153
  185.199.109.153
  185.199.110.153
  185.199.111.153
  ```

- Add a **CNAME record**:
  ```
  www  →  clarkemoyer.github.io
  ```

### Step 3 — Update Asset Paths (if needed)

If you're using a custom domain at the root level, you may want to update the asset paths in the HTML files from `/clarkemoyer-html/` to `/` for cleaner URLs.

---

## 🧾 5. Optional Files (Included)

| File          | Purpose                                        |
| ------------- | ---------------------------------------------- |
| `robots.txt`  | Tells search engines what to index             |
| `sitemap.xml` | Helps Google discover your pages               |
| `CNAME`       | Automatically added when using a custom domain |

---

## 🗺️ 6. Update Sitemap After Custom Domain Setup

After setting up a custom domain, update your `sitemap.xml` to match the new URLs.

### Why This Is Important

Your `sitemap.xml` points to GitHub Pages URLs. If you switch to a custom domain, update the sitemap so search engines can properly index your site.

### ✅ Steps to Update Sitemap

1. **Visit the Sitemap Generator:**
   Go to [https://www.xml-sitemaps.com/](https://www.xml-sitemaps.com/)

2. **Enter your live website URL:**
   Example: `https://clarkemoyer.com/`

3. **Click "Start"**  
   The tool will crawl all public pages and generate a new `sitemap.xml`.

4. **Download the generated file.**

5. **Replace your existing sitemap:**
   - Overwrite the `sitemap.xml` file in your project root.

6. **Commit and push the changes:**

```bash
git add sitemap.xml
git commit -m "update sitemap for custom domain"
git push
```

---

## 🧑‍💻 7. Troubleshooting

### ❌ Assets not loading on GitHub Pages?

Check that your asset paths in HTML files match the repository structure. For GitHub Pages at `https://username.github.io/repo-name/`, paths should start with `/repo-name/`.

### ❌ Blank page or 404 after custom domain setup?

Make sure DNS is configured correctly and allow up to 24 hours for DNS propagation.

### ❌ Want to change the base path?

If you need to change from `/clarkemoyer-html/` to `/` or another path:
1. Update all asset paths in the HTML files
2. Update links between pages
3. Test locally before deploying

---

## 🏁 Done!

Your site should now be:

- Accessible directly by opening HTML files
- Deployable to any static hosting service
- Automatically deployed to GitHub Pages via GitHub Actions
- Optimized for SEO and performance

---

**Maintained by:** [@clarkemoyer](https://github.com/clarkemoyer)  
📧 For support or questions, feel free to open an issue.
