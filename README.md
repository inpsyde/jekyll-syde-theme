<p align="center">
    <h1 align="center">Inpsyde Jekyll Theme</h1>
    <p align="center"></p>
</p>

![jekyll-inpsyde-theme](./jekyll-inpsyde-theme-screenshot.jpg)

## Installation

Add this line to your Jekyll site's Gemfile:

```ruby
gem "jekyll-inpsyde-theme"
```

And add this line to your Jekyll site's `_config.yml`:

```yaml
theme: jekyll-inpsyde-theme
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install jekyll-inpsyde-theme

Alternatively, you can run it inside Docker while developing your site

    $ docker-compose up

### Submitting code changes:

- Open a [Pull Request](https://github.com/inpsyde/jekyll-inpsyde-theme/pulls)
- Ensure all CI tests pass
- Await code review
- Bump the version number in `jekyll-inpsyde-theme.gemspec` and `package.json` according to [semantic versioning](https://semver.org/).

## Development

To set up your environment to develop this theme, run `bundle install`.

Your theme is set up just like a normal Jekyll site! To test your theme, run `bundle exec jekyll serve` and open your browser at `http://localhost:4000`. This starts a Jekyll server using your theme. Add pages, documents, data, etc. like normal to test your theme's contents. As you make modifications to your theme and to your content, your site will regenerate and you should see the changes in the browser after a refresh, just like normal.

When the theme is released, only the files in `_layouts`, `_includes`, and `_sass` tracked with Git will be released.

## License

The theme is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).
