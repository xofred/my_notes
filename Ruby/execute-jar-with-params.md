```ruby
IO.popen(["java", "-jar", "#{Rails.root}/lib/tuniu_sign.jar", TuniuSetting["apiKey"], "message"]).read
# => "p0jRuOdJEsJ/ohLBu1lbPKJzBqU9f4uFmB4ZEghVDrfKsB5++6cACW8oOJTqtJERsC3Ng2gNHCJdUwD1hWJaxQ==\n"
```

Reference: 

[Ruby on Rails: Executing JAR](http://stackoverflow.com/questions/14484033/ruby-on-rails-executing-jar)

[Class: IO (Ruby 2.3.2)](http://ruby-doc.org/core-2.3.2/IO.html#method-c-popen)