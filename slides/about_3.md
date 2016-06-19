## Roda

```ruby
require 'roda'

class App < Roda
  plugin :render
  plugin :all_verbs

  route do |r|
    r.root do
      view :index
    end

    r.is 'artist/:id' do |artist_id|
      @artist = Artist[artist_id]
      check_access(@artist)

      r.get do
        view :artist
      end

      r.post do
        @artist.update(r['artist'])
        r.redirect
      end

      r.delete do
        @artist.destroy
        r.redirect '/'
      end
    end
  end
end
```
