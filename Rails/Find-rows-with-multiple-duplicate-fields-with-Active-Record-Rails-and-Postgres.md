```ruby
User.select(:first,:email).group(:first,:email).having("count(*) > 1")

# Also, this is a little unrelated but handy. If you want to see how times each combination was found, put .count at the end:
User.select(:first,:email).group(:first,:email).having("count(*) > 1").size
```

Reference: [Find rows with multiple duplicate fields with Active Record, Rails & Postgres](https://stackoverflow.com/questions/21669202/find-rows-with-multiple-duplicate-fields-with-active-record-rails-postgres)