---
title: "Lachesis"
date: 2018-11-23T22:24:52-05:00
tags: ["content management", "ubuntu", "github", "golang"]
categories: ["software"]
draft: false
authors: ["ajduncan"]
---

# Lachesis

In my last [post](./posts/hugo.html) I created a pull request to make sure a parameter was parsed properly in the gohugo-theme-ananke theme.  
Since it's been almost two weeks since I submitted the PR, I decided to fork the MIT licensed theme into my own and attempt to take responsibility
for maintaining and extending this theme.  So this is how Ananke was forked and became Lachesis.

## Summary

I forked an MIT licensed hugo theme and renamed it to [Lachesis](https://github.com/ajduncan/lachesis.git), set the master branch up to trigger an
automatic deployment on netlify.com to demonstrate the result of using the theme, and now use this theme for my personal blog.

## Forking

The process is fairly straight forward for an MIT licensed open source project, although the particular details are a bit unclear to me even after
a small bit of research on the appropriate spirit and letter of the law.  Basically, you want to give attribution and note the copyright of the
code and work done by the project's authors, typically by prepending a notice to the beginning of the LICENSE file in the repository.

Github allows you to fork an existing project to your own account, but I'm not planning on making subsequent pull requests to the original 
author's remote.  I still need to provide attribution of copyright per the MIT license, but I'm not clear on how to formally edit the LICENSE file
in some standard way.  

So I asked Google.  As such, two answers came up in various forms:

   1. [Stack Exchange #1](https://softwareengineering.stackexchange.com/questions/277688/if-i-fork-a-project-on-github-that-is-licensed-under-mit-how-to-i-handle-the-at) offers a straight forward answer.
   2. [Stack Exchange #2](https://opensource.stackexchange.com/questions/5484/how-to-use-mit-license-in-a-project)

I've decided to use both and make things as clear as I can.

## Netlify.com

[Netlify](https://www.netlify.com/) is a platform you can use to automatically build, deploy, serve and manage frontend sites and web apps.  The
original project used Netlify for the demo site.  When you give Netlify access to your repository, updates to the production branch trigger a 
deployment on their end, which will run a command and publish the results to a site, either a custom domain, custom subdomain off netlify.com, or a 
randomly generated subdomain.

## Github security

Github is kind enough to tell me some of the package.json dependencies node uses for front end asset
management has vulnerabilities, but that isn't a priority since we're using this locally to generate static content, right?  I'm glad they do this,
since there are so many people using npm, gems, composer, etc and so many dependencies that are vulnerable.  I'll have to come back later and 
resolve these issues by removing dependencies.

## Publishing

Now if I want to update the theme (and demo site), my workflow becomes:

    $ git checkout -b feature
    ... edit changes
    $ git commit -m "Adds the feature"
    $ git push
    $ git checkout master
    $ git merge feature
    $ git push

Once the master branch is updated, the demo site will get built.

