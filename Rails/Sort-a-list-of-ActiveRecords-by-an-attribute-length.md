Let's say we have a model called `Hint`, and it has a attribute called `sentence`.

We want `Hint` sorted by `sentence`'s length.

Here's how we do it:

```ruby
hints = hints.sort { |x,y| x.sentence.length <=> y.sentence.length }
```

Reference: [How can I sort a list of ActiveRecords by an attribute length?](http://stackoverflow.com/questions/14185823/how-can-i-sort-a-list-of-activerecords-by-an-attribute-length)