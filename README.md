# https://ajduncan.org/blog/ #

Here's my static content for publishing automatically to my own blog.

## Setup

Ensure [Hugo](https://gohugo.io/) or similar static site publishing tool is installed on the remote end,
make sure you've set a git hook on the master branch, e.g.:

    $ mkdir ~/github && cd ~/github
    $ git clone https://github.com/ajduncan/blog.git
    $ vim ~/github/blog/.git/post-receive

Add the logic to run hugo e.g.;

    ```#!/bin/bash
       
       hugo -s ~/github/blog/ -d ~/blog/public'''

    $ chmod +x ~/github/blog/.git/hooks/post-receive

Then create a cron job to periodically check e.g.

    $ crontab -e

0 2 * * * cd ~/github/blog && git pull > 2&1 &

## Adding Pages

Using hugo, the workflow is typically:

    $ cd /path/to/blog
    $ hugo new/posts/post.md

Then edit your

## Manual Publishing

...

## Viewing Drafts

...


