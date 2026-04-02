# Analytics

## Approach
Lightweight. No heavy tracking. Respect privacy.

## Options (pick one)
1. **Google Analytics 4** -- industry standard, free, powerful. Adds ~30KB JS.
2. **Plausible** -- privacy-focused, no cookies, GDPR-compliant. ~1KB script. $9/mo or self-host.
3. **Cloudflare Web Analytics** -- free, privacy-first, no JS needed if using CF. We're not on CF.
4. **None** -- acceptable for now. Ron's the primary audience.

## What to Track
- Page views per page (which content gets read)
- Traffic sources (how people find us)
- Device breakdown (mobile vs desktop -- validates mobile-first)
- Geography (Israel vs international)
- Bounce rate on homepage

## What NOT to Track
- Individual user behavior
- Personal data
- Scroll depth (overkill for our scale)

## Privacy
- No cookies if possible (Plausible, CF)
- If GA4: add cookie consent banner
- Never share analytics data publicly
- GDPR not strictly required (not EU-based) but good practice

## Current Status
- No analytics installed
- Ron browses on phone -- we know mobile matters
- Traffic is low -- analytics are informational, not decision-critical yet
