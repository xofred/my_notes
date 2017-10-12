### yarn

I've node installed before, so I need yarn only.

```shell
brew install yarn --without-node
```

### webpacker

Add webpacker to Gemfile

```ruby
gem 'webpacker', '~> 3.0'
```

```shell
bundle exec rails webpacker:install
```

### webpack dev server

In development, other than rails server, we also need a webpack dev server, for live code reloading.

```shell
./bin/webpack-dev-server
```

### view

Include es6 code using `javascript_pack_tag`

```erb
<%= javascript_pack_tag 'application' %>
```

### Deployment

Webpacker hooks up a new webpacker:compile task to assets:precompile, which gets run whenever you run assets:precompile. If you are not using sprockets you can manually trigger NODE_ENV=production bundle exec rails webpacker:compile during your app deploy.

---

Reference: 

[Webpacker](https://github.com/rails/webpacker)

[Rails Rails 5.1 使用 yarn 和 webpack 实战 (vue, 构建等)](https://ruby-china.org/topics/32904)
