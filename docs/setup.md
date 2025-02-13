---
nav_order: 1
---
# Setup
{: .no_toc }
## Table of contents
{: .no_toc .text-delta }
1. TOC
{:toc}
---

## File Structure

To use Github Pages you need to introduce a new directory called `docs` into your repository. This folder will contain multiple markdown files - each file represents a page - with your documentation. The structure will look like following:

```
.
├── docs
│   ├── .gitignore
│   ├── README.md
│   ├── _config.yml
│   ├── ...
│   ├── ...
│   └── some-markdown-file.md
├── ...
├── ...
└── README.md
```

Copy and paste the following boilerplates into the `docs` directory.

### .gitignore

```
_site
.sass-cache
.jekyll-cache
.jekyll-metadata
vendor

Gemfile
Gemfile.lock
gems.rb
gems.locked
```

### _config.yml

Replace `<YOUR_REPO_XXX>` with your repo details.

```yaml
title: <YOUR_REPO_TITLE>
description: <YOUR_REPO_DESCRIPTION>
baseurl: /<YOUR_REPO_NAME> # Your repo name with a leading slash.

# Aux links for the upper right navigation
aux_links:
  "<YOUR_REPO_TITLE> on GitHub":
    - https://github.com/inpsyde/<YOUR_REPO_NAME>

# Footer "Edit this page on GitHub" link text
gh_edit_repository: https://github.com/inpsyde/<YOUR_REPO_NAME> # Your repo GitHub URL

# Everything above is repo specific.

###############################################################

# This section is repo specific. These can be omitted if defaults make sense.

gh_edit_branch: <YOUR_REPO_DEFAULT_BRANCH> # The default branch of the repo. Default: main
gh_edit_source: docs # The directory containing the docs. Default: docs

###############################################################

# Everything below should be copy and pasted into package repos

remote_theme: inpsyde/jekyll-syde-theme

###############################################################

# Everything below should be copy and pasted into package repos
# To be replaced by jekyll-syde-theme's `_config.yml` when GitHub Pages supports Jekyll v4.

plugins:
  - jekyll-remote-theme
  - jekyll-seo-tag
  - jekyll-sitemap
  - jemoji

permalink: pretty
```

### README.md

The following is is an example of the site homepage.
Only the [front matter](https://jekyllrb.com/docs/front-matter/) matters.
Adjust page content with content make sense to your project.

````md
---
title: Home
nav_order: 0
permalink: /
---

# <YOUR_REPO_TITLE>

<YOUR_REPO_DESCRIPTION>

## Installation

The best way to use this package is:

```bash
composer require inpsyde/<YOUR_REPO_NAME>
```

## Copyright and License

This package is [free software](https://www.gnu.org/philosophy/free-sw.en.html) distributed under the terms of the GNU General Public License version 2 or (at your option) any later version. For the full license, see [LICENSE](./LICENSE).

## Contributing

All feedback / bug reports / pull requests are welcome.
````

To add more pages to the Jekyll site, see [Usage](./usage.md).

## Serve the Jekyll Site Locally

*This step is optional but recommanded. If you don't want to test on local machines, skip to [GitHub Pages](#github-pages).*

This starts a Jekyll server using your theme. Add pages, documents, data, etc. like normal to test your Jekyll site. As you make modifications to your theme and to your content, your site will regenerate and you should see the changes in the browser after a refresh, just like normal.

### Docker

```bash
cd <repo-root>/docs

# If they exist
rm Gemfile Gemfile.lock gems.rb gems.locked

docker run --rm -it \
  --volume "$PWD:/srv/jekyll" \
  --publish 4000:4000 \
  jekyll/minimal:pages \
  jekyll serve
```

Open your browser at `http://localhost:4000/<YOUR_REPO_NAME>`.

### Ruby

```bash
cd <repo-root>/docs

# If they exist
rm Gemfile Gemfile.lock gems.rb gems.locked

bundle init
bundle add --group=jekyll_plugins --version='>= 0' github-pages

bundle exec jekyll serve
```

Open your browser at `http://localhost:4000/<YOUR_REPO_NAME>`.

### Tips

#### Reloading `_config.yml`

For technical reasons, `_config.yml` is **not** reloaded automatically when you use `jekyll serve`. If you change it, please restart the server process.

####  `jekyll serve` Command Flags

Run `jekyll serve --help` for information about option flags. Notably:

| Flag            | Description                                       |
|:--------------- |:--------------------------------------------------|
| `--baseurl`     | Serve the website from the given base URL         |
| `--incremental` | Enable incremental rebuild                        |
| `--port`        | Port to listen on                                 |
| `--livereload`  | Use LiveReload to automatically refresh browsers  |
| `--open-url`    | Launch your site in a browser                     |

## GitHub Pages

### Setup

1. Commit `docs` and push to GitHub on the default branch (e.g: `main` or `master`)
1. On GitHub, navigate to your site's repository
1. Under your repository name, click **Settings**
1. In the left sidebar, click **Pages**, e.g: `https://github.com/inpsyde/<YOUR_REPO_NAME>/settings/pages`
1. Under the **Source** section, select your default branch (e.g: `main` or `master`) and the `docs` directory
  ![Github Pages Settings Source](./assets/images/github-pages-settings-source.png)
1. Your don't need to choose a theme nor to add a custom domain

The Jekyll site will be avaible at `https://inpsyde.github.io/<YOUR_REPO_NAME>` in a few minutes.

### Troubleshooting

> It can take up to 20 minutes for changes to your site to publish after you push the changes to GitHub. If your don't see your changes reflected in your browser after an hour, see "[About Jekyll build errors for GitHub Pages sites](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/about-jekyll-build-errors-for-github-pages-sites)."
>
> -- [GitHub Docs - Creating a GitHub Pages site with Jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/creating-a-github-pages-site-with-jekyll)

- The person who pushed the changes must have their email addresses verified on GitHub. For more information, see [Verifying your email address](https://docs.github.com/en/get-started/signing-up-for-github/verifying-your-email-address)
- If GitHub reports any Jekyll build error messages, [build your site locally](#serve-the-jekyll-site-locally) to see any misconfiguration
- Ask on the `#p-jekyll-syde-theme` Slack channel if you need further help

#### Purging GitHub Pages Cache

GitHub builds the docs whenever you push to the `main` or `master` branch. In case you want to force a rebuild or purge the caches, run the following:

```bash
curl -u <YOUR_GITHUB_USERNAME>:<YOUR_GITHUB_PERSONAL_ACCESS_TOKEN> -X POST https://api.github.com/repos/inpsyde/<YOUR_REPO_NAME>/pages/builds
```

The above command returns a URL for checking the build status. To check the build status, run the following:

```bash
curl -u <YOUR_GITHUB_USERNAME>:<YOUR_GITHUB_PERSONAL_ACCESS_TOKEN> -X GET https://api.github.com/repositories/<THE_REPO_ID_RETURNED_FROM_PREVIOUS_COMMAND>/pages/builds/latest
```
