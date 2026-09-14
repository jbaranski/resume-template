# My resume template

A single-page resume site built with Jekyll and [simple.css](https://simplecss.org), deployed to GitHub Pages by GitHub Actions. The resume lives in one markdown file (`index.md`) and is served as the site's home page.

## Using this template

### 1. Fork the repository

Fork it to your own account, or click **Use this template → Create a new repository**. The rest of these steps assume you named it `resume-template`; if you chose a different name, note it for step 2.

### 2. Set `baseurl` to match your repository name

In `_config.yml`:

```yaml
url: 'https://<your-username>.github.io'
baseurl: '/<your-repo-name>'
```

Two exceptions:

- If you named the repository `<your-username>.github.io` (a GitHub Pages *user* site), set `baseurl: ''`.
- If you plan to use a custom domain (step 7), also set `baseurl: ''`.

### 3. Check the default branch in the workflow

`.github/workflows/deploy-web.yml` deploys on pushes to `main`:

```yaml
on:
  push:
    branches:
      - main
```

### 4. Turn on GitHub Pages

In your repository: **Settings → Pages → Build and deployment → Source → GitHub Actions**.


### 5. Replace the placeholder content

| File | What to do |
|------|------------|
| `index.md` | Your actual resume. Keep the front matter at the top and edit the markdown below it. The `title` here is what shows in the browser tab, so set it to your name. |
| `resume/resume.pdf` | Replace with your own PDF, or delete the `resume/` folder if you don't want one. |
| `assets/favicon.svg` | Replace with your own icon, or leave the placeholder. |
| `robots.txt` | Empty by default. Add rules if you want to restrict crawlers. |
| `_config.yml` | Set `baseurl` (step 2). `name` and `url` are conventional Jekyll fields that no template in this site reads, so they are cosmetic. |
| `LICENSE` | Update or remove the copyright line. |

### 6. Push

Push to your default branch. The **deploy-web** workflow builds the site and publishes it; watch it under the **Actions** tab. When it's green your site is live at:

```
https://<your-username>.github.io/<your-repo-name>
```

### 7. Optional: use a custom domain

1. Create a file named `CNAME` in the repository root containing only your domain, e.g. `www.example.com`.
2. Point your DNS at GitHub Pages, following [GitHub's DNS instructions](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site).
3. Set `baseurl: ''` and `url: 'https://www.example.com'` in `_config.yml`, since the site is now served from the domain root rather than a `/repo-name/` path.

## Previewing locally

Requires Ruby (see `.ruby-version` for the version this is built against):

```sh
bundle install
bundle exec jekyll serve
```

Then open the URL jekyll prints — with a `baseurl` set it will include the path prefix, e.g. `http://127.0.0.1:4000/resume-template/`. The server rebuilds as you edit, so a browser refresh shows your changes.

Styling comes from the simple.css CDN, so there's no CSS build step. `assets/simplecssthemehelper.css` overrides its theme variables — edit that file to change colors.
