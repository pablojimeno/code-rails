# Extra Credit: AWS S3 (Amazon Web Services: Simple Storage Service)

- Extra credit: Instead of trying to deal with image uploads for portfolio items right now, we'll deal with this later. For now, we can just upload an image to the web via the AWS management interface. This will help get us used to the Simple Storeage Service (S3)
    - Create a bucket and upload an image to s3 via the AWS management interface
      - Read: http://docs.aws.amazon.com/AmazonS3/latest/gsg/GetStartedWithS3.html
      - or Watch: http://aws.amazon.com/resources/webinars/?vid=hKK5UNrdEwE&p=PLhr1KZpdzukcbfIlFUyUUQaqI61WqWCiO&cue=play&t=Amazon%20S3%20-%20Creating%20a%20Bucket
    - Make sure your image is available on the public internet.
    - Add an "image_url" attribute to the project model via a migration.
    - Use this image_url to show the image in the show view, and in your index view if your design supports it.
