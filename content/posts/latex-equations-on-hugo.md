+++
title = 'latex equations on hugo'
date = 2024-04-12T07:12:00+07:00
draft = false
math = true
tags = ['latex', 'equation', 'katex', 'hugo', 'mhchem']
url = '0008'
authors = ['viridi']
+++
LaTex equations with KaTex and their code <!--more-->


## intro
I have just informed today that both MathJax and KateX provide support for chemical equations [^authorshugo_2024], but for KaTeX the [mhchem](https://mhchem.github.io/MathJax-mhchem/) extension should be enabled first [^authorskatex_2024]. This post showing LaTeX equations supported by KaTeX in a Hugo post.

## front matter
Following is front matter for this post

```
+++
title = 'latex equations on hugo'
date = 2024-04-12T07:12:00+07:00
draft = false
math = true
tags = ['latex', 'equation', 'katex', 'hugo', 'mhchem']
url = '0008'
authors = ['viridi']
+++
```

which is using TOML format. There are also two other formats supported by Hugo [^authorshugo_2024b]. The line

```
math = true
```

must be supplied in order to able to render LaTex equations using KaTex through `math` partial.


## partial
In my installed Hugo (v0.124.1-db083b05f16c945fec04f745f0ca8640560cf1ec+extended windows/amd64 BuildDate=2024-03-20T11:40:10Z VendorInfo=gohugoio) I put a partial `math.html` in `layouts\partials\posts` folder, where its contents is as follow

```
{{- if or (.Params.math) (.Site.Params.math) (.Params.katex) (.Site.Params.katex) -}}

  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.16.4/dist/katex.min.css"
    integrity="sha384-vKruj+a13U8yHIkAyGgK1J3ArTLzrFGBbBc0tDp4ad/EyewESeXE/Iv67Aj8gKZ0" crossorigin="anonymous">
  {{/* The loading of KaTeX is deferred to speed up page rendering */}}
  <script defer src="https://cdn.jsdelivr.net/npm/katex@0.16.4/dist/katex.min.js"
    integrity="sha384-PwRUT/YqbnEjkZO0zZxNqcxACrXe+j766U2amXcgMg5457rve2Y7I6ZJSm2A0mS4" crossorigin="anonymous"></script>
 
  <script defer src="https://cdn.jsdelivr.net/npm/katex@0.16.4/dist/contrib/auto-render.min.js"
    integrity="sha384-+VBxd3r6XgURycqtZ117nYw44OOcIax56Z4dCRWbxyPt0Koah1uHoK0o4+/RRE05" crossorigin="anonymous"
    onload="renderMathInElement(document.body,
      {
        delimiters: [
          {left: '$$', right: '$$', display:true},
          {left: '$', right: '$', display:false},
          {left: '\\(', right: '\\)', display: false},
          {left: '\\[', right: '\\]', display: true}
        ]
      }
    );"></script>
{{- end -}}
```

And according to information obtained from mhchem extension on GitHub following lines

```
<!--
url https://github.com/KaTeX/KaTeX/tree/main/contrib/mhchem [20240412]
-->
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.16.10/dist/contrib/mhchem.min.js" integrity="sha384-ifpG+NlgMq0kvOSGqGQxW1mJKpjjMDmZdpKGq3tbvD3WPhyshCEEYClriK/wRVU0"  crossorigin="anonymous"></script>
<!-- -->    
```

should be put it after the line that calls `katex.js`. And before the line that calls `auto-render.js`, if only you use it.


## mhchem
Example equation from GitHub

$$
C_p[\ce{H2O(l)}] = \pu{75.3 J // mol K}
$$

is obtained with

```tex
$$
C_p[\ce{H2O(l)}] = \pu{75.3 J // mol K}
$$
```

Other examples are also available [^hensel_2024], e.g.

$$
\ce{CH4 + 2 $\left( \ce{O2 + 79/21 N2} \right)$}
$$

using

```tex
$$
\ce{CH4 + 2 $\left( \ce{O2 + 79/21 N2} \right)$}
$$
```

$$
\ce{^234_90Th -> ^0_-1\beta{} + ^234_91Pa}
$$

using

```tex
$$
\ce{^234_90Th -> ^0_-1\beta{} + ^234_91Pa}
$$
```

$$
\ce{A-B=C#D}
$$

using

```tex
$$
\ce{A-B=C#D}
$$
```

and

$$
\ce{Zn^2+
<=>[+ 2OH-][+ 2H+]
$\underset{\text{amphoteres Hydroxid}}{\ce{Zn(OH)2 v}}$
<=>[+ 2OH-][+ 2H+]
$\underset{\text{Hydroxozikat}}{\ce{[Zn(OH)4]^2-}}$
}
$$

using

```tex
\ce{Zn^2+
<=>[+ 2OH-][+ 2H+]
$\underset{\text{amphoteres Hydroxid}}{\ce{Zn(OH)2 v}}$
<=>[+ 2OH-][+ 2H+]
$\underset{\text{Hydroxozikat}}{\ce{[Zn(OH)4]^2-}}$
}
```

## equation number
To have following result

$$\tag{10}
x
$$

following code

```tex
$$\tag{10}
x
$$
```

is required. Notice that the value `10` can be substituted with any string.


## fraction
To have following result

$$
x = \frac{y}{z}
$$

following code


```tex
$$
x = \frac{y}{z}
$$
```

is required. The `{y}` and `{z}` can be substituted with any LeTex expression, e.g. fractions as numerator and denominator

$$
x = \frac{1 + \frac{a}{b}}{1 - \frac{c}{d}}
$$

with

```tex
$$
x = \frac{1 + \frac{a}{b}}{1 - \frac{c}{d}}
$$
```

as the code.


## notes
[^authorshugo_2024]: Hugo Authors, "Mathematics in Markdown", hugoDocs -- GitHub, 20 Feb 2024, url https://github.com/gohugoio/hugoDocs/blob/c60cd20a/content/en/content-management/mathematics.md [20240412].
[^authorshugo_2024b]: Hugo Authros, "Front matter", hugoDocs, 8 Apr 2024, url https://gohugo.io/content-management/front-matter/ [20240412].
[^authorskatex_2024]: KaTeX Authors, "mhchem extension", KaTeX -- GitHub, 25 Mar 2024, url https://github.com/KaTeX/KaTeX/tree/ab323598f/contrib/mhchem [202404212].
[^hensel_2024]: Martin Hensel, "The mhchem Bundle Documentation for the LATEX Packages mhchem v4.10, hpstatement v2.1.0 and rsphrase v3.11", url https://www.ctan.org/pkg/mhchem [20240412].
