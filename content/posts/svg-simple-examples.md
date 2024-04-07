+++
title = 'svg simple examples'
date = 2024-04-08T03:27:00+07:00
draft = false
math = true
tags = ['svg', 'html', 'css', 'js']
url = '0004'
authors = ['viridi']
+++
Short intro to SVG and some simple examples <!--more-->


## intro
SVG, that stands for scalable vector graphis, is a web friendly vector-based file format used to render two-dimensional images on the internet, and it is written in pure XML [^chris_2022], which makes it can be created or edited using any text and code editor. Other than to code SVG, there is also a lot of drawing applications available that can be used to open and edit SVG files [^fisher_2022]. There are some reasons to use SVG, where one of them is SEO (search engine optimization) friendly that allowing keywords, descriptions, and links addition directly to the markup [^davey_2023]. Infinity scalability, small file size, editability, and accessiblity are advantages of SVG files, while complexity and browser support are the disadvantages [^edwards_2023].


## minimal lines
Let us make a SVG file with minimal content as displayed below

{{< div>}}
<svg height="100" width="100" style="background: #f8f8f8;">
  <circle r="45" cx="50" cy="50" fill="red" />
</svg>
{{< /div >}}

with

```svg
<svg height="100" width="100" style="background: #f8f8f8;">
  <circle r="45" cx="50" cy="50" fill="red" />
</svg>
```

as the code.


## notes
[^chris_2022]: Kolade Chris, "What is an SVG File", freeCodeCamp, 1 Jun 2022, url https://www.freecodecamp.org/news/what-is-an-svg-file/ [20240408].
[^davey_2023]: Mike Davey, "Why Developers Should Use SVG Files", WP Migrate, 6 Apr 2023, url https://deliciousbrains.com/svg-advantages-developers/ [20240408].
[^edwards_2023]: Carl Edwards, "What is SVG: Definition, Pros & Cons and How to Make", Fotor, 20 Dec 2023, url https://www.fotor.com/blog/what-is-svg/ [20240408].
[^fisher_2022]: Tim Fisher, "SVG Files: What They Are and How to Open & Convert Them", Livewire, 22 Sep 2022, url https://www.lifewire.com/p-4120603 [20240408].
