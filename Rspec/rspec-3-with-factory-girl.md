You just have to add the following in your spec_helper.rb file
```ruby
require 'factory_girl_rails'
```

The required addition should be made in spec/support/factory_girl.rb and it should look like this:
```ruby
# RSpec
# spec/support/factory_girl.rb
RSpec.configure do |config|
  config.include FactoryGirl::Syntax::Methods
end
```

Reference: 

[Having trouble with RSpec Testing “Uninitialized constant FactoryGirl (Name Error)”](http://stackoverflow.com/questions/22715519/having-trouble-with-rspec-testing-uninitialized-constant-factorygirl-name-erro)

[I can't seem to add “config.include FactoryGirl::Syntax::Methods” to my rspec config block in spec_helper.rb](http://stackoverflow.com/questions/25648456/i-cant-seem-to-add-config-include-factorygirlsyntaxmethods-to-my-rspec-co/25649064#25649064)