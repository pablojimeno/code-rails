# Week 5

## Day 21: Rails & File management @ivanoats

File uploading is a very common part of Rails apps. Let's learn the basics first, and take it "to the cloud! web scale!" We will be using the Carrierwave gem to facilitate this process.

What is a multi-part form?
- READ: [Rails Guides: Uploading Files](http://guides.rubyonrails.org/form_helpers.html#uploading-files)
- READ: [What Does Enctype Multipart Form Data Mean?](http://stackoverflow.com/questions/4526273/what-does-enctype-multipart-form-data-mean)
- Watch or Read: [RailsCast #253 *Carrier Wave File Uploads*](http://railscasts.com/episodes/253-carrierwave-file-uploads)
- Watch or Rad: [RailsCast #383 *Uploading to Amazon S3*](http://railscasts.com/episodes/383-uploading-to-amazon-s3) (Sep 26, 2012)
- Reference: [CarrierWave wiki](https://github.com/carrierwaveuploader/carrierwave/wiki/How-to:-Make-Carrierwave-work-on-Heroku)
- BDD file upload…just files, and then with S3

### RED

Just get the form spec failing: [codefellows/oortolio](https://github.com/codefellows/portfolio/commit/505f8f97aff8a858e528db2ffae6dadb05860ce0)

    Error: Unable to find file field Image

Add in the file field: [codefellows/portfolio](https://github.com/codefellows/portfolio/commit/d7ac07318d75e96f23aee5aea39e276607a161ec)

    Error: Expected to include "project_image.jpg" - The image is missing!

### GREEN

Read the README for [carrierwaveuploader/carrierwave](https://github.com/carrierwaveuploader/carrierwave)

Follow steps in the README and:

    $ rails g uploader Image

Check out the contents of the generated file at `app/uploaders/image_uploader.rb`

    $ rails g migration add_image_to_projects image:string

Check out the contents of the generated file at `db/migrate/YYYYMMDDHHMMSS_add_image_to_projects.rb`

#####Mount the uploader in the `app/models/project.rb`.
Within the class definition:
```ruby
mount_uploader :image, ImageUploader
```
Permit the image parameter in your controller if you're using strong parameters, add in the `image_tag` to `app/views/projects/show` (and/or `index`):
```ruby
image_tag @project.image_url.to_s
```

### REFACTOR

Well, too bad your Heroku dyno will not persist file uploads! All your images will eventually disappear! Bummer :-(

Now, refactor the uploads to upload to S3. Watch the second RailsCast if you haven't already on Carrierwave Direct

README: [dwilkie/carrier_wave](https://github.com/dwilkie/carrierwave_direct)

For bonus points look into direct and/or jQuery uploads.

## Day 22: Rails & Background Tasks @brookr
  - Intro: #linktoessay

  - Railscast: [RailsCast #366 *Sidekiq*](http://railscasts.com/episodes/366-sidekiq) (Jul 18, 2012 )

  - BDD Background Jobs

## Day 23: Performance

## Day 24: Security


