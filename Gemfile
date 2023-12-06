# frozen_string_literal: true

source "https://rubygems.org"

gem "jekyll-theme-chirpy", "~> 6.3", ">= 6.3.1"

group :test do
  gem "html-proofer", "~> 4.4"
end

# Plugins of this site loaded during a build with proper
# site configuration.
gem "jekyll-gist"
gem "jekyll-coffeescript"
gem "jekyll-seo-tag", "~> 2.8"
gem "jekyll-admin"


# Windows and JRuby does not include zoneinfo files, so bundle the tzinfo-data gem
# and associated library.
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
end

# Performance-booster for watching directories on Windows
gem "wdm", "~> 0.1.1", :platforms => [:mingw, :x64_mingw, :mswin]

# Lock `http_parser.rb` gem to `v0.6.x` on JRuby builds since newer versions of the gem
# do not have a Java counterpart.
gem "http_parser.rb", "~> 0.6.0", :platforms => [:jruby]


# Gems loaded irrespective of site configuration.
group :jekyll_plugins do
  gem "jekyll-cli-plus"
  gem "jekyll-seo-tag", "~> 2.8"
  gem "jekyll-admin"
end