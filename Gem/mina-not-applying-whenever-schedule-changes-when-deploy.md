```ruby
# config/deploy.rb
task deploy: :remote_environment  do
    # ...
    on :launch do
      invoke :cron_task
    end
  end
end

# it's important to add :remote_environment
# or error "bash: bundle: command not found" will occur when using `mina console`
task :cron_task => :remote_environment do
  rails_env = fetch(:rails_env)

  if rails_env != 'production'
    invoke :'whenever:update'
  end
end
```

Reference: 

[Whenever tasks use old release in readme example · Issue #304 · mina-deploy/mina](https://github.com/mina-deploy/mina/issues/304)

[Mina 1.0.2+ error "bash: bundle: command not found" when using `mina console` · Issue #476 · mina-deploy/mina](https://github.com/mina-deploy/mina/issues/476)