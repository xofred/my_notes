```ruby
class Person

  def self.get_name
    persons_name
  end

  class << self

    private

    def persons_name
      "Sam"
    end
  end
end

puts "Hey, " + Person.get_name
puts "Hey, " + Person.persons_name  #=> raises "private method `persons_name' called for Person:Class (NoMethodError)"
```

Reference: [How to create a private class method?](https://stackoverflow.com/questions/4952980/how-to-create-a-private-class-method)