You can then use the sale_info value from an instance of the Model class to access the integer value for that instance:
```ruby
my_model = Model.find(123)
Model.sale_infos[my_model.sale_info] # Returns the integer value
```

Reference: [How get integer value from a enum in Rails?](http://stackoverflow.com/questions/25570209/how-get-integer-value-from-a-enum-in-rails)