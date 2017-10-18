```ruby
mac = OpenSSL::HMAC.digest("sha1", key, encoded_data)
signed_integer_array = mac.unpack('c*') # 8-bit signed (signed char)
```

Reference:

[Convert a string of 0-F into a byte array in Ruby](https://stackoverflow.com/questions/3772410/convert-a-string-of-0-f-into-a-byte-array-in-ruby)

[Class: OpenSSL::HMAC (Ruby 2.1.0) ](http://ruby-doc.org/stdlib-2.1.0/libdoc/openssl/rdoc/OpenSSL/HMAC.html)

[Class: Array (Ruby 2.2.0) ](https://ruby-doc.org/core-2.2.0/Array.html#method-i-pack)