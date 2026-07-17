# Brad Barrish's Documentation

This is the source for `https://docs.bradbarrish.com/`. It is a Jekyll site hosted with GitHub Pages.

Current GitHub Pages settings:

- Repository: `bradbarrish/documentation`
- Default branch: `master`
- Pages source: `master` branch, repository root
- Custom domain: `docs.bradbarrish.com`
- HTTPS: enforced

## Publishing from Obsidian

The repo includes an Obsidian Templater template at `Templates/bb-docs Post.md`.

See [docs/obsidian-publishing.md](docs/obsidian-publishing.md) for setup and day-to-day publishing notes. The short version:

1. Run **Templater: Create new note from template** and choose **bb-docs Post**.
2. Write the post in plain Markdown.
3. Run **Obsidian Git: Commit-and-sync**.
4. GitHub Pages builds and publishes the site from the `master` branch.

## Local development

```sh
export PATH="/opt/homebrew/opt/ruby@3.4/bin:$PATH"
bundle install
bundle exec jekyll build
bundle exec jekyll serve
```

## Site structure

This site uses a lightly edited version of Clio, a template and theme based on [danromero.org](https://danromero.org). The template supports:

1. A homepage that displays a brief introduction and the most recent blog posts in reverse chronological order.
2. An about page located at `/about/`.
3. A sample blog post.
4. An RSS feed for all of the blog posts.

## Original template setup notes

1. Clone the repository. Delete `screenshot.png` from the main folder.
2. Edit `_config.yml`. Replace the sample text for title, email, description, url, and twitter.
3. Enable GitHub Pages in the repository's settings. If you are planning to use a custom domain, you can also set that up on the settings page.
4. Add future **posts** as Markdown `(.md)` files to the `_posts` folder. GitHub Pages will automatically generate the HTML.
5. Add future **pages** (like the `/about/` page) as Markdown `(.md)` files to the main folder. GitHub Pages will automatically generate the HTML.
6. **Update the images** in the `/assets/` folder. **If you don't, your site will be represented by a purple square.** 🙂
67. Add future images to the `/assets/` folder. 

## Open Graph images
The template is set up to support Open Graph images for services like [Twitter](https://developer.twitter.com/en/docs/tweets/optimize-with-cards/guides/getting-started). Be sure to add the image name in the [front matter](https://jekyllrb.com/docs/front-matter/) of the blog posts and the images should be uploaded to the `/assets/og/` folder. The Hello World! sample post has a functioning example.

## Google Analytics
You can add the Javascript into the `default.html` [layout](https://jekyllrb.com/docs/layouts/) right above the `</body>` tag.

## Why is it called Clio?
[Answer](https://en.wikipedia.org/wiki/Clio).
