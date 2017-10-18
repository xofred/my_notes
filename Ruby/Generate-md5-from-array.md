```ruby
Digest::MD5.hexdigest [1].pack 'U*'
```
`U` means UTF-8 character

`*` means all member of that array

[how md5 byte array in ruby?](https://stackoverflow.com/questions/42579488/how-md5-byte-array-in-ruby)

[Class: Array (Ruby 2.2.0) ](https://ruby-doc.org/core-2.2.0/Array.html#method-i-pack)