### ApplicationRecord

Say I want to add some extra functionality to Active Record. This is what I would do in Rails 4.2.
```ruby
module MyAwesomeFeature
  def do_something_great
    puts "Doing something complex stuff!!"
  end
end
```
ActiveRecord::Base.include(MyAwesomeFeature)
But now, ActiveRecord::Base forever includes MyAwesomeFeature and any class inheriting from it also includes MyAwesomeFeature even if they don’t want it.

This is especially true if you are using plugins and engines where monkey patching to ActiveRecord::Base can leak into engine or plugin code.

But with ApplicationRecord, they will be localized to only those models which are inheriting from ApplicationRecord, effectively only to your application.
```ruby
class ApplicationRecord < ActiveRecord::Base
  include MyAwesomeFeature

  self.abstract_class = true
end
```

---

### case_sensitive option in validation

Alright it's not new in Rails 5, but it's new to me. So, let me take some notes.

#### confirmation

There is also a :case_sensitive option that you can use to define whether the confirmation constraint will be case sensitive or not. This option defaults to true.
```ruby
class Person < ApplicationRecord
  validates :email, confirmation: { case_sensitive: false }
end
```
The default error message for this helper is "doesn't match confirmation".

#### uniqueness

There is also a :case_sensitive option that you can use to define whether the uniqueness constraint will be case sensitive or not. This option defaults to true.
```ruby
class Person < ApplicationRecord
  validates :name, uniqueness: { case_sensitive: false }
end
```

---

### Reference

- [ApplicationRecord in Rails 5](http://blog.bigbinary.com/2015/12/28/application-record-in-rails-5.html)
- [Active Record Validations — Ruby on Rails Guides](http://guides.rubyonrails.org/active_record_validations.html)
