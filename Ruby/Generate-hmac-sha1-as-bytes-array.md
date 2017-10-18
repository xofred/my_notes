```ruby
mac = OpenSSL::HMAC.digest("sha1", key, encoded_data)
signed_integer_array = mac.unpack('c*') # 8-bit signed (signed char)
```

Reference:

[Convert a string of 0-F into a byte array in Ruby](https://stackoverflow.com/questions/3772410/convert-a-string-of-0-f-into-a-byte-array-in-ruby)

[Class: Array (Ruby 2.2.0) ](https://ruby-doc.org/core-2.2.0/Array.html#method-i-pack)