
### About Rails Model Validations
A validation is a check that ensures that information is present, in a specifc format, or within a value range that is acceptable. If a model object does not pass validation, it is not saved to the database. For example, a blog post should always have a title, or a user account should always have an email address. If there are problems saving a record - that is, failures in validation - then the model's .errors array will have details on the validation failures.

#### Read up on validations:
- Read all of section 1, and skim the other sections so you have an idea of what can be done: http://guides.rubyonrails.org/active_record_validations.html
- Additional reference: http://api.rubyonrails.org/classes/ActiveModel/Validations/ClassMethods.html#method-i-validates

### Add validations to your model
- Validate the technologies attribute won't be blank.
  - [COMPLETE] Add to your `project.rb` model file (highlight):

    <pre style="color: #f7f7f7">
      validates :technologies_used, presence: true
    </pre>

- Validate that the name attribute must be more than 4 characters long.
  - [COMPLETE]   Add to your project.rb model file (highlight):

        validates :name, length: { in: 4..255 }
