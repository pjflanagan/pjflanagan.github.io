# Decap CMS Setup

Goal: Add a /admin UI for editing blog posts and content without touching code directly.

## Decision: Auth Backend

Pick one before starting:

- [ ] **GitHub OAuth + proxy** (recommended for GitHub Pages)
  - Requires creating a GitHub OAuth App (free)
  - Requires deploying a tiny auth proxy — Cloudflare Workers or Vercel, both free tier
  - Stays on GitHub Pages hosting
- [ ] **Netlify Identity** (easiest overall)
  - Move hosting from GitHub Pages to Netlify
  - Auth is built-in, no proxy needed
  - Free tier should cover a personal site

## Steps (GitHub OAuth + Cloudflare Workers path)

1. **Create GitHub OAuth App**
   - Go to GitHub > Settings > Developer settings > OAuth Apps > New OAuth App
   - Homepage URL: `https://flanny.app`
   - Callback URL: `https://<your-worker>.workers.dev/callback`
   - Save the Client ID and Client Secret

2. **Deploy auth proxy to Cloudflare Workers**
   - Use `decap-netlify-oauth-provider` or `cloudflare-worker-github-oauth` (open source, one file)
   - Set `GITHUB_CLIENT_ID` and `GITHUB_CLIENT_SECRET` as Worker secrets
   - Note the deployed worker URL for the next step

3. **Add `admin/index.html`**
   ```html
   <!doctype html>
   <html>
     <head>
       <meta charset="utf-8" />
       <meta name="viewport" content="width=device-width, initial-scale=1.0" />
       <title>Content Manager</title>
     </head>
     <body>
       <script src="https://unpkg.com/decap-cms@^3.0.0/dist/decap-cms.js"></script>
     </body>
   </html>
   ```

4. **Add `admin/config.yml`**
   ```yaml
   backend:
     name: github
     repo: pjflanagan1/pjflanagan.github.io
     branch: main
     base_url: https://<your-worker>.workers.dev

   media_folder: assets/images
   public_folder: /assets/images

   collections:
     - name: posts
       label: Blog Posts
       folder: _posts
       create: true
       slug: "{{year}}-{{month}}-{{day}}-{{slug}}"
       fields:
         - { label: Title, name: title, widget: string }
         - { label: Date, name: date, widget: datetime }
         - { label: Body, name: body, widget: markdown }
         - { label: Tags, name: tags, widget: list, required: false }
   ```

5. **Test locally**
   - Run `bundle exec jekyll serve`
   - Visit `http://localhost:4000/admin`

6. **Push and verify on prod**
   - The `/admin` route should be live at `https://flanny.app/admin`
   - Log in via GitHub to confirm the OAuth flow works end-to-end

## Notes
- The `config.yml` fields above are minimal — can add categories, featured image, excerpt, etc.
- Decap edits commit directly to the repo via the GitHub API, so changes go through the normal Jekyll build
- If GitHub Pages build times feel slow for editing, Netlify path builds faster (~30s vs ~2min)
