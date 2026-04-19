source "https://rubygems.org"

# Modern Jekyll 4 toolchain — built via .github/workflows/pages.yml, NOT
# GH Pages' built-in (frozen-at-3.10) builder. The legacy builder cannot
# resolve this template's vendored SCSS partials.

gem "jekyll", "~> 4.3"
# Pin to 2.x: this template's vendored SCSS uses partial-resolution
# patterns that Dart Sass (sass-converter 3.x) rejects but LibSass
# (2.x) accepts. Migrating @imports → @use is a larger refactor.
gem "jekyll-sass-converter", "~> 2.2"
gem "webrick", "~> 1.8"

group :jekyll_plugins do
  gem "jekyll-feed"
  gem "jekyll-sitemap"
  gem "jekyll-paginate"
  gem "jekyll-gist"
  gem "jekyll-redirect-from"
  gem "jekyll-include-cache"
end
