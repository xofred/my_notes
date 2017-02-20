### config.web_console.whitelisted_ips

By default, only requests coming from IPv4 and IPv6 localhosts are allowed.

config.web_console.whitelisted_ips lets you control which IP's have access to the console.

You can whitelist single IP's or whole networks. Say you want to share your console with 192.168.0.100. You can do this:

```ruby
class Application < Rails::Application
  config.web_console.whitelisted_ips = '192.168.0.100'
end
```

If you want to whitelist the whole private network, you can do:

```ruby
Rails.application.configure do
  config.web_console.whitelisted_ips = '192.168.0.0/16'
end
```

Or

```ruby
config.web_console.whiny_requests = false
```

Reference: 

- [Web Console](https://github.com/rails/web-console#configweb_consolewhitelisted_ips)
- [Cannot Render Console From Some IP With Rails](https://solidfoundationwebdev.com/blog/posts/cannot-render-console-from-some-ip-with-rails)