## The Flash

The flash is used primarily for displaying status messages to users. It can be used to display confirmations, errors, and other information. The flash can be used to pass objects, too. For more info, read the API docs: http://api.rubyonrails.org/classes/ActionDispatch/Flash.html

Based on [this coderwall article](https://coderwall.com/p/jzofog), add this code to `app/helpers/application_helper.rb`

```ruby
module ApplicationHelper

# translate the rails flash levels to appropriate Zurb Foundation css classes    def flash_class(level)
    case level
      when :notice then "info"
      when :success then "success"
      when :error then "error"
      when :alert then "warning"
    end
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

You might need some other html/css around the `.alert-box` div to make it fit properly in your page layout. Feel free to experiment!
