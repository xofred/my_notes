```ruby
begin
  # something which might raise an exception
rescue SomeExceptionClass => some_variable
  # code that deals with some exception
rescue SomeOtherException => some_other_variable
  # code that deals with some other exception
else
  # code that runs only if *no* exception was raised
ensure
  # ensure that this code always runs, no matter what
end
```

Reference: [Begin, Rescue and Ensure in Ruby?](http://stackoverflow.com/questions/2191632/begin-rescue-and-ensure-in-ruby)