---
nav_order: 1
---
# Usage
{: .no_toc }
## Table of contents
{: .no_toc .text-delta }
1. TOC
{:toc}
---

This theme is originally forked form [Just the Docs](https://github.com/pmarsceill/just-the-docs). Refer to its [documentation](https://pmarsceill.github.io/just-the-docs/) for more information.

## Creating Pages

Each markdown file under the `docs` directory is generated as a page on the Jekyll site.

```
.
├── README.md   # => (Homepage) https://inpsyde.github.io/example/
├── setup.md    # => https://inpsyde.github.io/example/setup/
└── usage.md    # => https://inpsyde.github.io/example/usage/
```

Here is some example markdown files you can copy and paste into your `docs` directory.

### Homepage (README.md)

Name the homepage markdown file as `README.md` instead of `index.md` so that GitHub would render them at `https://github.com/inpsyde/<YOUR_REPO_NAME>/tree/main/docs`.

`permalink: /` is to tell Jekyll generates this file as `index.html`.

```
---
title: "Home"
nav_order: 0
permalink: /
---

# Your Project Title

Lorem ipsum dolor sit amet, consectetur adipiscing elit.
```

### Page without Table of Content

```md
---
nav_order: 123
---

# Your Titile

Lorem ipsum dolor sit amet, consectetur adipiscing elit.

## Your Subtitle

Nullam finibus purus elit, eu dictum magna gravida a. Nam finibus, leo eu lacinia interdum, turpis velit tincidunt diam, sit amet fermentum ipsum tortor ut ante. Suspendisse non neque massa. Maecenas orci metus, ultricies eu odio lobortis, tristique finibus ipsum.
```

### Page with Table of Content

```md
---
nav_order: 123
---
# Your Titile
{: .no_toc }
## Table of contents
{: .no_toc .text-delta }
1. TOC
{:toc}
---

Lorem ipsum dolor sit amet, consectetur adipiscing elit.

## Your Subtitle

Nullam finibus purus elit, eu dictum magna gravida a. Nam finibus, leo eu lacinia interdum, turpis velit tincidunt diam, sit amet fermentum ipsum tortor ut ante. Suspendisse non neque massa. Maecenas orci metus, ultricies eu odio lobortis, tristique finibus ipsum.
```

## Front Matter

Any file that contains a YAML front matter block will be processed by Jekyll as a special file. The front matter must be the first thing in the file and must take the form of valid YAML set between triple-dashed lines. Here is a basic example:

```yaml
---
# If omitted, first heading (e.g: <h1>, <h2>, etc) will be used.
title: "Home"
# To control left navigation sidebar ordering
nav_order: 0
# Only use it on README.md to customise the URL.
permalink: /
---
```

For this theme, front matter blocks are optional.

Learn more at [Jekyll - Front Matter](https://jekyllrb.com/docs/front-matter/).

### Left Navigation Sidebar

By default, all pages will appear as top level pages in the main nav unless a parent page is defined.

You can use the `nav_order` parameter in your pages' YAML front matter.

```yaml
---
nav_order: 123
---
```

When you omit nav_order parameters, they default to the titles of the pages, which are ordered alphabetically.

For specific pages that you do not wish to include in the main navigation, e.g. a 404 page or a landing page, use the `nav_exclude: true` parameter in the YAML front matter for that page.

```yaml
---
nav_exclude: true
---
```

Learn more at [Just the Docs - Navigation Structure](https://pmarsceill.github.io/just-the-docs/docs/navigation-structure/).

## Tips

### Markdown and UI Component

Jekyll uses [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).
To see how they are rendered in this theme, refer to Just the Docs' [UI Components](https://pmarsceill.github.io/just-the-docs/docs/ui-components) documentation.

### Jekyll Blog (Posts)

[Jekyll Blog (posts)](https://jekyllrb.com/docs/posts/) is not in use. Do not place any files under the `docs/_posts` or `docs/_drafts` directories.
