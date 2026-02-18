# template-hugo

Hugo site template with multi-file TOML config, Hugo modules, and CI.

## Build

```bash
# Dev server with drafts
task dev

# Production build
task build

# Create a new post
task new -- my-post-title
```

## Test

```bash
# Build and verify
hugo --minify
```

## CI

GitHub Actions runs `hugo --minify` then `hugo-link-checker` on every push to `main` and on PRs.

## First-Use Checklist

After creating a repo from this template:

1. Update `baseURL` and `title` in `config/_default/hugo.toml`
2. Add a Hugo module theme (uncomment and edit the `[module]` block in `hugo.toml`, then run `hugo mod get`)
3. Configure `config/_default/params.toml` with theme-specific parameters
4. Set up navigation in `config/_default/menus.toml`
5. Replace `content/posts/hello-world.md` with real content
6. Update this `CLAUDE.md` with project-specific instructions
