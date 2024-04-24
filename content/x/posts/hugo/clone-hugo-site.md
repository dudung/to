---
title: "Clone a Hugo site"
date: 2023-05-29T07:31:00+07:00
authors: ['Sparisoma Viridi']
tags: ['x', 'hugo', 'clone', 'submodules']
draft: false
math: false
url: "0003"
---
In order to clone a Hugo site stored in a GitHub repository, which has themes as submodules, it requires --recursve-submodules option, or it will generate only empty folders.


## clone
To clone https://github.com/dudung/x with its submodules

```shell
$ git clone --recurse-submodules https://github.com/dudung/x
Cloning into 'x'...
remote: Enumerating objects: 99, done.
remote: Counting objects: 100% (99/99), done.
remote: Compressing objects: 100% (54/54), done.
remote: Total 99 (delta 30), reused 66 (delta 15), pack-reused 0
Receiving objects: 100% (99/99), 19.46 KiB | 6.49 MiB/s, done.
Resolving deltas: 100% (30/30), done.
Submodule 'themes/hugo-coder' (https://github.com/luizdepra/hugo-coder.git) registered for path 'themes/hugo-coder'
Cloning into 'D:/x/themes/hugo-coder'...
remote: Enumerating objects: 3522, done.
remote: Counting objects: 100% (87/87), done.
remote: Compressing objects: 100% (46/46), done.
remote: Total 3522 (delta 35), reused 73 (delta 33), pack-reused 3435
Receiving objects: 100% (3522/3522), 3.11 MiB | 10.57 MiB/s, done.
Resolving deltas: 100% (1829/1829), done.
Submodule path 'themes/hugo-coder': checked out '1fb96cf9a920c46e01f3c0736cf01770c041617e'
```


## start hugo
```shell
PS D:\x> hugo server
Start building sites …
hugo v0.112.4-e285153d7f75d13bb062101c0a66b0138a90a71c+extended windows/amd64 BuildDate=2023-05-28T13:04:00Z VendorInfo=gohugoio

                   | EN
-------------------+-----
  Pages            | 28
  Paginator pages  |  0
  Non-page files   |  0
  Static files     |  6
  Processed images |  0
  Aliases          |  7
  Sitemaps         |  1
  Cleaned          |  0

Built in 902 ms
Watching for changes in D:\x\{archetypes,content,layouts,static,themes}
Watching for config changes in D:\x\hugo.toml
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/x/ (bind address 127.0.0.1)
Press Ctrl+C to stopc
```


## clone without submodules
If it is cloned without submodules

```shell
PS D:\> cd x
PS D:\x> hugo server
Start building sites …
hugo v0.112.4-e285153d7f75d13bb062101c0a66b0138a90a71c+extended windows/amd64 BuildDate=2023-05-28T13:04:00Z VendorInfo=gohugoio
WARN 2023/05/29 07:49:19 found no layout file for "html" for kind "page": You should create a template file which matches Hugo Layouts Lookup Rules for this combination.
WARN 2023/05/29 07:49:19 found no layout file for "html" for kind "term": You should create a template file which matches Hugo Layouts Lookup Rules for this combination.
WARN 2023/05/29 07:49:19 found no layout file for "html" for kind "taxonomy": You should create a template file which matches Hugo Layouts Lookup Rules for this combination.
WARN 2023/05/29 07:49:19 found no layout file for "html" for kind "page": You should create a template file which matches Hugo Layouts Lookup Rules for this combination.
WARN 2023/05/29 07:49:19 found no layout file for "html" for kind "home": You should create a template file which matches Hugo Layouts Lookup Rules for this combination.
WARN 2023/05/29 07:49:19 found no layout file for "html" for kind "term": You should create a template file which matches Hugo Layouts Lookup Rules for this combination.
WARN 2023/05/29 07:49:19 found no layout file for "html" for kind "term": You should create a template file which matches Hugo Layouts Lookup Rules for this combination.
WARN 2023/05/29 07:49:19 found no layout file for "html" for kind "term": You should create a template file which matches Hugo Layouts Lookup Rules for this combination.
WARN 2023/05/29 07:49:19 found no layout file for "html" for kind "taxonomy": You should create a template file which matches Hugo Layouts Lookup Rules for this combination.
WARN 2023/05/29 07:49:19 found no layout file for "html" for kind "section": You should create a template file which matches Hugo Layouts Lookup Rules for this combination.
WARN 2023/05/29 07:49:19 found no layout file for "html" for kind "page": You should create a template file which matches Hugo Layouts Lookup Rules for this combination.
WARN 2023/05/29 07:49:19 found no layout file for "html" for kind "section": You should create a template file which matches Hugo Layouts Lookup Rules for this combination.
WARN 2023/05/29 07:49:19 found no layout file for "html" for kind "taxonomy": You should create a template file which matches Hugo Layouts Lookup Rules for this combination.
WARN 2023/05/29 07:49:19 found no layout file for "html" for kind "taxonomy": You should create a template file which matches Hugo Layouts Lookup Rules for this combination.
WARN 2023/05/29 07:49:19 found no layout file for "html" for kind "term": You should create a template file which matches Hugo Layouts Lookup Rules for this combination.

                   | EN
-------------------+-----
  Pages            | 12
  Paginator pages  |  0
  Non-page files   |  0
  Static files     |  1
  Processed images |  0
  Aliases          |  0
  Sitemaps         |  1
  Cleaned          |  0

Built in 62 ms
Watching for changes in D:\x\{archetypes,content,layouts,static}
Watching for config changes in D:\x\hugo.toml
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/x/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```

that is producing several warnings. "Page not found" message will be displayed in a browser while trying to access the localhost address.


## refs
+ Mathias Bynens, "Answer to 'How do I "git clone" a repo, including its submodules?'", Stack Overflow, 14 Dec 2010, url https://stackoverflow.com/a/4438292/9475509 [20230529].
