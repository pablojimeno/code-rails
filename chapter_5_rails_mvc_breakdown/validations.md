
### About Rails Model Validations

A validation is a check that ensures that information is present, in a specifc format, or within a value range that is acceptable. If a model object does not pass validation, it is not saved to the database. For example, a blog article should always have a title, or a user account should always have an email address. If there are problems saving a record - that is, failures in validation - then the model's `.errors` array will have details on the validation failures.

#### Read up on validations

Read all of section 1 in [Active Record Validations in *Rails Guides*](http://guides.rubyonrails.org/active_record_validations.html).

Skim the other sections in that guide so you have an idea of what is available.

Of course, you can always reference the documentation for [the `validates` method in ActiveModel::Validations::ClassMethods](http://api.rubyonrails.org/classes/ActiveModel/Validations/ClassMethods.html#method-i-validates).

### Add validations to your model

Validate the technologies attribute won't be blank. See if you can write the validations on your own, and then check the **hints** below if you have trouble.

Add to your `project.rb` model file:

<pre style="color: #f7f7f7; font-size: 1.1em;">
  validates :technologies_used, presence: true
</pre>

Validates that the name attribute must be more than 4 characters long.

<pre style="color: #f7f7f7; font-size: 1.1em;">
    validates :name, length: { in: 4..255 }
</pre>
