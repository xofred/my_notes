**Post-install message from capistrano:**

Capistrano 3.1 has some breaking changes. Please check the [CHANGELOG](http://goo.gl/SxB0lr)

If you're upgrading Capistrano from 2.x, we recommend to read the [upgrade guide](http://goo.gl/4536kB)

The `deploy:restart` hook for passenger applications is now in a separate gem called capistrano-passenger.  Just add it to your Gemfile and require it in your Capfile.

**Post-install message from capistrano-passenger:**

==== Release notes for capistrano-passenger ====

passenger once had only one way to restart: `touch tmp/restart.txt`
Beginning with passenger v4.0.33, a new way was introduced: `passenger-config restart-app`

The new way to restart is not so practical for everyone, since it may require your deployment user to have sudo access.
While we eagerly await the release of passenger v5.0.10, which will make the new method possible without sudo access,
we recognize that not everyone is ready for this change yet.

capistrano-passenger gives you the flexibility to choose your restart approach, or to rely on reasonable defaults.

If you want to restart using `touch tmp/restart.txt`, add this to your config/deploy.rb:

    set :passenger_restart_with_touch, true

If you want to restart using `passenger-config restart-app`, add this to your config/deploy.rb:

    set :passenger_restart_with_touch, false # Note that `nil` is NOT the same as `false` here

If you don't set `:passenger_restart_with_touch`, capistrano-passenger will check what version of passenger you are running
and use `passenger-config restart-app` if it is available in that version.

If you are running passenger in standalone mode, it is possible for you to put passenger in your
Gemfile and rely on capistrano-bundler to install it with the rest of your bundle.
If you are installing passenger during your deployment AND you want to restart using `passenger-config restart-app`,
you need to set `:passenger_in_gemfile` to `true` in your `config/deploy.rb`.
================================================

### deploying multiple applications to the same server

```ruby
# config/deploy.rb or config/deploy/<stage_name>.rb
#set :deploy_to, '/var/www/my_app_name'
set :deploy_to, '/var/www/my_app2_name' # choose a different :deploy_to path.
```

### sensitive config files or things should be persist

```ruby
set :linked_files, %w{config/database.yml config/settings/alipay.yml config/upyun.yml config/umeng_message.yml
                      config/danche.yml config/yongle.yml config/viagogo.yml config/mlb_translate.yml
                      config/certs/rsa_private_key.pem config/certs/app_private_key.pem config/certs/alipay_public_key.pem}

set :linked_dirs, %w{tmp/pids tmp/cache tmp/sockets}
```

New in Capistrano 3.5: for a variable that holds an Array, easily add values to it using append. This comes in especially handy for `:linked_dirs` and `:linked_files` (see Variables reference below).
```ruby
append :linked_dirs, ".bundle", "tmp"
```

[More Configuration Variables](http://capistranorb.com/documentation/getting-started/configuration/)

[Before Deploy](http://capistranorb.com/documentation/getting-started/preparing-your-application/)

Reference: [Capistrano Offical Site](http://capistranorb.com)

