# Publishing to Brad Barrish's Documentation from Obsidian

This repo is a Jekyll/GitHub Pages site. Publishing from Obsidian is file-based:

1. Templater creates a Markdown file in `_posts/`.
2. You write the post in plain Markdown.
3. Obsidian Git commits and syncs the repo.
4. GitHub Pages builds `https://docs.bradbarrish.com/`.

Verified on 2026-07-16:

- GitHub repository: `bradbarrish/documentation`
- Default branch: `master`
- GitHub Pages source: `master` branch, repository root
- GitHub Pages status: built
- Custom domain: `docs.bradbarrish.com`
- HTTPS: enforced
- Latest Pages build at verification time: commit `1f488ac2130dc313c85eb4b890f4cc33785acc0b`, pushed on 2025-10-04

## Setting up on a new machine

Current local setup:

- Git clone: `/Users/bradbarrish/Projects/bb-docs`
- `bbOS` vault link: `/Users/bradbarrish/Vaults/bbOS/bb-docs`
- Vault-level Templater copy: `/Users/bradbarrish/Vaults/bbOS/Templates/bb-docs Post.md`

Clone the repo so Obsidian can see it:

```sh
cd /Users/bradbarrish/Projects
git clone https://github.com/bradbarrish/documentation.git bb-docs
```

If you want it inside the `bbOS` vault like `a.littlesometh.ing`, clone it there or link the project clone into the vault:

```sh
ln -s /Users/bradbarrish/Projects/bb-docs /Users/bradbarrish/Vaults/bbOS/bb-docs
```

Confirm the folder is a real git clone:

```sh
cd /Users/bradbarrish/Projects/bb-docs
git status
```

## One-time Obsidian setup

Use either setup:

- Open `/Users/bradbarrish/Projects/bb-docs` directly as an Obsidian vault.
- Or expose this repo as `bb-docs` inside the `bbOS` vault and set Obsidian Git's custom base path to `bb-docs`.

Install and enable these community plugins:

- Templater
- Obsidian Git

Templater:

- Template folder location: `Templates` when opening `bb-docs` directly.
- Template folder location: `bb-docs/Templates` when opening the parent `bbOS` vault.

Obsidian Git:

- Custom base path: blank when opening `bb-docs` directly.
- Custom base path: `bb-docs` when opening the parent `bbOS` vault.
- Auto pull on startup: recommended.
- Auto commit-and-sync: leave off unless you intentionally want every change published.

## Writing a post

1. Run **Templater: Create new note from template**.
2. Choose **bb-docs Post**.
3. Enter the post title.
4. Templater creates `_posts/YYYY-MM-DD-slug.md`.
5. Write the body in plain Markdown.

Do not use Obsidian's core **Templates: Insert template** command for this template. It will paste the raw `<%* ... %>` code instead of running it.

## Publishing

1. Run **Obsidian Git: Pull** if you may have published from another machine.
2. Run **Obsidian Git: Commit-and-sync**.
3. Obsidian Git pushes to `master`.
4. GitHub Pages should rebuild the site within about a minute.

## Local verification

Use Homebrew Ruby instead of the macOS system Ruby:

```sh
export PATH="/opt/homebrew/opt/ruby@3.4/bin:$PATH"
bundle install
bundle exec jekyll build
```

The dependency lock was refreshed on 2026-07-16 from `github-pages 203` to `github-pages 232`, and `bundle exec jekyll build` passed locally after the update.

## House rules

- Plain Markdown only: use `[text](url)` links instead of wikilinks.
- Put post images in `assets/` and reference them as `/assets/file-name.jpg`.
- Put Open Graph images in `assets/og/` and set `ogimage:` to the file name.
- Keep `description:` to one sentence when you want a better social preview.

## Troubleshooting

- If Obsidian Git says this is not a git repo, the folder was copied instead of cloned. Re-clone it from `https://github.com/bradbarrish/documentation.git`.
- If a new post shows raw Templater code, recreate it with **Templater: Create new note from template**.
- If the site does not update, check the GitHub Pages build for `bradbarrish/documentation`.
- If local Jekyll commands use the macOS system Ruby and fail on Bundler, use Homebrew Ruby first: `export PATH="/opt/homebrew/opt/ruby@3.4/bin:$PATH"`.
