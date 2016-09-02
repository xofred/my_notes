Got a pet project called [AppTracker](https://itunesapptracker.herokuapp.com/apps) up and running recently. Here's a [fine instruction](https://devcenter.heroku.com/articles/getting-started-with-rails4), step by step. 

Gemfile
```ruby
ruby "2.3.1"
gem 'pg' # Sqlite won't work on heroku, need to change db to pg.
gem 'rails_12factor', group: :production # features such as static asset serving and logging on Heroku 
```

config/database.yml
```yml
# PostgreSQL. Versions 8.2 and up are supported.
#
# Install the pg driver:
#   gem install pg
# On OS X with Homebrew:
#   gem install pg -- --with-pg-config=/usr/local/bin/pg_config
# On OS X with MacPorts:
#   gem install pg -- --with-pg-config=/opt/local/lib/postgresql84/bin/pg_config
# On Windows:
#   gem install pg
#       Choose the win32 build.
#       Install PostgreSQL and put its /bin directory on your path.
#
# Configure Using Gemfile
# gem 'pg'
#
default: &default
  adapter: postgresql
  encoding: unicode
  # For details on connection pooling, see rails configuration guide
  # http://guides.rubyonrails.org/configuring.html#database-pooling
  pool: 5
```

And MOST IMPORTANTLY, don't forget to run this(love capistrono)
```shell
heroku run rake db:migrate
```

---

ps: some useful command of heroku CLI

List apps
```shell
heroku apps
```

Delete app
```shell
heroku apps:destroy --appname
```

Reference: [Getting Started with Rails 4.x on Heroku](https://devcenter.heroku.com/articles/getting-started-with-rails4)

Reference: [naaman/delete-heroku-apps.sh](https://gist.github.com/naaman/1384970#file-delete-heroku-apps-sh)