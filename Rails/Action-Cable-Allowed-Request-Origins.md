Action Cable will only accept requests from specific origins.

By default, only an origin matching the cable server itself will be permitted. Additional origins can be specified using strings or regular expressions, provided in an array.
```ruby
Rails.application.config.action_cable.allowed_request_origins = ['http://rubyonrails.com', /http:\/\/ruby.*/]
```
When running in the development environment, this defaults to "http://localhost:3000".

To disable protection and allow requests from any origin:
```ruby
Rails.application.config.action_cable.disable_request_forgery_protection = true
```
To disable automatic access for same-origin requests, and strictly allow only the configured origins:
```ruby
Rails.application.config.action_cable.allow_same_origin_as_host = false
```

Reference: 

- [Request origin not allowed: http://localhost:3001 when using Rails5 and ActionCable](http://stackoverflow.com/questions/35188892/request-origin-not-allowed-http-localhost3001-when-using-rails5-and-actionca)
- [Allowed Request Origins](https://github.com/rails/rails/tree/master/actioncable#allowed-request-origins)