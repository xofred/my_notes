```ruby
# resets the user password and save the record, true if valid passwords are given, otherwise false
User.find(1).reset_password('password123', 'password123')
```

Reference: [Module: Devise::Models::Recoverable](http://www.rubydoc.info/github/plataformatec/devise/master/Devise/Models/Recoverable)