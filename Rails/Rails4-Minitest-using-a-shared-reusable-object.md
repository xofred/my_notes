Do
```ruby
def category
  @category ||= Category.new(name:'Homey')
end
```
Then only use category not @category

Reference: [Rails4 Minitest | using a shared reusable object](https://stackoverflow.com/questions/29928596/rails4-minitest-using-a-shared-reusable-object)