Just add this to config/initializers/inflections.rb:

```ruby
ActiveSupport::Inflector.inflections do |inflect|
  inflect.irregular 'stadium', 'stadiums'
end
```

**Reference: [Rails creating wrong table name for model](http://stackoverflow.com/questions/15718681/rails-creating-wrong-table-name-for-model)**