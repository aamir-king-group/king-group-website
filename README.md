# King Group of Companies — Website Demo

Approved demo website for **King Group of Companies** (Dubai). This repository is the
handoff package for the development team building the production website.

**Live preview:** open `index.html` in any browser — no build step, no server needed.

---

## 1. What is in this repository

| Path | Purpose |
|---|---|
| `index.html` | The complete approved demo — all pages, styles, scripts and images in ONE file |
| `assets.zip` | Raw production assets — `logos/` (transparent PNGs, group + all 8 companies) and `photos/` (leadership portraits) |
| `content-plan.md` | Approved content, timeline, and open items |

`index.html` is self-contained (images embedded as base64) so the demo works from a
double-click or GitHub Pages with zero setup. For production, use the raw files from
`assets.zip` instead of the embedded copies.

## 2. Anatomy of index.html

The file has three clearly separated sections:

1. **`<style>` block** — the full design system (see brand tokens below).
2. **`const LEADERS = [...]` and `const COMPANIES = [...]`** — ALL site content lives in
   these two JavaScript arrays (bios, services, facts, quotes). Editing content = editing
   these arrays. No content is hidden in markup.
3. **View functions + hash router** — `viewHome()`, `viewAbout()`, `viewLeadership()`,
   `viewLeader(slug)`, `viewCompanies()`, `viewCompany(slug)`, `viewContact()` render into
   `#app` based on `location.hash`.

### Routes (18 views)

| Hash | Page |
|---|---|
| `#/home` | Home |
| `#/about` | The Group — welcome, story, timeline, mission |
| `#/leadership` | Leadership index |
| `#/leader/<slug>` | 5 profile pages (`umar-farooq`, `saeed-ahmed-khan`, `saleem-ahmed-khan`, `muhammad-asad-khan`, `muhammad-aamir-khan`) |
| `#/companies` | Companies index |
| `#/company/<slug>` | 8 company pages (`king-riders`, `king-limousine`, `king-drive`, `digitalcoo`, `king-prime`, `king-smart`, `solutionwin`, `xpert-advertising`) |
| `#/contact` | Contact + company directory |

## 3. Brand tokens

| Token | Value | Use |
|---|---|---|
| Black | `#131011` | Headers, footer, dark sections |
| Coal | `#1b1718` | Page heroes |
| Red | `#a3121c` | Primary accent (from group logo) |
| Deep red | `#7c0c14` | Hover states |
| Cream | `#fcfaf3` | Page background |
| Paper | `#f5efe2` | Alternate sections |
| Brass | `#9d8451` | Hairline ornaments only |
| Headings | `Playfair Display` (Google Fonts) | Serif display |
| Body | `EB Garamond` (Google Fonts) | Serif text, fallback Georgia |

Design language: classic/editorial — square corners, double-rule borders, small-caps
letterspaced labels, monogram medallions. Please keep this character in production.

## 4. SEO — current status

**Already done in this demo:**
- Per-page `document.title` via router
- Meta description, robots, theme-color
- Open Graph + Twitter card tags
- Valid JSON-LD `Organization` schema listing all 8 subsidiary companies
- Semantic headings (one `h1` per view), alt text on all images, favicon

**Required for production (cannot be done in a hash-routed single file):**
1. Real URL per page (`/companies/king-riders` not `#/company/king-riders`) — static
   generation or SSR. The view functions map 1:1 to pages.
2. Hosted `og:image` (1200×630) + `og:url` + canonical tags per page.
3. `sitemap.xml` + `robots.txt` at domain root.
4. Serve images as files (from `assets/`) with `loading="lazy"`, not base64.
5. Analytics + Search Console verification.

## 5. Functional notes

- **Contact form is a demo** — it shows a message and sends nothing. Connect to a real
  backend/email service in production.
- The mobile menu, dropdown menus, and company/leader pager are pure JS/CSS — no
  dependencies, no frameworks, no build tools.
- Browser storage is NOT used anywhere.

## 6. Open content items (confirm with Mr. Aamir Khan before launch)

1. "Xpert" vs "Xperts" — the logo reads XPERTS; site text and domain use Xpert.
2. Digitalcoo founding year — site text says 2021 (per management); digitalcoo.ae says
   licensed 2018.
3. Group HQ contact details on the Contact page are placeholders.
4. Xpert Advertising services are still draft (marked on the page).

---

© 2026 King Group of Companies. Prepared for internal development use.
