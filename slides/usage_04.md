## Rendering

`render` pluginを使用する事でviewのrenderを行うことが出来る

```ruby
require "roda"

class App < Roda
  plugin :render

  route do |r|
    @var = '1'

    r.get "render" do
      # Renders the views/home.erb template, which will have access to
      # the instance variable @var, as well as local variable content.
      render("home", locals: { content: "hello, world"})
    end

    r.get "view" do
      @var2 = '1'

      # Renders the views/home.erb template, which will have access to the
      # instance variables @var and @var2, and takes the output of that and
      # renders it inside views/layout.erb (which should yield where the
      # content should be inserted).
      view("home")
    end
  end
end

run App.freeze.app
```

内部では[tilt: Generic interface to multiple Ruby template engines](https://github.com/rtomayko/tilt)が使われている
