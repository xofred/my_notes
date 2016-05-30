```ruby
user.attributes = {name: "Rob"}
```

This method will set all the attributes you pass it. The changes are not saved to the database. Any attributes you don’t pass will be left unchanged. You can also use assign_attributes:

```ruby
user.attributes = {name: "Rob", age: 12}
user.assign_attributes {name: "Rob", age: 12}
```
These are equivalent

Reference: [http://www.davidverhasselt.com/set-attributes-in-activerecord/](Different Ways to Set Attributes in ActiveRecord (Rails 4))