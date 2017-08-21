```ruby
class AddUniqueIndexToReleases < ActiveRecord::Migration
  def change
    add_index :releases, [:country, :medium], unique: true
  end
end
```

Reference: [Rails: validate uniqueness of two columns (together)](https://stackoverflow.com/questions/34424154/rails-validate-uniqueness-of-two-columns-together)