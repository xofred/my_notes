If you are creating a new application, you can use -O to skip ActiveRecord:

`rails new my_app -O`

For existing applications:

1. Remove database adapter gems from your Gemfile (mysql2, sqlite3, etc.)

2. Change your config/application.rb

Remove require 'rails/all line and require frameworks you want to use, for example:
```ruby
require "action_controller/railtie"
require "action_mailer/railtie"
require "sprockets/railtie"
require "rails/test_unit/railtie"
```

3. Delete your config/database.yml file, db/schema.rb and migrations (if any)

4. Delete migration check in test/test_helper.rb

5. Delete any ActiveRecord configuration from your config/environments files (this is what is causing your error)

This is all you need to do for an empty Rails app. If you run into problems caused by your existing code, stack trace should give you sufficient information on what you need to change. You might for example have some ActiveRecord configuration in your initializers.