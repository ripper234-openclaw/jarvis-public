# Testing & QA

## Pre-Ship (every change)
See `checklist.md` for the full list. This doc covers the broader QA process.

## Browser Matrix
Test on at minimum:
- **Chrome mobile** (Ron's primary device)
- **Safari mobile** (iOS users)
- **Chrome desktop** (development)
- **Firefox desktop** (catches CSS edge cases)

## Accessibility
- Color contrast: 4.5:1 minimum for body text, 3:1 for large text
- All images have `alt` attributes
- Interactive elements are keyboard-navigable
- `prefers-reduced-motion` respected
- Semantic HTML: headings in order (h1 → h2 → h3), landmarks
- Test with screen reader (VoiceOver on Mac/iOS) periodically

## Link Checking
- No 404s. Ever. Use "Coming soon" placeholders.
- Renamed pages get instant redirects
- External links checked monthly (they rot)

## Visual QA
- Screenshot comparison before/after changes
- Check on real phone, not just responsive mode
- Test at: 320px, 375px, 480px, 768px, 1024px, 1440px

## Performance QA
- Lighthouse audit (aim for 90+ on all categories)
- PageSpeed Insights for real-world data
- Check hero image LCP specifically

## Staging QA Process
1. Push to staging
2. Visual check on phone + desktop
3. Run through checklist.md
4. Flag blockers
5. Get Ron's approval
6. Promote to prod
7. Verify prod + link in message
