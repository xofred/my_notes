It's easy to "upload" a file programmatically, for test or fixture or seed or scripting purposes.

For instance, do this inside seed.rb to create a Restaurant instance with a CarrierWave logo field from an image you've got stored away in your own db/images directory:
```ruby
restaurant = Restaurant.create!(name: "McDonald's")
restaurant.logo = Rails.root.join("db/images/mcdonalds_logo.png").open
restaurant.save!
```

Reference: [How to: "Upload" from a local file](https://github.com/carrierwaveuploader/carrierwave/wiki/How-to:-%22Upload%22-from-a-local-file)