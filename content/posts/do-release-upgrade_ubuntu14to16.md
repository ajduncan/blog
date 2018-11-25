---
title: "do-release-upgrade from Ubuntu 14.04 to 16.04 (and then to 18.04)"
date: 2018-11-24T20:08:52-05:00
draft: false
tags: ["ubuntu", "hugo", "blog"]
categories: ["software"]
---

# do-release-upgrade

When I was automating the update for my personal site, I noticed the system it's running on was out of date.  I should be moving to a platform,
or creating one myself.  For now I'm using digital ocean or linode and have to maintain my own systems.  When I ssh'd in to look at using hugo,
I found it didn't exist for 14.04, and so I went ahead and performed a remote update.

# 14.04 to 16.04

Mainly, you need to make sure the recovery ssh port is open if anything goes wrong:

    $ sudo iptables -I INPUT -p tcp --dport 1022 -j ACCEPT

Running do-release-upgrade will let you know about this, so you can make sure you've added the above firewall rule.  The process was pain free
for me, and continues to (mostly) be this way across servers and on my workstation.  After a reboot, I went to see what version of hugo is in
the 16.04 repository:

    root@strategem:/home/andy# hugo version
    Hugo Static Site Generator v0.16-DEV BuildDate: 2016-02-06T12:14:17-05:00

# 16.04 to 18.04

The version of hugo that ships with Ubuntu 14.04 is way too old and will lack built in functions (like now) for templates that I'm using.  So, 
another do-release-upgrade later I'm running 18.04 in production and:

    root@strategem:/home/andy# hugo version
    Hugo Static Site Generator v0.40.1 linux/amd64 BuildDate: 2018-04-25T17:16:11Z

This version I'm happy with!
