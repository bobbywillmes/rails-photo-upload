# Photo Upload with Rails & Active Storage

1. Initialize a new Rails project
2. Scaffold the project to create models, views & controllers
  - run command: `rails g scaffold movies title:string description:text year:integer rating:string`
3. Initialize active storage in Rails
  - run command: `rails active_storage:install`
  - then run: `rails db:migrate`
  - This migration creates three new tables: active_storage_blobs, active_storage_attachments & active_storage_variant_records
4. Update model
  - `has_one_attached :image`
5. Update controller parameters
  - add `:image` to .permit()
      - params.require(:movie).permit(:title, :description, :year, :rating, `:image`)
6. Update views
  - _form.html.erb
```
     <div class="field">
        <%= form.label :image %>
        <%= form.file_field :image %>
      </div>
```
  - show.html.erb
```
      <% if @movie.image.attached? %>
        <%= image_tag @movie.image, style: 'max-width: 500px; max-height: 500px; display: block' %>
      <% end %>
```