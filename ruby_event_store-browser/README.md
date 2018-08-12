# RubyEventStore::Browser
This is the Sinatra version of the browser.

## Usage
You need to require `ruby_event_store/browser/app`.

There is a helper method to configure options `event_store_locator`, `host` and `path`.

```ruby
require 'ruby_event_store/browser/app'

event_store = RubyEventStore::Client.new(
  repository: RubyEventStore::InMemoryRepository.new
)

run RubyEventStore::Browser::App.for(
  event_store_locator: -> { event_store },
  host: 'http://localhost:2300'
)
```

Specify `path` option if you are not mounting the browser at the root.

```ruby
# e.g. mounting the Rack app in Hanami
mount RubyEventStore::Browser::App.for(
  event_store_locator: -> { event_store },
  host: 'http://localhost:2300',
  path: '/res'
), at: '/res'
```

## Installation
Add this line to your application's Gemfile:

```ruby
gem 'ruby_event_store-browser'
```

And then execute:
```bash
$ bundle
```

Or install it yourself as:
```bash
$ gem install ruby_event_store-browser
```

## Contributing
Contribution directions go here.

## License
The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).