```ruby
# app/models/product.rb
class Product
  include Taggable

  ...
end

# app/models/concerns/taggable.rb
# notice that the file name has to match the module name 
# (applying Rails conventions for autoloading)
module Taggable
  extend ActiveSupport::Concern

  included do
    has_many :taggings, as: :taggable
    has_many :tags, through: :taggings

    class_attribute :tag_limit
  end

  def tags_string
    tags.map(&:name).join(', ')
  end

  def tags_string=(tag_string)
    tag_names = tag_string.to_s.split(', ')

    tag_names.each do |tag_name|
      tags.build(name: tag_name)
    end
  end

  # methods defined here are going to extend the class, not the instance of it
  module ClassMethods

    def tag_limit(value)
      self.tag_limit_value = value
    end

  end

end
```

Reference: [How to use concerns in Rails 4](http://stackoverflow.com/questions/14541823/how-to-use-concerns-in-rails-4)