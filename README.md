# biangulum.com

Website of Dražen Hudoletnjak and Biangulum, obrt za računalne usluge.

Plain static HTML and CSS: no build step, no framework, no JavaScript, no cookies,
no third-party requests. Hosted on GitHub Pages.

## Structure

```
index.html            English (https://biangulum.com/)
404.html              Not-found page (GitHub Pages serves it for any missing path)
assets/site.css       All styles; brand colors are CSS variables at the top
assets/fonts/         IBM Plex Sans 400/500/600, latin + latin-ext (self-hosted)
assets/og-image.png   Preview image for links shared on LinkedIn, Slack etc.
favicon.*, icon-*, apple-touch-icon.png, site.webmanifest
                      From C:\WORK\BiangulumLogo\web
CNAME                 Custom domain for GitHub Pages
sitemap.xml, robots.txt
```

A Croatian version may be added later as `hr/index.html`, with the same markup as `index.html`.

## Local preview

Open the site through a local web server so that absolute paths (404 page) work:

```
python -m http.server 8000
```

Then open http://localhost:8000.

## Publishing on GitHub Pages

1. Create a public repository `Biangulum/biangulum.com` and push this folder to `main`.
2. Repository **Settings → Pages**: Source **Deploy from a branch**, branch `main`, folder `/ (root)`.
3. Account **Settings → Pages → Add a domain**: add `biangulum.com` and create the
   TXT record GitHub shows. This verifies the domain so no one else can use it on GitHub Pages.
4. At the domain registrar, set these DNS records:

   | Type | Name | Value |
   |---|---|---|
   | A | @ | 185.199.108.153 |
   | A | @ | 185.199.109.153 |
   | A | @ | 185.199.110.153 |
   | A | @ | 185.199.111.153 |
   | AAAA | @ | 2606:50c0:8000::153 |
   | AAAA | @ | 2606:50c0:8001::153 |
   | AAAA | @ | 2606:50c0:8002::153 |
   | AAAA | @ | 2606:50c0:8003::153 |
   | CNAME | www | biangulum.github.io |

5. Back in repository **Settings → Pages**, the custom domain is read from `CNAME`.
   When the DNS check passes, tick **Enforce HTTPS**.

Every push to `main` publishes the site within a minute or two.

## Email

The site uses `drazen@biangulum.com`. That address needs a mailbox or forwarding
(for example the registrar's email forwarding, or Cloudflare Email Routing if DNS
is moved to Cloudflare) before the site goes live.

## Legal details in the footer

A Croatian obrt with a website must show its name, seat, email and register
number (Zakon o elektroničkoj trgovini, čl. 6). If Biangulum enters the VAT system,
add the VAT ID to the footer of both pages.
