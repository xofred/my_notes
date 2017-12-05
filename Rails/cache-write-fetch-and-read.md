### write, fetch, and read
```ruby
class Product < ApplicationRecord
  def competing_price
    # write will always update cache
    # fetch won't if cache found
    Rails.cache.write(price_cache_key, expires_in: 12.hours) do
      Competitor::API.find_price(id)
    end
  end

  def get_competing_price
    # read
    Rails.cache.read price_cache_key
  end
end

private
def price_cache_key
  "#{cache_key}/competing_price"
end
```

### Caching in Development

It's common to want to test the caching strategy of your application in developement mode. Rails provides the rake task dev:cache to easily toggle caching on/off.
```
$ bin/rails dev:cache
Development mode is now being cached.
$ bin/rails dev:cache
Development mode is no longer being cached.
```

Reference: [Caching with Rails: An Overview — Ruby on Rails Guides](http://guides.rubyonrails.org/caching_with_rails.html#basic-caching)