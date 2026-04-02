# Operations

## Deploy Process
1. Edit on `main` branch (staging/ subdirectory or staging branch)
2. `git push` triggers GitHub Pages rebuild (~30s)
3. CDN propagation: 2-3 minutes (hard-refresh or incognito to verify)
4. Promoting staging → prod: copy files, bump version, tag release

## Rollback
- `git revert <commit>` + push = instant rollback
- For emergencies: `git reset --hard <tag>` + force push
- Tags mark every prod release (v0.1, v0.2, v0.3...)

## CDN Cache
- GitHub Pages caches aggressively
- Changes may not appear for 2-3 minutes
- Hard-refresh (Ctrl+Shift+R) bypasses browser cache but not CDN
- Incognito is the safest way to verify
- No cache-busting mechanism without custom headers (GitHub Pages limitation)

## Domain Management
- Current: `ripper234.github.io/jarvis-public/`
- Target: `jarvis.ripper234.com` (Namecheap CNAME → GitHub Pages)
- See `../drafts/jarvis-ripper234-com-dns-setup.md` for instructions

## Versioning
- Semantic tags: `v0.1`, `v0.2`, `v0.3`...
- Version shown in footer of every page
- Bump on every production promote

## Incident Response
1. Identify: what's broken, when did it start
2. Communicate: tell Ron immediately
3. Rollback if needed (revert commit)
4. Root cause: 5 Whys analysis
5. Document in `memory/logs/incidents.md`
6. Prevent: add to checklist if applicable

## Uptime
- GitHub Pages: 99.9%+ uptime (their SLA)
- No server-side code = nothing to crash
- Only risk: bad deploy (broken HTML/CSS)
