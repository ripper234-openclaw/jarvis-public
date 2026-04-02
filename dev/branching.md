# Branching & Deployment Strategy

## Current Setup
- `main` branch, `staging/` subdirectory = staging
- `main` branch, root files = production
- Both deployed via GitHub Pages from `main`

### Problems
- Staging and prod changes in same commit history
- Can't review them independently
- Easy to accidentally push staging content to prod
- `git log` is a mess of interleaved staging/prod commits

## Options

### Option 1: Separate repo
- `ripper234/jarvis-public` = production (main branch, GitHub Pages)
- `ripper234/jarvis-public-staging` = staging (main branch, GitHub Pages)

| Pro | Con |
|-----|-----|
| Cleanest separation | Two repos to manage |
| Zero config | Manual sync between repos |
| Both on GitHub Pages | PRs can't cross repos |
| Free | Duplicated assets/CSS |

### Option 2: GitHub Actions
- `main` = prod source
- `staging` branch = staging source
- GitHub Action merges both into `gh-pages` branch (prod at `/`, staging at `/staging/`)

| Pro | Con |
|-----|-----|
| One repo | Need to write/maintain the Action |
| Clean branch separation | More moving parts |
| PRs work normally | Action debugging can be annoying |
| Free | Slight deploy delay (Action run ~30s) |

### Option 3: Netlify or Vercel (free tier)
- Keep GitHub Pages for production (`main` branch)
- Add Netlify/Vercel for staging + branch previews
- Every branch/PR gets a unique preview URL automatically

| Pro | Con |
|-----|-----|
| Zero config after setup | Third-party dependency |
| Per-PR preview URLs | Another account to manage |
| Instant deploys | Free tier limits (Netlify: 100GB bandwidth/mo, 300 build min/mo) |
| Branch deploys built-in | Slightly different CDN behavior than prod |
| Free for our scale | Two different hosting providers = potential style/behavior drift |
| No GitHub Actions to maintain | If Netlify/Vercel changes pricing, need to migrate |

#### Netlify free tier specifics
- 100GB bandwidth/month (we use ~nothing)
- 300 build minutes/month (each build ~5s, so ~3,600 builds)
- 1 concurrent build
- Custom domains included
- Deploy previews on every PR

#### Vercel free tier specifics  
- 100GB bandwidth/month
- 6,000 build minutes/month
- Serverless functions included (don't need)
- Deploy previews on every PR
- Slightly faster builds than Netlify

### Option 4: Cloudflare Pages (honorable mention)
- Similar to Option 3 but on Cloudflare
- Unlimited bandwidth on free tier
- Deploy previews per branch
- Fastest global CDN

## Recommendation

**Option 3 (Netlify)** for now. Reasons:
1. Least effort — connect repo, done
2. Per-PR previews are killer for review workflow
3. Free tier is way more than we need
4. Production stays on GitHub Pages (no migration)
5. If we hate it, zero lock-in — just disconnect

**Downsides are minor:**
- One more account (use GitHub OAuth, 30 seconds)
- Theoretical pricing risk (we'd see it coming, easy to switch)
- Staging CDN slightly different from prod CDN (negligible for static HTML)

**When to revisit:** If we add a custom domain and want everything unified, Option 2 (GitHub Actions) becomes more attractive.

## Migration Steps (if Option 3 approved)
1. Sign up at netlify.com with GitHub
2. Connect `ripper234/jarvis-public` repo
3. Set build command: (none, static site)
4. Set publish directory: `/` (or `/staging` for staging site)
5. Enable branch deploys for `staging` and PR previews
6. Remove `staging/` subdirectory from `main` branch
7. Move staging content to `staging` branch
8. Update dev workflow docs
