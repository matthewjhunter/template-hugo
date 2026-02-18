# template-hugo

GitHub template repository for Hugo sites. Provides a ready-to-use project structure with multi-file TOML configuration, Hugo modules support, Taskfile automation, and CI with link checking.

## What's Included

- **Multi-file TOML config** — `config/_default/` splits Hugo configuration into `hugo.toml`, `menus.toml`, and `params.toml` for clarity
- **Hugo modules** — `go.mod` is ready for module-based theme management (no git submodules)
- **Taskfile** — Common commands (`dev`, `build`, `new`) available via [Task](https://taskfile.dev)
- **CI pipeline** — GitHub Actions builds the site with Hugo and checks for broken links with [hugo-link-checker](https://github.com/infodancer/hugo-link-checker)
- **Dependabot** — Automated weekly updates for GitHub Actions and Go modules

## Usage

1. Click **Use this template** on GitHub (or `gh repo create --template matthewjhunter/template-hugo`)
2. Clone your new repository
3. Update `config/_default/hugo.toml`:
   - Set `baseURL` to your site's URL
   - Set `title` to your site's name
   - Uncomment the `[module]` block and add your theme
4. Install the theme module:
   ```bash
   hugo mod get
   ```
5. Start the dev server:
   ```bash
   task dev
   ```

## Project Structure

```
├── archetypes/         Front matter templates for new content
├── assets/             Processed assets (SCSS, JS)
├── config/_default/    Multi-file Hugo configuration
├── content/posts/      Site content
├── layouts/            Template overrides
├── static/             Static files (copied as-is)
├── Taskfile.yml        Task automation
└── go.mod              Hugo modules support
```

## Tasks

| Command | Description |
|---------|-------------|
| `task dev` | Start Hugo dev server with drafts enabled |
| `task build` | Build site for production with minification |
| `task new -- slug` | Create a new post from the archetype |

## CI

The CI pipeline runs on pushes to `main` and on pull requests:

1. **Build** — Installs Hugo (extended) and Go, runs `hugo --minify`, uploads `public/` as an artifact
2. **Link check** — Downloads the built site and runs `hugo-link-checker` to catch broken internal and external links

## License

MIT
