paste into a file like `config/locales/kaminari-zh-CN.yml`

```yml
zh-CN:
  views:
    pagination:
      first: "&laquo; 第一页"
      last: "最后一页 &raquo;"
      previous: "&lsaquo; 上一页"
      next: "下一页 &rsaquo;"
      truncate: "&hellip;"
  helpers:
    page_entries_info:
      one_page:
        display_entries:
          zero: "没有任何 %{entry_name}"
          one: "显示 <b>1</b> 个 %{entry_name}"
          other: "显示 <b>全部 %{count}</b> 个 %{entry_name}"
      more_pages:
        display_entries: "显示 <b>%{total}</b> 个 %{entry_name} 中的第 <b>%{first}&nbsp;-&nbsp;%{last}</b> 个"
```

in `config/application.rb`

```ruby
config.i18n.default_locale = :"zh-CN"
```

install theme `rails g kaminari:views semantic_ui`

if the pagination view looks funny, check the theme template just generated, make sure the locale file cover all the translations

```erb
<% if page.current? %>
  <a class="item active" href="<%= url %>" title="<%= t('views.pagination.page.current') %> <%= page %>">
    <%= page %>
  </a>
<% else %>
  <a class="item" href="<%= url %>" title="<%= t('views.pagination.page.goto') %> <%= page %>">
    <%= page %>
  </a>
<% end %>
```

add the missing translations

```yml
zh-CN:
  views:
    pagination:
      page:
        current: "当前"
        goto: "去"
```

set locale for certain controller( optional )

```ruby
before_action :set_locale
 
def set_locale
  I18n.locale = params[:locale] || I18n.default_locale
end
```

Reference: 

[Internationalization and Locales](https://github.com/amatsuda/kaminari/wiki/Internationalization-and-Locales)

[kaminari_themes/semantic_ui/app/views/kaminari/_page.html.erb](https://github.com/amatsuda/kaminari_themes/blob/master/semantic_ui/app/views/kaminari/_page.html.erb)

[Rails Internationalization (I18n) API](http://guides.rubyonrails.org/i18n.html#inflection-rules-for-other-locales)