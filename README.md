Create a new image
Creating a brand new image and getting it pushed to the gcr.io/resson-1208 registry is extremely easy.

Create a new folder and a new Dockerfile



Optional (but recommended): Create a TAG file that indicates the tag you want this to push as. By default, this will be latest

Optional (not recommended): If you want your image to be named something other than the directory in which it resides, you can create an IMAGE file with the content of the image name (See google-sql-cloud as an example)

Add entries for the file in .circleci/config.yml

Under jobs:

jobs:
    ... <more jobs> ...
  publish_newimage:
    <<: *publish_image
    environment:
    - PLATFORM: ramas-newimage
    ... <more jobs> ...
Under workflows:

workflows:
  version: 2
  build:
    jobs:
        ... <more jobs> ...
      - publish_newimage:  *workflow_filters
        ... <more jobs> ...
Create a pull request and assign to Adam or Tim

Once accepted into the master branch, your image will be built in Circle CI and available as gcr.io/resson-1208/<image_name>:<tag>. See Image Naming to learn more about how your image will be named
