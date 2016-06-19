## Sinatra

```ruby
require 'sinatra/base'

class App < Sinatra::Base
  get '/' do
    erb :index
  end

  get '/artist/:id' do
    @artist = Artist[params[:id]]
    check_access(@artist)
    erb :artist
  end

  post '/artist/:id' do
    @artist = Artist[params[:id]]
    check_access(@artist)
    @artist.update(params[:artist])
    redirect(request.path_info)
  end

  delete '/artist/:id' do
    @artist = Artist[params[:id]]
    check_access(@artist)
    @artist.destory
    redirect '/'
  end
end
```
[Roda: Routing Tree Web Toolkit - Why](http://roda.jeremyevans.net/why.html)から引用
