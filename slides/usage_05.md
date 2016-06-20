## JSON

`json` pluginを使用する

```ruby
require "roda"

class App < Roda
  plugin :json

  route do |r|
    r.root do
      [1, 2, 3]
    end

    r.is "foo" do
      {'a'=>'b'}
    end
  end
end

run App.freeze.app
```
