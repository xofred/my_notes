### Name and Extension
```ruby
file = "/path/to/xyz.mp4"

comp = File.basename file        # => "xyz.mp4"
extn = File.extname  file        # => ".mp4"
name = File.basename file, extn  # => "xyz"
path = File.dirname  file        # => "/path/to"
```

### Delete
```ruby
File.delete(path_to_file) if File.exist?(path_to_file)
```

### Download
```ruby
require 'open-uri'
open('image.png', 'wb') do |file|
  file << open('http://example.com/image.png').read
end
```

Reference: [Get file name and extension in Ruby](http://stackoverflow.com/questions/20793180/get-file-name-and-extension-in-ruby)

Reference: [Rails how to delete a file without failing on error](http://stackoverflow.com/questions/12808988/rails-how-to-delete-a-file-without-failing-on-error)

Reference: [How can I download a file from a URL and save it in Rails?](http://stackoverflow.com/questions/2515931/how-can-i-download-a-file-from-a-url-and-save-it-in-rails)