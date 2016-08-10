In `application.rb` file:

```ruby
# Autoload lib/ folder including all subdirectories
config.autoload_paths += Dir["#{config.root}/lib/**/"]
```

[Rails: Can't access a module in my lib directory](http://stackoverflow.com/questions/18392708/rails-cant-access-a-module-in-my-lib-directory)