# Deployment

aystoai.com is a static site on Netlify. The domain is registered with GoDaddy and pointed at Netlify.

## How it's wired

```text
GitHub (sdg00x/aystoai, main)
        │  push
        ▼
Netlify  ── publishes site/ (from netlify.toml)
        │
        ▼
aystoai.com  (GoDaddy DNS → Netlify)
```

## Connect this repo to Netlify (one time)

If the site was first deployed by dragging a folder into Netlify, switch it to deploy from GitHub:

1. Netlify dashboard → your aystoai site → **Site configuration → Build & deploy → Continuous deployment**.
2. **Link repository** → GitHub → `sdg00x/aystoai`.
3. Branch: `main`. Build command: leave empty. Publish directory: `site` (already set in `netlify.toml`).
4. Save. Netlify runs the first deploy straight away.

From then on, every push to `main` goes live.

## Domain and DNS (GoDaddy)

In Netlify: **Domain management → Add a domain → aystoai.com**. Netlify shows the records to add. In GoDaddy DNS they are usually:

| Type | Name | Value |
| --- | --- | --- |
| A | `@` | `75.2.60.5` (Netlify's load balancer, confirm in your Netlify panel) |
| CNAME | `www` | `<your-site>.netlify.app` |

Netlify issues the HTTPS certificate automatically once DNS resolves. That can take up to a few hours.

## Redirects

`site/_redirects` sends old `/websites` links to `/business` with a permanent 301, so links already sent in outreach keep working.

Add new redirects there, one per line:

```text
/old-path    /new-path    301
```

## Headers and caching

`netlify.toml` sets:

- basic security headers on every page
- long caching for audio and images
- short caching for HTML, so copy changes show up straight away

## Rolling back

Netlify keeps every deploy. **Deploys → pick an older one → Publish deploy** puts it live in seconds. Then fix forward in Git.

## Checklist before pushing

- [ ] Checked the page on a phone-sized window
- [ ] `CONFIG` values are right (Calendly link, Formspree ID, email)
- [ ] No API keys or private numbers added to the code
- [ ] New images compressed (under ~300 KB each)
