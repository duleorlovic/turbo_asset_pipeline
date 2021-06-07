# Turbo rails asset pipeline

```
rails new turbo_asset_pipeline
cd turbo_asset_pipeline/
git add .
git commit -am'rails new turbo_asset_pipeline'

echo 'gem "turbo-rails"' >> Gemfile
bundle
rails turbo:install
git add .
git commit -m'rails turbo:install'

rails g scaffold room name
rails db:migrate
sed -i config/routes.rb -e "/^end$/i root to: 'rooms#index'"
git add .
git commit -am'rails g scaffold room name'

sed -i '2s/^/<%= turbo_frame_tag "room" do %>/' app/views/rooms/show.html.erb 
echo '<% end %>' >> app/views/rooms/show.html.erb 
echo '<br><input>' >> app/views/rooms/show.html.erb 
sed -i '2s/^/<%= turbo_frame_tag "room" do %>/' app/views/rooms/edit.html.erb 
sed -i '4s/^/<% end %>/' app/views/rooms/edit.html.erb 
git commit -am'Adding turbo_frame_tag'

rails turbo:install:asset_pipeline
sed -i '7s/^/\/\/  /' app/javascript/packs/application.js 
git commit -am'Using asset_pipeline'
```
