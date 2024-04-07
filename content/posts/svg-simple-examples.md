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
SVG, that stands for scalable vector graphis, is a web friendly vector-based file format used to render two-dimensional images on the internet, and it is written in pure XML [^chris_2022], which makes it can be created or edited using any text and code editor. Other than to code SVG, there is also a lot of drawing applications available that can be used to open and edit SVG files [^fisher_2022]. There are some reasons to use SVG, where one of them is SEO (search engine optimization) friendly that allowing keywords, descriptions, and links addition directly to the markup [^davey_2023]. Infinity scalability, small file size, editability, and accessiblity are advantages of SVG files, while complexity and browser support are the disadvantages [^edwards_2023]. Image stored as SVG does not require compression compared to other formats [^tey_2021].


## minimal lines
Let us make a SVG file with minimal content as displayed below

{{< div >}}
<svg height="100" width="100" style="background: #f8f8f8;">
  <circle r="45" cx="50" cy="50" fill="red" />
</svg>
{{< /div >}}

with

```svg
<svg height="100" width="100">
  <circle r="45" cx="50" cy="50" fill="red" />
</svg>
```

is the code.

Notice that above code if for SVG embeded inline in a HTML file. For serving the SVG as image/svg+xml or application/xhtml+xml or any other MIME type that causes the user agent to use an XML parser then it requires to add `xmlns="http://www.w3.org/2000/svg` attribute and value to `<svg>` element [^longson_2013].

The line `<circle r="45" cx="50" cy="50" fill="red" />` can be replaced by folowing lines

+ `<rect x="5" y="30" width="90" height="40" fill="blue" />`
+ `<ellipse rx="45" ry="20" cx="50" cy="50" fill="green" />`
+ `<line x1="20" y1="20" x2="80" y2="80" stroke="black" />`
+ `<polygon points="20,20 50,80 80,20" fill="magenta" />`
+ `<polyline points="20,80 50,20 80,80" stroke="magenta" fill="none" />`
+ `<path d="M20 20 L50 20 L25 50 v20 h30" fill="none" stroke="black" />`
+ `<text x="5" y="50" fill="darkgreen">Hello, World!</text>`

and you get the others basic SVG shapes and text, where

{{< div "width: 100px; display: inline-block;" >}}
<svg height="100" width="100" style="background: #f8f8f8;">
  <circle r="45" cx="50" cy="50" fill="red" />
</svg>
{{< /div >}}
{{< div "width: 100px; display: inline-block;" >}}
<svg height="100" width="100" style="background: #f8f8f8;">
  <rect x="5" y="30" width="90" height="40" fill="blue" />
</svg>
{{< /div >}}
{{< div "width: 100px; display: inline-block;" >}}
<svg height="100" width="100" style="background: #f8f8f8;">
  <ellipse rx="45" ry="20" cx="50" cy="50" fill="green" />
</svg>
{{< /div >}}
{{< div "width: 100px; display: inline-block;" >}}
<svg height="100" width="100" style="background: #f8f8f8;">
  <line x1="20" y1="20" x2="80" y2="80" stroke="black" />
</svg>
{{< /div >}}

{{< div "width: 100px; display: inline-block;" >}}
<svg height="100" width="100" style="background: #f8f8f8;">
  <polygon points="20,20 50,80 80,20" fill="magenta" />
</svg>
{{< /div >}}
{{< div "width: 100px; display: inline-block;" >}}
<svg height="100" width="100" style="background: #f8f8f8;">
  <polyline points="20,80 50,20 80,80" stroke="magenta" fill="none" />
</svg>
{{< /div >}}
{{< div "width: 100px; display: inline-block;" >}}
<svg height="100" width="100" style="background: #f8f8f8;">
  <path d="M20 20 L50 20 L25 50 v20 h30" fill="none" stroke="black" />
</svg>
{{< /div >}}
{{< div "width: 100px; display: inline-block;" >}}
<svg height="100" width="100" style="background: #f8f8f8;">
  <text x="5" y="50" fill="darkgreen">Hello, World!</text>
</svg>
{{< /div >}}

are the results and also with the first one. More complex drawing can be built based on above given shapes and text.


## notes
[^chris_2022]: Kolade Chris, "What is an SVG File", freeCodeCamp, 1 Jun 2022, url https://www.freecodecamp.org/news/what-is-an-svg-file/ [20240408].
[^davey_2023]: Mike Davey, "Why Developers Should Use SVG Files", WP Migrate, 6 Apr 2023, url https://deliciousbrains.com/svg-advantages-developers/ [20240408].
[^edwards_2023]: Carl Edwards, "What is SVG: Definition, Pros & Cons and How to Make", Fotor, 20 Dec 2023, url https://www.fotor.com/blog/what-is-svg/ [20240408].
[^fisher_2022]: Tim Fisher, "SVG Files: What They Are and How to Open & Convert Them", Livewire, 22 Sep 2022, url https://www.lifewire.com/p-4120603 [20240408].
[^longson_2013]: Robert Longson, sleske, "Are SVG parameters such as 'xmlns' and 'version' needed?", Stack Overflow, 26 Sep 2018, url https://stackoverflow.com/a/18468348/9475509 [20240408].
[^tey_2021]: Estee Tey, "Introduction to Scalable Vector Graphics (SVG)", DEV Community, 16 Nov 2021, url https://dev.to/lyqht/introduction-to-scalable-vector-graphics-svg-734 [20240408].