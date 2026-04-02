# SEO

## Meta Tags (every page)
- `<title>` -- unique, descriptive, under 60 chars
- `<meta name="description">` -- unique, under 160 chars, includes key phrase
- `<meta name="viewport">` -- always `width=device-width, initial-scale=1.0`

## Open Graph (social sharing)
```html
<meta property="og:title" content="Page Title">
<meta property="og:description" content="Short description">
<meta property="og:image" content="https://ripper234.github.io/jarvis-public/img/hero.webp">
<meta property="og:url" content="https://ripper234.github.io/jarvis-public/">
<meta property="og:type" content="website">
<meta name="twitter:card" content="summary_large_image">
```

## Current Status
- Title tags: ✅ on all pages
- Meta descriptions: ⚠️ only on index and projects
- Open Graph: ❌ not yet added
- Sitemap: ❌ not yet created
- robots.txt: ❌ not yet created

## Sitemap
Create `sitemap.xml` in root. Update when pages are added/removed.

## robots.txt
```
User-agent: *
Allow: /
Sitemap: https://ripper234.github.io/jarvis-public/sitemap.xml
```
Block `dev/` and `staging/` from indexing if desired.

## Structured Data
Consider JSON-LD for Person (Ron) and SoftwareApplication (Jarvis). Low priority.

## Canonical URLs
Add `<link rel="canonical" href="...">` to each page. Prevents duplicate content between staging/prod.
