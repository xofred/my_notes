```ruby
class Foo
  def test_method
    __method__
    # To return the method name as a string, call __method__.to_s instead.
  end
end
```

Reference: [Get the name of the currently executing method](https://stackoverflow.com/questions/199527/get-the-name-of-the-currently-executing-method)