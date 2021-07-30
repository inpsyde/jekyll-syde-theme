---
layout: default
title: Tests
has_children: true
nav_order: 100
permalink: /tests/
---

# Tests

 The main documentation pages of this theme illustrate the use of many of its features, which to some extent tests their implementation. The pages linked below provide further test cases for particular features, and may be useful for regression testing when developing new features.

The default configuration does not include the test pages. To include them, *commment-out* the following line in `_config.yml`:

```diff
  # _config.yml

  exclude:
    # Comment out the following line for local development
-   - "docs/tests/"
+   # - "docs/tests/"
```

(Apparently Jekyll's `include` does *not* override `exclude`  for the same folder...)
