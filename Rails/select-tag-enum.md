```erb
<%= select_tag :status, options_for_select(Lead.statuses.map {|k, v| [k.humanize.capitalize, v]}) %>
```

[Rails select_tag/dropdown with enums](http://stackoverflow.com/questions/37674187/rails-select-tag-dropdown-with-enums)