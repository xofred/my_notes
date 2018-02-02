```ruby
Rails.cache.write('dummy_one', 1)
Rails.cache.write('dummy_two', 2)

Rails.cache.delete_matched("dummy*") # => 2
```

Reference: [rails how to delete cache key using partial match](https://stackoverflow.com/questions/19603598/rails-how-to-delete-cache-key-using-partial-match)