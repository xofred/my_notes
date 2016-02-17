Add `bootstrap` to your Gemfile:

```ruby
gem 'bootstrap', '~> 4.0.0.alpha3'
```

Ensure that `sprockets-rails` is at least v2.3.2.

`bundle install` and restart your server to make the files available through the pipeline.

Import Bootstrap styles in `app/assets/stylesheets/application.scss`:

```scss
// Custom bootstrap variables must be set or import before bootstrap itself.
@import "bootstrap";
```

Make sure the file has `.scss` extension (or `.sass` for Sass syntax). If you have just generated a new Rails app,
it may come with a `.css` file instead. If this file exists, it will be served instead of Sass, so rename it:

```console
$ mv app/assets/stylesheets/application.css app/assets/stylesheets/application.scss
```

Then, remove all the `*= require` and `*= require_tree` statements from the Sass file. Instead, use `@import` to import Sass files.

Do not use `*= require` in Sass or your other stylesheets will not be able to access the Bootstrap mixins and variables.

Require Bootstrap Javascripts in `app/assets/javascripts/application.js`:

```js
//= require jquery
//= require bootstrap-sprockets
```

While `bootstrap-sprockets` provides individual Bootstrap components for ease of debugging, you may alternatively require the concatenated `bootstrap` for faster compilation:

```js
//= require jquery
//= require bootstrap
```

Tooltips and popovers depend on [tether][tether] for positioning.
If you use them, add tether to the Gemfile:

```ruby
source 'https://rails-assets.org' do
  gem 'rails-assets-tether', '>= 1.1.0'
end
```

Then, run `bundle`, restart the server, and require tether before bootstrap but after jQuery:

```js
//= require jquery
//= require tether
//= require bootstrap-sprockets
```



Reference: [Bootstrap Ruby gem](https://github.com/twbs/bootstrap-rubygem)