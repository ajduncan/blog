# https://ajduncan.org/blog/ #

Here's my static content for publishing automatically to my own blog.

## Setup

Ensure [Hugo](https://gohugo.io/) or similar static site publishing tool is installed on the remote end,
make sure you've set a git hook on the master branch, e.g.:

    $ mkdir ~/github && cd ~/github
    $ git clone https://github.com/ajduncan/blog.git
    $ git submodule update --init
    $ vim ~/github/blog/.git/post-merge

Add the logic to run hugo e.g.;

    ```#!/bin/bash
 
       cd /home/andy/github/blog && git submodule update --recursive
       /usr/bin/hugo -s /home/andy/github/blog/ -d /var/www/vhosts/ajduncan.org/www/blog/
     '''

    $ chmod +x ~/github/blog/.git/hooks/post-merge

Then create a cron job to periodically check e.g.

    $ crontab -e

* * * * * cd ~/github/blog && git pull > /dev/null 2>&1

Which will issue git pull every minute, and run post-merge if there are any commits.

## Adding Pages

Using hugo, the workflow is typically:

    $ cd /path/to/blog
    $ hugo new/posts/post.md

Then edit your

## Manual Publishing

...

## Viewing Drafts

...


