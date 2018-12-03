---
title: "Lakespace"
date: 2018-12-02T19:07:05-05:00
draft: false
tags: ["nodejs", "npm", "javascript", "lakesite", "business"]
categories: ["software", "open source"]
---

For a while I've had an itch to scratch with the original idea I had
for [linksync](https://github.com/ajduncan/linksync).  The premise is a standard format for opening tabs for a project, in either chrome or firefox, and launch your IDE and basically set up your workspace for each software project you're working on.  Enter [lakespace](https://lakesite.net/project/lakespace) - ([github](https://github.com/lakesite/lakespace)) which I plan to integrate into linksync.

I also moved linksync into
[Lakesite.Net](https://lakesite.net/project/linksyc) and subsequently
drafted out an entire idea that combines
[del.icio.us](https://del.icio.us) and
[pinboard.in](https://pinboard.in) with services like
[feedly.com](https://feedly.com/) so I can easily create window groups
and user profiles around groups of links, that are also archived and
available for search.  The specific idea was for numerous projects, I
like to keep specific tabs open for them.  I dislike having to re-open
windows and use [Tab Session Manager](https://addons.mozilla.org/en-US/firefox/addon/tab-session-manager/)
for Firefox and Chrome, along with Multi-Account containers.  So having
a simple command I can type to automatically launch a new browser window
(or windows) with the tabs open to the URLs I'd be working with and my
editor of choice open and pointing to the project directory.

## Usage ##

Lakespace is available on [npm](https://www.npmjs.com/) as a [package](https://www.npmjs.com/package/lakespace).  Installation and use is pretty straight forward;

    ```
    # npm install -g lakespace
    ```

Lakespace uses [toml](https://github.com/toml-lang/toml) - Tom's obvious markup language, for configuration.  Once you have lakespace installed, create a folder and create a lakespace.toml file:

    $ cd /path/to/project
    $ cat <<EOF >>lakespace.toml

```
[example_window_name]
browser = "firefox"
tabs = [
  "https://ajduncan.org/",
  "https://lakesite.net/",
  "http://www.duncaningram.com/"

]

[ide]
editor = "atom"
project_directory = "."
EOF
```

Then you can type:

    $ lakespace

Which will open a new firefox browser window with three tabs, and open the [atom editor](https://ide.atom.io/) for the current directory.
