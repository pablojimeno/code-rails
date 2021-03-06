## FAILURE

#### Why is the test **failing**?

There is no *notice* that a project was successfully created. We need to add more code to do that. In Rails, this *notice* feature is implemented in **the [Flash Hash](http://api.rubyonrails.org/classes/ActionDispatch/Flash/FlashHash.html)**.

#### The Flash

The `flash` is used primarily for displaying status messages to users. It can be used to display *confirmations*, *errors*, *alerts*, and even customized information. The `flash` can be used to pass objects, too.

For more info, read [the Rails API docs about the Flash Object hash](http://api.rubyonrails.org/classes/ActionDispatch/Flash.html).

To get that to display correctly with your front-end framework, we'll need to translate that flash `:key` into a css class. If you are using Bootstrap, check out [this coderwall article](https://coderwall.com/p/jzofog). For Zurb Foundation, add something like the following code to `app/helpers/application_helper.rb`:

```ruby
module ApplicationHelper
  # translate Rails flash levels to appropriate Zurb Foundation css classes    
  def flash_class(level)
    level == :notice ? "info" : level.to_s
  end
end
```

Find a good place in your layout (`application.html.erb`), and put in:

```html
<% flash.each do |key, value| %>
  <div class="alert-box round <%= flash_class(key) %>">
    <%= value %>
  </div>
<% end %>
```

You might need some other HTML and CSS around the `div.alert-box` to make it fit properly in your page layout. Feel free to experiment!
