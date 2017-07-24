You can use the Enumerable.all? method:
```ruby
%i( p1 p2 p3 ).all? { |key| params[key].present? }
```
Another alternative, if you need the values, it to fetch them and check the presence.
```ruby
params.values_at(*%i( p1 p2 p3 )).all?(&:present?)
```
or
```ruby
params.values_at(:p1, :p2, :p3).all?(&:present?)
```

Reference: [Check Presence of multiple params](https://stackoverflow.com/questions/34766494/check-presence-of-multiple-params)