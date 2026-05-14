# brucelande-site / brucelande.com — Deploy Rules

**This is the marketing site for brucelande.com.** Separate from the CMS / creatorprotools.com workflow. Do NOT confuse the two.

## How deploys work here

Two GitHub remotes exist:

| Remote | URL | Purpose |
|--------|-----|---------|
| `origin` | github.com/brucelande-hub/brucelande-site.git | Source repo. Branch: `master`. |
| `vercel-repo` | github.com/brucelande-hub/brucelande-website.git | The repo Vercel watches. Production branch: **`main`**. |

**Vercel deploys from `main` on `vercel-repo`.** Pushing to `origin/master` alone does NOT trigger a deploy — you must also push to `vercel-repo`'s `main`.

## To deploy a change

```bash
cd c:/Users/bruce/OneDrive/repos/brucelande-site
git add <files>
git commit -m "..."
git push origin master              # source of truth
git push vercel-repo master:main    # triggers Vercel deploy of brucelande.com
```

## About the "NEVER commit to main" rule in repos/CLAUDE.md

That rule (rule #15) is scoped to the **CMS** workflow on `paid-dev`. It does NOT apply here. **For brucelande.com, `main` on `vercel-repo` IS the live production branch** — that's Vercel's configured production branch and the only way to deploy this site. Bruce explicitly OK'd this carve-out on 2026-05-14.

If you want to change this, the alternative is to switch the production branch in Vercel Project Settings → Git → Production Branch to `master`. Until then, push to `master:main` on `vercel-repo`.
