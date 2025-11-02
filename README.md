# 🌐 Clarke Mayer Static Site

This repository contains the source code for the **Clarke Mayer** website --- a static site built using **Vite**, **Handlebars**, **HTML**, and **CSS**.

It is optimized for GitHub Pages hosting and supports optional custom domain configuration.

---

## 🚀 Features

- Fast static site built with [Vite](https://vitejs.dev/)

- Modular page structure using Handlebars partials

- Optimized assets (CSS, JS, images)

- SEO-ready (`robots.txt`, `sitemap.xml`)

- Configurable for GitHub Pages or a custom domain

---

## 🧩 Project Structure

clark-mayer/\
├── index.html\
├── certification-guides.html\
├── fun.html\
├── cooking.html\
├── src/\
│ ├── partials/ # Handlebars partials (header, footer, etc.)\
│ ├── assets/ # Static assets (CSS, JS, images)\
│ └── main.js\
├── vite.config.js\
├── sitemap.xml\
├── robots.txt\
├── package.json\
└── README.md

---

## 🧭 1. Clone the Repository

You can clone this project using either HTTPS or SSH.

### Using HTTPS:

```bash
git clone https://github.com/syedshaon/clark-mayer.git
```

### Using SSH:

```bash
git clone git@github.com:syedshaon/clark-mayer.git
```

Then navigate into the folder:

```bash
cd clark-mayer
```

## 💻 2. Local Setup & Testing

### Step 1 --- Install Dependencies

Make sure you have **Node.js (v16 or later)** installed.

Then install dependencies:

`npm install`

### Step 2 --- Run Development Server

Start a local dev server with hot reload:

`npm run dev`

By default, the site will be available at:

`http://localhost:5173`

### Step 3 --- Build for Production

To create an optimized build:

`npm run build`

This generates static files inside the `dist/` folder.

To locally preview the production build:

`npm run preview`

---

## 🌍 3. Deploying to GitHub Pages

### Step 1 --- Create a GitHub Repository

If this repo is being deployed on a client's GitHub account:

1.  Create a **new GitHub repository** (for example, `clark-mayer`).

2.  Push all files to it:

    `git remote set-url origin https://github.com/....................git (new github repo url)

    git push -u origin main`

### Step 2 --- Enable GitHub Pages

1.  Go to **Settings → Pages**

2.  Under **Source**, choose:

    - **Branch:** `main`

    - **Folder:** `/ (root)` or `/dist` if you deploy built files

3.  Click **Save**

The site will be available at:

`https://CLIENT_USERNAME.github.io/clark-mayer/`

---

## ⚙️ 4. Vite Configuration for GitHub Pages

Vite needs to know your base path for asset URLs.

In `vite.config.js`, the base path should match the GitHub Pages subdirectory:

`const repoName = "clark-mayer";
const base = command === "build" ? `/${repoName}/` : "/";`

This ensures all assets load correctly from:

`https://CLIENT_USERNAME.github.io/clark-mayer/`

---

## 🌐 5. Adding a Custom Domain

If you want the site to load from a **custom domain** (like `https://clarkmayer.com`):

### Step 1 --- Add Custom Domain in GitHub Pages

1.  Go to **Settings → Pages**

2.  Under **Custom domain**, enter your domain (e.g. `clarkmayer.com`)

3.  Save it --- GitHub will automatically create a `CNAME` file.

### Step 2 --- Configure DNS

In your domain registrar (Namecheap, GoDaddy, Cloudflare, etc.):

- Add **A records** pointing to GitHub Pages servers:

  ```185.199.108.153
  185.199.109.153
  185.199.110.153
  185.199.111.153
  ```

- Add a **CNAME record**:

  `www  →  your-github-pages-url for me it is syedshaon.github.io`

---

## 🧠 6. Update Vite Config for Custom Domain

If your site will now live at `https://clarkmayer.com` (root, not a subpath):

Change this line in your `vite.config.js`:

`// OLD (for GitHub Pages subfolder)
const base = isProduction ? `/clark-mayer/` : "/";

// NEW (for custom domain)
const base = "/";`

Then rebuild and redeploy:

`npm run build
git add .
git commit -m "update base for custom domain"
git push`

---

## 🧾 7. Optional Files (Recommended)

| File          | Purpose                                        |
| ------------- | ---------------------------------------------- |
| `robots.txt`  | Tells search engines what to index             |
| `sitemap.xml` | Helps Google discover your pages               |
| `CNAME`       | Automatically added when using a custom domain |

---

## 🧰 8. Common Commands

| Command           | Description                              |
| ----------------- | ---------------------------------------- |
| `npm install`     | Install dependencies                     |
| `npm run dev`     | Run local development server             |
| `npm run build`   | Create production-ready build in `dist/` |
| `npm run preview` | Preview the built site locally           |

---

## 🗺️ 9. Update Sitemap After Custom Domain Setup

After the site has been cloned, configured, and verified to work properly on a **new domain**, it’s important to generate a fresh sitemap to match the new URLs.

### Why This Is Important

Your old `sitemap.xml` still points to:
https://syedshaon.github.io/clark-mayer/

Search engines like Google and Bing use this file to crawl your website.  
If the URLs don’t match your new domain (for example `https://clarkmayer.com/`), search engines may ignore or delay indexing.

---

### ✅ Steps to Generate and Replace Sitemap

1. **Visit the Sitemap Generator:**
   Go to [https://www.xml-sitemaps.com/](https://www.xml-sitemaps.com/)

2. **Enter your live website URL:**
   Example: `https://clarkmayer.com/`

3. **Click “Start”**  
   The tool will crawl all public pages and generate a new `sitemap.xml`.

4. **Download the generated file.**

5. **Replace your existing sitemap:**

- Delete or overwrite the old `sitemap.xml` file in your project root.
- Paste the new XML content from xml-sitemaps.com.

6. **Re-deploy the site** (commit and push changes):

```bash
git add sitemap.xml
git commit -m "update sitemap for custom domain"
git push
```

---

## 🧑‍💻 10. Troubleshooting

### ❌ Assets not loading on GitHub Pages?

Check `vite.config.js` → ensure `base` matches your repo name.

### ❌ Blank page or 404 after custom domain setup?

Rebuild with `base: "/"` and clear your browser cache.

### ❌ Service Worker not updating?

Increment your `CACHE_NAME` version and re-publish.

---

## 🏁 Done!

Your site should now be:

- Running locally on `localhost:5173`

- Deployed to GitHub Pages

- Optionally accessible from a custom domain

- Optimized with SEO configuration

---

**Maintained by:** [@syedshaon](https://github.com/syedshaon)\
📧 For support or questions, feel free to open an issue.
