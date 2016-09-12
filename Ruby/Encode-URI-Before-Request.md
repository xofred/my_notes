```ruby
require 'uri'

url = URI.parse('http://192.168.178.23/emoncms/input/post.json')
url.query = URI::encode_www_form(
  {
    'json' => '{power:200}',
    'apikey' => '671b341330a7b1a4c20bf8ae7dd1faf1',
    'time' => 12345677890
  }
)

url.to_s # => "http://192.168.178.23/emoncms/input/post.json?json=%7Bpower%3A200%7D&apikey=671b341330a7b1a4c20bf8ae7dd1faf1&time=12345677890"
```

Reference: [How to post a URL containting curly braces and colons](http://stackoverflow.com/questions/24920692/how-to-post-a-url-containting-curly-braces-and-colons/24922684#24922684)