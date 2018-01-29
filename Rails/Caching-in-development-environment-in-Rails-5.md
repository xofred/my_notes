```ruby
# environments/development.rb
if Rails.root.join('tmp/caching-dev.txt').exist?
  config.action_controller.perform_caching = true
  config.static_cache_control = "public, max-age=172800"
  #config.cache_store = :mem_cache_store
  config.cache_store = :readthis_store, {
    namespace: 'cache',
    redis: { url: REDIS_CONFIG['url'], driver: :hiredis, password: REDIS_CONFIG['password']  }
  }
else
  config.action_controller.perform_caching = false
  config.cache_store = :null_store
end
```
Then it will use specified cache_store like in staging or production. In this case for example, it's `readthis` 

Reference: [Caching in development environment in Rails 5](https://blog.bigbinary.com/2016/01/25/caching-in-development-environment-in-rails5.html)