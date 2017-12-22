```ruby
# followers_count is a calculated value of model User
performers = User.reporter.sort_by(&:followers_count).reverse.first(10)
```

Reference: [Sorting a Rails Resource Based on a Calculated Value](http://awaxman11.github.io/blog/2013/10/11/sorting-a-rails-resource-based-on-a-calculated-value/)