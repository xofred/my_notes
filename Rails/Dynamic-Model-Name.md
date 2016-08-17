Use [constantize](http://api.rubyonrails.org/classes/ActiveSupport/Inflector.html#method-i-constantize):
```ruby
model_name = ['Show', 'Event'].sample # Model
record = model_name.find_by(id: 666) # Record
```

Reference: [How to call a Class method dynamically in ruby](http://stackoverflow.com/questions/9653031/how-to-call-a-class-method-dynamically-in-ruby)