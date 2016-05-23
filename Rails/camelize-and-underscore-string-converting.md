### camelize -> underscore

```ruby
"iAmCamel".underscore # => "i_am_camel"
```

### underscore -> camelize

```ruby
"i_am_underscore".camelize # => "IAmUnderscore"
"i_am_underscore".camelize(:lower) # => "iAmUnderscore"
```

Reference: 

- [Converting camel case to underscore case in ruby](http://stackoverflow.com/questions/1509915/converting-camel-case-to-underscore-case-in-ruby)
- [Converting string from snake case to camel case in ruby](http://stackoverflow.com/questions/9524457/converting-string-from-snake-case-to-camel-case-in-ruby)