---
nav_order: 1
---
# Local Development
{: .no_toc }
## Table of contents
{: .no_toc .text-delta }
1. TOC
{:toc}
---

## Clone the Git Repository

```bash
git clone https://github.com/inpsyde/jekyll-inpsyde-theme
```

## Serve the Jekyll Site Locally

This starts a Jekyll server using your theme. Add pages, documents, data, etc. like normal to test your theme's contents. As you make modifications to your theme and to your content, your site will regenerate and you should see the changes in the browser after a refresh, just like normal.

When the theme is released, only the files in `_layouts`, `_includes`, `_sass` and `assets` tracked with Git will be released.

### Docker

```bash
cd <repo-root>

# If they exist
rm Gemfile Gemfile.lock

docker run --rm -it \
  --volume "$PWD:/srv/jekyll" \
  --publish 4000:4000 \
  jekyll/minimal:pages \
  jekyll serve -c docs/_config.yml,_config.yml
```

Open your browser at `http://localhost:4000/jekyll-inpsyde-theme/docs/`.

### Ruby

```bash
cd <repo-root>

# If they exist
rm Gemfile Gemfile.lock

bundle init
bundle add --group=jekyll_plugins --version='>= 0' github-pages

bundle exec jekyll serve -c docs/_config.yml,_config.yml
```

Open your browser at `http://localhost:4000/jekyll-inpsyde-theme/docs/`.

## Test Content

Test content at [`docs/tests`](https://github.com/inpsyde/jekyll-inpsyde-theme/tree/master/docs/tests) are excluded by default. If you wish to use them during development:

First, comment out this line in [`_config.yml`](https://github.com/inpsyde/jekyll-inpsyde-theme/blob/master/_config.yml) at repo root:

```diff
  # _config.yml

  exclude:
    # Comment out the following line for local development
-   - "docs/tests/"
+   # - "docs/tests/"
```

Then, restart the Jekyll server.

Test content is avaible at [http://localhost:4000/jekyll-inpsyde-theme/docs/tests/index.html](./tests/)

## `_config.yml` vs `docs/_config.yml`

[`docs/_config.yml`](https://github.com/inpsyde/jekyll-inpsyde-theme/blob/master/docs/_config.yml) is for generating https://inpsyde.github.io/jekyll-inpsyde-theme on GitHub Pages.

[`_config.yml`](https://github.com/inpsyde/jekyll-inpsyde-theme/blob/master/_config.yml) at repo root is for generating http://localhost:4000/jekyll-inpsyde-theme/docs for local development.

Whenever duplicated, [`_config.yml`](https://github.com/inpsyde/jekyll-inpsyde-theme/blob/master/_config.yml) at repo root takes priority.

## Tips

### Reloading `_config.yml`

For technical reasons, [`_config.yml`](https://github.com/inpsyde/jekyll-inpsyde-theme/blob/master/_config.yml) and [`docs/_config.yml`](https://github.com/inpsyde/jekyll-inpsyde-theme/blob/master/docs/_config.yml) are **not** reloaded automatically when you use `jekyll serve`. If you change those files, please restart the server process.


###  `jekyll serve` Command Flags

Run `jekyll serve --help` for information about option flags. Notably:

| Flag            | Description                                       |
|:--------------- |:--------------------------------------------------|
| `--baseurl`     | Serve the website from the given base URL         |
| `--incremental` | Enable incremental rebuild                        |
| `--port`        | Port to listen on                                 |
| `--livereload`  | Use LiveReload to automatically refresh browsers  |

### GitHub Pages Dependencies

We rely on [GitHub Pages](https://docs.github.com/en/pages) to generate and host the Jekyll sites to avoid maintenance overheads. Thus, only GitHub Pages [allowed dependencies](https://pages.github.com/versions/) can be used.
