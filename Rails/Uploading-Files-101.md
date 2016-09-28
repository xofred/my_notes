
### Uploading Files
A common task is uploading some sort of file, whether it's a picture of a person or a CSV file containing data to process. The most important thing to remember with file uploads is that the rendered form's encoding **MUST** be set to `"multipart/form-data"`. If you use form_for, this is done automatically. If you use form_tag, you must set it yourself, as per the following example.

The following two forms both upload a file.

```erb
<%= form_tag({action: :upload}, multipart: true) do %>
  <%= file_field_tag 'picture' %>
<% end %>
 
<%= form_for @person do |f| %>
  <%= f.file_field :picture %>
<% end %>
```

Rails provides the usual pair of helpers: the barebones file_field_tag and the model oriented file_field. The only difference with other helpers is that you cannot set a default value for file inputs as this would have no meaning. As you would expect in the first case the uploaded file is in params[:picture] and in the second case in params[:person][:picture].

Reference: [Form Helpers — Ruby on Rails Guides](http://guides.rubyonrails.org/form_helpers.html#uploading-files)