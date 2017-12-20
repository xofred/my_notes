image locate at `assets/images/activity/wheel`

In html:
```erb
<%= image_tag "activity/wheel/1.png", id: "diy1-img", style: "display:none;" %>
```

In js:
```erb
$("#tab2 img").attr("src", "<%= asset_path 'activity/wheel/NG_07.png' %>");
```

Reference: [The Asset Pipeline — Ruby on Rails Guides](http://guides.rubyonrails.org/asset_pipeline.html)