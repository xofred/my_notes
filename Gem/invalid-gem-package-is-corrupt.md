When I ran `gem install nokogiri -v '1.6.7.2'`
```
ERROR:  Error installing nokogiri:
	invalid gem: package is corrupt, exception while verifying: undefined method `size' for nil:NilClass (NoMethodError) in /Users/MD212/.rvm/gems/ruby-2.3.0/cache/nokogiri-1.6.7.2.gem
```
So I deleted the gem `rm /Users/MD212/.rvm/gems/ruby-2.3.0/cache/nokogiri-1.6.7.2.gem`

And try again...`gem install nokogiri -v '1.6.7.2'`
```
Fetching: nokogiri-1.6.7.2.gem (100%)
Building native extensions.  This could take a while...
Successfully installed nokogiri-1.6.7.2
1 gem installed
```
Problem solved!