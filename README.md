# Project Log

A GitHub Pages site that catalogs your projects as index cards. Click
a card, get the full doc. Built with Jekyll, which GitHub Pages runs
natively — no build step, no npm install.

## 1. Get it on GitHub Pages

**Option A — this is your `username.github.io` repo**
1. Create a repo named exactly `yourusername.github.io`.
2. Push everything in this folder to it (root of the repo).
3. In the repo, go to **Settings → Pages** and confirm the source is
   the `main` branch, root folder. (Usually auto-detected.)
4. Your site is live at `https://yourusername.github.io`.

**Option B — a project repo (e.g. `github.com/you/project-log`)**
1. Push this folder to that repo.
2. Open `_config.yml` and set:
   ```yaml
   baseurl: "/project-log"   # your repo name, with leading slash
   ```
3. Settings → Pages → source: `main` branch, root folder.
4. Live at `https://yourusername.github.io/project-log`.

Either way, GitHub rebuilds the site automatically a minute or two
after every push — nothing to run locally unless you want a preview.

## 2. Add a new project (the whole point)

1. Copy `project-template.md` into the `_projects/` folder.
2. Rename it to your project's slug, e.g. `_projects/weather-cli.md`.
   The filename becomes the URL: `/projects/weather-cli/`.
3. Fill in the front matter (the part between `---`) and write the
   doc in Markdown below it.
4. Commit and push. It appears on the homepage automatically, newest
   first — no other file needs to change.

That's the entire workflow. No registering the page anywhere else,
no editing `index.html`.

### Front matter fields

| Field     | Required | Notes                                          |
|-----------|----------|-------------------------------------------------|
| `title`   | yes      | Shown on the card and the doc page              |
| `summary` | yes      | One sentence, shown on the card                 |
| `status`  | yes      | `Active`, `Shipped`, `Archived`, or `Experiment`|
| `date`    | yes      | `YYYY-MM-DD`, controls sort order on homepage   |
| `stack`   | no       | List of languages/frameworks, e.g. `[Rust, CLI]`|
| `tags`    | no       | List of freeform tags                           |
| `repo`    | no       | Link to the source repo                         |
| `demo`    | no       | Link to a live version                          |

## 3. Preview locally (optional)

Only needed if you want to see changes before pushing.

```bash
gem install bundler jekyll
bundle init
echo 'gem "github-pages", group: :jekyll_plugins' >> Gemfile
bundle install
bundle exec jekyll serve
# open http://localhost:4000
```

## 4. Customize

- **Site name / description / your GitHub handle** — edit the top of
  `_config.yml` (`title`, `description`, `github_username`).
- **Colors, type, layout** — everything is in
  `assets/css/style.css`, driven by CSS variables at the top of the
  file (`--paper`, `--ink`, `--stamp-red`, etc.).
- **Two example entries** (`weather-cli.md`, `recipe-vault.md`) are
  in `_projects/` — delete them once you've added your own, or keep
  them as formatting references.

## File map

```
_config.yml           site settings, collection config
_layouts/
  default.html         header, footer, font loading
  project.html          single-project doc page
_projects/              ← your project docs live here
index.html             homepage — auto-lists everything in _projects/
project-template.md    copy this to start a new project doc
assets/css/style.css   all visual styling
```
