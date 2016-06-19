## 使い方

当然引数をとることも出来る

```ruby
...

# GET /post/2011/02/16/hello
r.get "post/:y/:m/:d/:slug" do |y, m, d, slug|
  "#{y}-#{m}-#{d} #{slug}" #=> "2011-02-16 hello"
end

# GET /username/foobar branch
r.on "username/:username", :method=>:get do |username|
  user = User.find_by_username(username)

  # GET /username/foobar/posts
  r.is "posts" do
    # You can access user here, because the blocks are closures.
    "Total Posts: #{user.posts.size}" #=> "Total Posts: 6"
  end

  # GET /username/foobar/following
  r.is "following" do
    user.following.size.to_s #=> "1301"
  end
end

# /search?q=barbaz
r.get "search" do
  "Searched for #{r['q']}" #=> "Searched for barbaz"
end

...
```
