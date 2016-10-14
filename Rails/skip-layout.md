```ruby
ReportsController < ApplicationController
  layout false # skip all action
  layout 'application', :except => :view # skip some action(s)
```

Reference: [Turn off layout for one of action](http://stackoverflow.com/questions/2062312/turn-off-layout-for-one-of-action)