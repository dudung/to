---
title: "Setup a Hugo site (again)"
date: 2023-05-27T18:30:00+07:00
authors: ['Sparisoma Viridi']
tags: ['x', 'hugo', 'go']
draft: false
math: false
url: "0000"
---
Several steps are required to set up a Hugo site in Windows. In general the steps includes download and install Hugo, create and clone repository in GitHub, make a new site with Hugo, add theme, tune configuration, post article, and push changes to GitHub.


## download
Latest version is [v0.112.3](https://github.com/gohugoio/hugo/releases/tag/v0.112.3) which is released three days ago by [bep](https://github.com/bep). The filename `hugo_extended_0.112.3_windows-amd64.zip` has size about 18.6 MB.


## install
+ Extract the zip file ang put `hugo.exe`, `LICENSE`, `README.md` files to `C:\Hugo\bin`.
+ Add `C:\Hugo\bin` to Path of your user veriables by editing system environmental variables.
+ Test it
  ```shell
  L:\home>hugo version
  hugo v0.112.3-ba6f74e40420d76f15fc8c2358be90f7aca98e0e+extended windows/amd64 BuildDate=2023-05-24T14:42:50Z VendorInfo=gohugoio
  ```

## repository
+ Create a GitHub repository, which is https://github.com/dudung/x in this case.
+ Clone it.
  ```shell
  $ git clone https://github.com/dudung/x
  Cloning into 'x'...
  remote: Enumerating objects: 10, done.
  remote: Counting objects: 100% (10/10), done.
  remote: Compressing objects: 100% (8/8), done.
  remote: Total 10 (delta 1), reused 0 (delta 0), pack-reused 0
  Receiving objects: 100% (10/10), done.
  Resolving deltas: 100% (1/1), done.
  ```

## create site
Here site and folder name is `x`.
  ```
  L:\home>hugo new site x --force
  Congratulations! Your new Hugo site is created in L:\home\x.

  Just a few more steps and you're ready to go:

  1. Download a theme into the same-named folder.
     Choose a theme from https://themes.gohugo.io/ or
     create your own with the "hugo new theme <THEMENAME>" command.
  2. Perhaps you want to add some content. You can add single files
     with "hugo new <SECTIONNAME>\<FILENAME>.<FORMAT>".
  3. Start the built-in live server via "hugo server".

  Visit https://gohugo.io/ for quickstart guide and full documentation.
  ```

## add theme
Hugo-Coder theme is used here.
```
$ git submodule add https://github.com/luizdepra/hugo-coder.git themes/hugo-coder
Cloning into 'L:/home/x/themes/hugo-coder'...
remote: Enumerating objects: 3522, done.
remote: Counting objects: 100% (87/87), done.
remote: Compressing objects: 100% (46/46), done.
remote: Total 3522 (delta 35), reused 74 (delta 33), pack-reused 3435
Receiving objects: 100% (3522/3522), 3.10 MiB | 501.00 KiB/s, done.
Resolving deltas: 100% (1828/1828), done.
warning: LF will be replaced by CRLF in .gitmodules.
The file will have its original line endings in your working directory
```


## tune configuration
+ Modify cofiguration file, where Hugo version 0.95.0 uses `config.toml`, while version 0.112.3 uses `hugo.toml`.

```toml
baseURL = 'https://dudung.github.io/x'
languageCode = 'en-us'
title = 'x'
theme = 'hugo-coder'
```


### add files
`content/about.md`.
```md
# about
It is me, @6unpnp.
```

`static/img/avatar.svg` &rightarrow; [avatar.svg](https://github.com/dudung/x/blob/main/static/img/avatar.svg)


## modify files
Modify `layouts/partials/footer.html` from
```
{{ i18n "powered_by" }}
<a href="https://gohugo.io/">Hugo</a> &
<a href="https://github.com/luizdepra/hugo-coder/">Coder</a>.
```
to
```
{{ i18n "powered_by" }}
<a href="https://gohugo.io/">Hugo</a> &
<a href="https://github.com/luizdepra/hugo-coder/">Coder</a> &
<a href="https://iconscout.com/contributors/dmitriy-bondarchuk">IconScout</a>.
```
where the result is foother in this page.


## start hugo
```
L:\home\x>hugo server
Start building sites …
hugo v0.112.3-ba6f74e40420d76f15fc8c2358be90f7aca98e0e+extended windows/amd64 BuildDate=2023-05-24T14:42:50Z VendorInfo=gohugoio

                   | EN
-------------------+-----
  Pages            | 12
  Paginator pages  |  0
  Non-page files   |  0
  Static files     |  6
  Processed images |  0
  Aliases          |  0
  Sitemaps         |  1
  Cleaned          |  0

Built in 712 ms
Watching for changes in L:\home\x\{archetypes,assets,content,data,layouts,static,themes}
Watching for config changes in L:\home\x\hugo.toml
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/x/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```


## refs
+ Sarah Lean, "How to install Hugo on Windows 10", Techielass, 1 Jul 2021, url https://www.techielass.com/how-to-install-hugo-on-windows-10/ [20230527].
+ Shay Lynn Khan, "Getting Started With Hugo: How to Create a Simple Website", MakeUseOf, 24 May 2022, url https://www.makeuseof.com/hugo-start-create-simple-website/ [20230527].
+ Hugo Authors, "hugo new site", Hugo, 24 May 2023, url https://gohugo.io/commands/hugo_new_site/ [20230527].
+ Seann Hicks, "Hugo Themes", Tangent Technologies, 8 Jun 2020, url https://tangenttechnologies.ca/blog/hugo-themes/ [20230527].
