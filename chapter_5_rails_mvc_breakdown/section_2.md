# Clean Up Test and Features Directory

Cleaning up the test/features directory. This list of post features, and the new ones we will be creating for portfolio items, is getting to be too long a list for me. Here's what I did to start organizing:

1. I used the bash `mkdir` command with the `-p` flag to create a directory a few levels deep from my current directory. I'm always in the app root directory.

        $ mkdir -p test/features/posts

2. I'm organizing all the post features into their own directory using the bash `mv` command and specifying a directory (ending in / ) as a destination:

        $ mv test/features/*post*.rb test/features/posts/

3. I'm going to call my portfolio items projects. Let's make a directory just for tests of the Project resource, like we did with posts (above):

        $ mkdir -p test/features/projects
