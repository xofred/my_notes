All of these should work:
```ruby
user[attribute_name]
user.read_attribute(attribute_name)
user.send(attribute_name)
```

Reference: [get attribute of ActiveRecord object by string](https://stackoverflow.com/questions/11808949/get-attribute-of-activerecord-object-by-string)