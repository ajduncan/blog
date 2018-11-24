---
title: "Hugo"
date: 2018-11-13T23:13:30-05:00
draft: false
tags: ["content management", "ubuntu", "github", "golang"]
categories: ["software"]
authors: ["ajduncan"]
---

# Managing content with Hugo

I've periodically kept and maintained a blog over the years.  I keep restarting whenever I enter a new life pattern.  Recently I came back to a 
static site generator, [Hugo](https://gohugo.io/), which is written in Go and has 30k+ stars on [Github](https://github.com/gohugoio/hugo/). 

## Summary

Hugo has excellent documentation on installation, getting started and usage. I'm surprised it doesn't have a section that covers installation on
Linux distributions.  I personally use Ubuntu and Debian on the desktop for development, along with OSX and Windows.  If you're familar with 
Markdown and can follow directions from the command line, Hugo makes a great choice for quickly building a site.

## Installation

Installation on Ubuntu was simple:

    # apt-get install hugo

Once installed, I checked the version:

    $ hugo version
    Hugo Static Site Generator v0.40.1 linux/amd64 BuildDate: 2018-04-25T17:16:11Z

The latest version as of 14 November 2018 on hugo's github is v0.51 and includes packages for DragonFlyBSD, FreeBSD, Linux, OSX, NetBSD, OpenBSD
and Windows.  This package is from April.  If this package is too old, you can install the .deb file from their 
[releases](https://github.com/gohugoio/hugo/releases) on github.

## Creating a site

Creating a new site, or folder to produce static content for publishing, is as easy as:

    $ mkdir sites
    $ cd sites
    $ hugo new site ajduncan

Make sure your working directory is the folder you just created, as subsequent commands assume this step:

    $ cd ajduncan

The documentation points out you should install a theme, using git, by adding a submodule and editing your site config file as such:

    $ git init
    $ git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke
    $ echo 'theme = "ananke"' >> config.toml

## Creating content

Once you have a site and theme defined you create new content as such:

    $ hugo new posts/hugo.md

Which adds a folder, posts, under the existing content folder and creates a hugo.md file.

## Previewing content

You can easily view the content prior to publishing by executing the following command:

    $ hugo server -D

Then you can go to http://localhost:1313/ to view your site.

## Markdown

Hugo uses markdown to generate static content, which makes it easy to add, update and delete content or migrate to another platform.

## Configuration

While configuring Hugo using the config.toml file, specifically for the theme they introduce in the documentation (ananke), I found that
line 12 of themes/ananke/layouts/partials/site-header.html should instead have:

   {{ with .Params "description" }}

Instead of:

   {{ with .Params.description }}

Which allows me to set a description under the params section of the config.toml file.  I've submitted a pull [request](https://github.com/budparr/gohugo-theme-ananke/pull/141), but someone else
has also done this.  It's likely I've missed something, but if we're both making the same mistake either the documentation should be updated
or the issue should be fixed.

## Publishing

Once you've updated your post metadata, set draft: false, and run hugo, it will publish the html and assets under a folder called public.
When I was finished, I entered a command similar to:

    $ cd public
    $ scp -r * site-name:/path/to/your/blog/

Which copies everything over, assuming you're using ssh keys and have setup site-name in your ssh config file.


