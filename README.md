# render-async

Lets you render paths asynchronously in Rails with an AJAX call. You use it like this:

```ruby
# routes.rb:

get 'articles/counter' => 'articles#counter', :as => :articles_counter
```

```erb
# In a view template:

<%= render_async articles_counter_path %>
```

This will generate the following HTML:

```html
<div id="render_async_1a931cec881377296672"></div>

<script type="text/javascript">
(function($){
  divElement = $("#render_async_1a931cec881377296672");
  spinnerElement = $("#render_async_1a931cec881377296672 spinner");
  $.ajax({
      url: "/articles/counter",
    })
    .done(function(response, status) {
      divElement.html(response);
    })
    .fail(function(response, status) {
      divElement.html(response);
    })
    .always(function(response, status) {
      spinnerElement.hide();
    });
}(jQuery));
</script>
```

## Requirements

render-async depends on a footer-block in your application-wide template, like this:

```erb
# application.html.erb

<%= yield :render_async %>
```

And it also depends on you having included jQuery on the page.

## Installation

Add this line to your application's Gemfile:

    gem 'render_async'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install render_async

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
