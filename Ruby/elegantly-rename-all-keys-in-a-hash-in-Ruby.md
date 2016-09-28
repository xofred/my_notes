 have a Ruby hash:

```ruby
ages = { "Bruce" => 32,
         "Clark" => 28
       }
```

Assuming I have another hash of replacement names, is there an elegant way to rename all the keys so that I end up with:

```ruby
ages = { "Bruce Wayne" => 32,
         "Clark Kent" => 28
       }
```

Solution:

```ruby
ages = { "Bruce" => 32, "Clark" => 28 }
mappings = {"Bruce" => "Bruce Wayne", "Clark" => "Clark Kent"}

ages.map {|k, v| [mappings[k], v] }.to_h
```

Reference: [How to elegantly rename all keys in a hash in Ruby? [duplicate]](http://stackoverflow.com/questions/4137824/how-to-elegantly-rename-all-keys-in-a-hash-in-ruby)