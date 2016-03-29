### update
```ruby
user.update_attribute(:name, "Rob")
```
This method will change the attribute in the model and pass it straight to the database, without running any validations.

Two gotchas:

- Any other changed attributes are also saved to the database.
- Validations are skipped so you could end up with invalid data.

Because of that last quirk it’s a good practice to use `update` instead even though you might only want to update one attribute.

### update_attributes
```ruby
user.update(name: "Rob")
```
This method used to be called `update_attributes` in Rails 3. It changes the attributes of the model, checks the validations, and updates the record in the database if it validates.

Note that just like `update_attribute` this method also saves other changed attributes to the database.

***

Reference: [http://www.davidverhasselt.com/set-attributes-in-activerecord/](Different Ways to Set Attributes in ActiveRecord (Rails 4))