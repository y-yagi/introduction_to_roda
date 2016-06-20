## Reliability

* `Roda`アプリ自体を`freeze`する事が出来る
  * 内部ではRuby標準の`freeze`メソッドを使って各変数を`freeze`している
  * `frozen-string-literal`もバンバンも使ってる

```ruby
require "roda"

class App < Roda
  route do |r|
    r.root do
      r.redirect "/hello"
    end
  end
end

run App.freeze.app
```

