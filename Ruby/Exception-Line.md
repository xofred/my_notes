```ruby
# ensure.rb
begin
  1 / 0
rescue => e
  p e.backtrace
end

# #<ZeroDivisionError: divided by 0>
# ["ensure.rb:2:in `/'", "ensure.rb:2:in `<main>'"]
```

Reference: [Catching line numbers in ruby exceptions](http://stackoverflow.com/questions/119286/catching-line-numbers-in-ruby-exceptions)