source "https://rubygems.org"

# Built and deployed by .github/workflows/pages.yml; locally run
# `bundle exec jekyll serve`. The Ruby version comes from .ruby-version.
gem "jekyll", "~> 4.4"

# Ruby 4.0 no longer ships logger as a default gem and Jekyll 4.4.1 does not
# declare it (jekyll/jekyll#9915; fixed on master by #9920, not yet released).
gem "logger"

group :jekyll_plugins do
  gem "jekyll-redirect-from"
  gem "jekyll-relative-links"
end

group :test do
  gem "html-proofer", "~> 5.2"
end
