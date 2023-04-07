# THINGS IN HERE

## GEMS

```
# gem 'paperclip', '~> 4.2.0'
# gem 'bootstrap-sass', '~> 3.2.0.2'

# Use Sass to process CSS
gem "sassc-rails"

# Use Active Storage variants [https://guides.rubyonrails.org/active_storage_overview.html#transforming-images]
gem "image_processing", "~> 1.2"
gem 'devise'
gem 'searchkick'
# gem "elasticsearch" 
gem "opensearch-ruby"
```
- no paperclip needed
- i didnt use bootstrap sass
- sass rails for .scss files
- image processing for storage
- devise set for turbo, rails 7
- from: https://dev.to/efocoder/how-to-use-devise-with-turbo-in-rails-7-9n9
- devise links

```
    <div class="collapse navbar-collapse" id="bs-example-navbar-collapse-1">
      <ul class="nav navbar-nav">
        <% if user_signed_in? %>
          <li><%= link_to "New Movie", new_movie_path, class: "active" %></li>
          <li><%= link_to "Account", edit_user_registration_path %></li>
        <% else %>
          <li><%= link_to "Sign Up", new_user_registration_path, class: "active" %></li>
          <li><%= link_to "Sign In", new_user_session_path, class: "active" %></li>
        <% end %>
      </ul>
      <%= form_tag search_movies_path, method: :get, class: "navbar-form navbar-right", role: "search" do %>
        <p>
          <%= text_field_tag :search, params[:search], class: "form-control" %>
          <%= submit_tag "Search", name: nil, class: "btn btn-default" %>
        </p>
      <% end %>
```

### searchkick/elasticsearch
- I didnt finish setting it up
- installing searchkick/elasticsearch: https://www.youtube.com/watch?v=jb4lrihz6_E
- had to add elastic search gem
- install elastic search in terminal: https://github.com/ankane/searchkick
- https://stackoverflow.com/questions/42526394/failed-to-open-tcp-connection-to-localhost9200-connection-refused-connect2
- https://stackoverflow.com/questions/17191539/how-to-stop-shut-down-an-elasticsearch-node
```
brew services start elasticsearch-full
brew services stop elasticsearch-full
```

### jquery raty rating
- added to the layouts/app

```
<script src="https://code.jquery.com/jquery-3.6.1.min.js" integrity="sha256-o88AwQnZB+VDvE9tvIXrMQaPlFFSUTR+nldQm1LuPXQ=" crossorigin="anonymous"></script>    
<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/raty/2.9.0/jquery.raty.js"></script>
```
- add the images for the stars to assets/images
- in the show page

```
<script>
    $('.star-rating').raty({
      path: '/assets/',
      readOnly: true,
      score: function() {
            return $(this).attr('data-score');
    }
  });
</script>
```

## MODELS
- devise user: has many movies and reviews
- movies: belongs to user
- attached an image, searchkick
- reviews: belong to user, movies

## OTHER
- he did his own styling
- search tag form

```
      <%= form_tag search_movies_path, method: :get, class: "navbar-form navbar-right", role: "search" do %>
        <p>
          <%= text_field_tag :search, params[:search], class: "form-control" %>
          <%= submit_tag "Search", name: nil, class: "btn btn-default" %>
        </p>
      <% end %>
```