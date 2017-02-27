```ruby
File.open("test.txt", "w+") do |f|
  a.each { |element| f.puts(element) }
end
```

Reference: [Add each array element to the lines of a file in ruby](http://stackoverflow.com/questions/18900474/add-each-array-element-to-the-lines-of-a-file-in-ruby)