Timobox - timo docker box
=========================

## What is it

It's code to deploy timorest into aws beanstalk as a docker container.

It uses make script for simplicity.

    $ make

## requirements

    $ apt-get install -y zip git make

## Configuration

### Build time

None, for now

### beanstalk environment

TIMO_APPLICATION_DATA
:   application data to be downloaded from s3
