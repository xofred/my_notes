```ruby
require 'json'

my_hash = {:hello => "goodbye"}
puts JSON.generate(my_hash) => "{\"hello\":\"goodbye\"}"
```

Or an alternative way:

```ruby
require 'json'
puts {:hello => "goodbye"}.to_json => "{\"hello\":\"goodbye\"}"
```

JSON.generate only allows objects or arrays to be converted to JSON syntax. to_json, however, accepts many Ruby classes even though it acts only as a method for serialization:

```ruby
require 'json'

1.to_json => "1"
```

Reference: [Module: JSON (Ruby 2.0.0) ](http://ruby-doc.org/stdlib-2.0.0/libdoc/json/rdoc/JSON.html)