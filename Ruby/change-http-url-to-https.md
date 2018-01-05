```ruby
  def find_avatar(user)
    avatar = user.avatar
    return default_avatar if avatar.blank?

    begin
      uri = URI avatar
      case uri.scheme
      when 'http'
        uri.scheme = 'https'
        uri.to_s
      when 'https'
        uri.to_s
      else
        default_avatar
      end
    rescue
      return default_avatar
    end
  end

  private
  def default_avatar
    ActionController::Base.helpers.asset_path("default_avatar.png")
  end
```

Reference: [Easily change parts of a URI](https://coderwall.com/p/f8pjda/easily-change-parts-of-a-uri)