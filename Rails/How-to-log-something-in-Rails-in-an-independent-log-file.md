```ruby
class User < ActiveRecord::Base
  def my_logger
    @@my_logger ||= Logger.new("#{Rails.root}/log/my.log")
  end

  def before_save
    my_logger.info("Creating user with name #{self.name}")
  end
end
```

Reference: [How to log something in Rails in an independent log file?](http://stackoverflow.com/questions/337739/how-to-log-something-in-rails-in-an-independent-log-file)