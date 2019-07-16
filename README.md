# goto null;

An untitled website.

## Development

**Setup:**

```sh
brew install ruby
gem install bundler
mkdir -p vendor/bundler
bundle install --path vendor/bundle
```

**Run:**

```sh
bundle exec jekyll serve
```

**Adding a plugin:**

1. Add to Gemfile:

```
gem 'my-plugin', group: :jekyll_plugins
```

2. Get bundle to install

```sh
bundle install --path vendor/bundle
```

3. Update `_config.yml`:

```yml
plugins:
  - my-plugin
```

Favicon from https://favicon.io/favicon-generator/:

* Font family: Share Tech Mono

## Help

https://jekyllrb.com/docs/
