# Claude Code Instructions

## Local Development Server

This is a Jekyll site. To run a local test server **without polluting the repo**:

1. **Initialize rbenv** (required — the system Ruby is too old and doesn't have gems):
   ```
   eval "$(rbenv init -)"
   ```

2. **Install gems into `vendor/bundle`** (already gitignored):
   ```
   bundle config set --local path 'vendor/bundle'
   bundle install
   ```

3. **Create a dev config overlay** (in `/tmp`, not in the repo) to force localhost URLs. Without this, the `github-pages` gem resolves `site.url` to the production domain and links redirect to prod:
   ```
   cat > /tmp/_config_dev.yml << 'EOF'
   url: "http://127.0.0.1:4000"
   baseurl: ""
   EOF
   ```

4. **Serve with build output redirected to a temp directory** so `_site/` in the repo is not touched:
   ```
   TMPDIR=$(mktemp -d)
   bundle exec jekyll serve --destination "$TMPDIR/_site" --livereload --host 127.0.0.1 --config _config.yml,/tmp/_config_dev.yml
   ```
   This builds into `/tmp/...` instead of the repo's `_site/` directory, and the config overlay keeps all URLs pointing to localhost.

Key points:
- **Never run `bundle exec jekyll serve` without `--destination`** — it writes into `_site/` which is gitignored but still creates noise in `git status`.
- `vendor/`, `.bundle/`, `Gemfile.lock`, `_site/`, `.sass-cache/`, `.jekyll-cache/` are all in `.gitignore`.
- The project uses **rbenv** with Ruby 3.3.4 (set via `.ruby-version`).
- Do not install gems globally or with `sudo` — always use `vendor/bundle`.

## Project Structure

- Jekyll site for workingpaper.co
- Menu configuration lives in `_data/settings.yml` under `menu_settings.menu_items`
- Menu items can have nested `children` arrays for dropdown submenus
- SCSS uses `@include mq(tabletl)` for the desktop breakpoint (1024px)
- JS uses jQuery (available globally as `$`)

## Adding or Removing a Team Member

When adding or removing a team member, update **all** of the following:

1. **Bio page** – Create or remove `_pages/{firstname}-{lastname}.html` (hero section with title/role, portrait image from `/images/`, bio text, and "Contact {Name}" button)
2. **Menu** – Add or remove entry under `menu_settings.menu_items > Team > children` in `_data/settings.yml`
3. **Team page** – Add or remove entry in `_pages/team.md` (name as `h3` link with `→` arrow, job title as plain text, and booking button if applicable)
4. **Calendar booking page** – If the member should have a booking page, create or remove `_pages/calendar-{firstname}.md` and add a `<a class="button button--small">` booking button on the team page. Also add or remove their entry on the **calendar directory page** (`_pages/calendar.md`), which lists all bookable team members.
5. **Photo** – Ensure portrait image exists at `/images/{firstname}-{lastname}.jpg` (or `.png`)
