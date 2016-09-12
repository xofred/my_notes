If you want to remove the header completely, you can create an `after_action` filter:
```ruby
class FilesController < ApplicationController
  after_action :allow_iframe, only: :embed

  def embed
  end

private

  def allow_iframe
    response.headers.except! 'X-Frame-Options'
  end
end
```
Or, of course, you can code the `after_action` to set the value to something different:
```ruby
class FacebookController < ApplicationController
  after_action :allow_facebook_iframe

private

  def allow_facebook_iframe
    response.headers['X-Frame-Options'] = 'ALLOW-FROM https://apps.facebook.com'
  end
end
```
Note that you need to clear your cache in certain browsers (Chrome for me) while debugging this.

Reference: [How to override X-Frame-Options for a controller or action in Rails 4](http://stackoverflow.com/questions/18445782/how-to-override-x-frame-options-for-a-controller-or-action-in-rails-4)