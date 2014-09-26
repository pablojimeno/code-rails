# Week 5

### Day 21: Rails & File management @ivanoats
- File uploading is a very common part of Rails apps. Let's learn the basics first, and take it "to the cloud! web scale!" We will be using the Carrierwave gem to facilitate this process.
- What is a multi-part form?
  - READ: http://guides.rubyonrails.org/form_helpers.html#uploading-files
  - http://stackoverflow.com/questions/4526273/what-does-enctype-multipart-form-data-mean
- Railscast: http://railscasts.com/episodes/253-carrierwave-file-uploads
- Railscast: http://railscasts.com/episodes/383-uploading-to-amazon-s3 (Sep 26, 2012)
- Reading: CarrierWave wiki: https://github.com/carrierwaveuploader/carrierwave/wiki/How-to:-Make-Carrierwave-work-on-Heroku
- BDD file upload…just files, and then with S3
  - RED
    - Just get the form spec  failing https://github.com/codefellows/portfolio/commit/505f8f97aff8a858e528db2ffae6dadb05860ce0
      - Error: Unable to find file field "Image"
    - Add in the file field: https://github.com/codefellows/portfolio/commit/d7ac07318d75e96f23aee5aea39e276607a161ec
      - Error: Expected to include "project_image.jpg" - The image is missing!
  - GREEN
    - visit https://github.com/carrierwaveuploader/carrierwave and read the README
    - Follow steps in the README
      - rails g uploader Image
        - check out the contents of the generated file at app/uploaders/image_uploader.rb
      - rails g migration add_image_to_projects image:string
        - check out the contents of the generate file at db/migrate/YYYYMMDDHHMMSS_add_image_to_projects.rb
      - mount the uploader in the app/models/project.rb
        - within the class definition:  `mount_uploader :image, ImageUploader`
      - permit the image parameter in your controller if you're using strong parameters
      - add in the image_tag to app/views/projects/show (and/or index)
        - `image_tag @project.image_url.to_s`
      -
  - REFACTOR
    - Well, too bad your Heroku dyno will not persist file uploads! All your images will eventually disappear! Bummer :-(
    - Now, refactor the uploads to upload to S3. Watch the second Railscast if you haven't already on Carrierwave Direct
      - README: https://github.com/dwilkie/carrierwave_direct
    - For bonus points look into direct and/or jQuery uploads.

### Day 22: Rails & Background Tasks @brookr
  - Intro: #linktoessay
  - Railscast: http://railscasts.com/episodes/366-sidekiq (Jul 18, 2012 )
  - BDD Background Jobs

### Day 23: Performance

### Day 24: Security


