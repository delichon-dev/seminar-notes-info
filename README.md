# seminarnotes.app

The public website of the Seminar Notes iPhone app, served by GitHub Pages from the `main` branch at https://seminarnotes.app (`CNAME`). Plain HTML and CSS, no build step and no Jekyll (`.nojekyll`).

- `index.html`: the one-page site.
- `privacy.html`: the privacy policy, linked from the App Store listing.
- `site.css`: the styles. Text scales with the viewport; light and dark follow the system.
- `fonts/`: Fraunces and Nunito as variable woff2 fonts (one file per subset covers every weight), self-hosted so the page makes no request to a font service.
- `images/icon.png`: the app icon, cropped to the squircle at 512 px (from the `app-marketing` repo).
- `images/app-store-badge.svg`: Apple's "Download on the App Store" badge.
- `images/*.png`: App Store screenshots from the app repo's `fastlane/screenshots/en-US/`, resized to 800 px wide.

Preview locally:

```sh
python3 -m http.server 8000
```

then open <http://localhost:8000/>.

## DNS for seminarnotes.app

At the registrar, point the apex at GitHub Pages and `www` at the organization's Pages host:

| Type  | Name | Value |
|-------|------|-------|
| A     | @    | 185.199.108.153 |
| A     | @    | 185.199.109.153 |
| A     | @    | 185.199.110.153 |
| A     | @    | 185.199.111.153 |
| AAAA  | @    | 2606:50c0:8000::153 |
| AAAA  | @    | 2606:50c0:8001::153 |
| AAAA  | @    | 2606:50c0:8002::153 |
| AAAA  | @    | 2606:50c0:8003::153 |
| CNAME | www  | delichon-dev.github.io |

Add the records before merging a change to `CNAME`: when the file lands on `main`, GitHub Pages sets the custom domain and redirects the old github.io address to it, so the privacy URL in App Store Connect fails until the domain resolves. Then, in the repository's Settings › Pages, confirm the custom domain `seminarnotes.app` and turn on *Enforce HTTPS* once the certificate is issued (up to a day after the DNS records resolve). The old address https://delichon-dev.github.io/seminar-notes-info/ redirects to the new one.
