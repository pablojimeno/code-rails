# Extra Credit: AWS S3 (Amazon Web Services: Simple Storage Service)

Instead of trying to deal add an image upload feature for portfolio items right now, we'll deal with it later.

For now, we can just upload an image to the web via the AWS management interface. We'll get used to the Simple Storeage Service (S3).

## First, create a bucket and upload an image

Use the AWS Mgmt. Console to upload an image via the S3 interface

**Read:** [Get Started with S3](http://docs.aws.amazon.com/AmazonS3/latest/gsg/GetStartedWithS3.html)

**or Watch:** [Amazon S3 - Creating a Bucket](
http://aws.amazon.com/resources/webinars/?vid=hKK5UNrdEwE&p=PLhr1KZpdzukcbfIlFUyUUQaqI61WqWCiO&cue=play&t=Amazon%20S3%20-%20Creating%20a%20Bucket)

## Now make use of your bucket
- Make sure your image is available on the public internet.
- Add an `image_url` attribute to the project model via a migration.
- Use this `image_url` to display the image in the show view (and your index view if your design supports it).
