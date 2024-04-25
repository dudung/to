+++
title = 'old posts migration'
date = 2024-04-25T09:02:00+07:00
draft = false
math = true
tags = ['posts migration', 'jekyll', 'hugo']
url = '0021'
authors = ['viridi']
+++
Incomplete documentation for manual migration of old posts <!--more-->


## intro
Some of my old posts were still for Jekyll post, while this and the newer ones are already for Hugo post. I need to tune something in order to make it works for all old posts, e.g. images, mathematical expression support, comment, etc. One of the reasons while people switching from Jekyll to Hugo is to obtain stability and robustness [^congdon_2018] and also additional feature like the ability to create, modify, build, and preview the site all within R, using the blogdown package [^richards_2020]. Assuring that folder structure, e.g. for images, from Jekyll recognized by Hugo is one thing that must be settled.

One of the problems in migration from jekyll to Hugo is number of posts that could be hundreds of them, even most of them are just ramblings and brain dumps [^jing_2020], where in my case there are about 740 posts to migrate. I have already encountered some problems like folder for images, Liquid templating language to Hugo shortcodes translation, and math support, since Jekyll is using MathJax, while Hugo is using KaTeX. I think I can manage it, since there is a report that the migration was mostly painless [^guo_2018], but for tha math support it was easier said than done [^newman_2022].


## problems
+ Support for mathematical expression: MathJax to KaTeX.
+ Data conversion: Manually edited.
+ Post URL: Collision prevention between new posts and being migrated posts.
+ Images: Fix link or just use the image there or just text.
+ JS apps: Shortcodes or code in post.
+ Tags: Accept all old ones or transform it to suit current tags, or even tagged as their repo.


## mathjax
File is `layouts\partials\posts\mathjax.html` with content as follow.

```html
{{- if or (.Params.mathjax) -}}
<script>
  MathJax = {
    tex: {
      inlineMath: [['$', '$'], ['\\(', '\\)']],
      displayMath: [['$$','$$'], ['\\[', '\\]']],
      processEscapes: true,
      processEnvironments: true,
			tags: 'ams',
    },
    options: {
      skipHtmlTags: [
				'script',
				'noscript',
				'style',
				'textarea',
				'pre'
			]
    }
  };
</script>

<script
	type="text/javascript"
	id="MathJax-script"
	async 
	src="https://cdn.jsdelivr.net/npm/\
	mathjax@3/es5/tex-mml-chtml.js"
	>
</script>
{{- end -}}
```


## katex
File is `layouts\partials\posts\math.html` with content as follow.

```html
{{- if or (.Params.math) (.Site.Params.math) (.Params.katex) (.Site.Params.katex) -}}

  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.16.4/dist/katex.min.css"
    integrity="sha384-vKruj+a13U8yHIkAyGgK1J3ArTLzrFGBbBc0tDp4ad/EyewESeXE/Iv67Aj8gKZ0" crossorigin="anonymous">
  {{/* The loading of KaTeX is deferred to speed up page rendering */}}
  <script defer src="https://cdn.jsdelivr.net/npm/katex@0.16.4/dist/katex.min.js"
    integrity="sha384-PwRUT/YqbnEjkZO0zZxNqcxACrXe+j766U2amXcgMg5457rve2Y7I6ZJSm2A0mS4" crossorigin="anonymous"></script>

<!--
url https://github.com/KaTeX/KaTeX/tree/main/contrib/mhchem [20240412]
-->
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.16.10/dist/contrib/mhchem.min.js" integrity="sha384-ifpG+NlgMq0kvOSGqGQxW1mJKpjjMDmZdpKGq3tbvD3WPhyshCEEYClriK/wRVU0"  crossorigin="anonymous"></script>
<!-- -->    
    
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


## usage
File is `layouts\posts\single.html` with content as follow.
```html
{{ define "main" }}
  <h1>{{ .Title }}</h1>

  {{ $dateMachine := .Date | time.Format "2006-01-02T15:04:05-07:00" }}
  {{ $dateHuman := .Date | time.Format ":date_long" }}
  
  <!--div class='author'>{{- .Params.author -}}</div-->
  
  
  <!--ul class="authors">
  {{ range .Params.authors }}
    <li>{{ . }}</li>
  {{ end }}
  </ul-->
  
  {{- range .Params.authors }}
    {{- with $.Site.GetPage "taxonomyTerm" (printf "authors/%s" (urlize .)) }}
      <figure class='authors'>
        <img src="{{ .Params.photo }}" alt=""/>
        <figcaption>
          <a href="{{ .Permalink }}">{{ .Params.name }}</a>
        </figcaption>
      </figure>
    {{ end }}
  {{ end }}
  
  <div class='readingtimedate'>
    {{ partial "reading-time.html" . }} &middot;
    <time datetime="{{ $dateMachine }}">{{ $dateHuman }}</time>
  </div>
  
  {{ .Content }}
  {{ partial "terms.html" (dict "taxonomy" "tags" "page" .) }}
  
  {{ partial "posts/math.html" . }}
  {{ partial "posts/mathjax.html" . }}
{{ end }}
```

Notice the last third and second lines.


## date
Jekyll is using `date: 2021-09-29 09:57:00 +07` in its post front matter, while Hugo is using `date = 2024-04-25T09:02:00+07:00`. The problem is not just YAML vs TOML but the date information stored as string in post parameters, since the first has two spaces and the second only a long single word. And also the minutes in the UTS offsets.

Withour writing a program, the hundreds of posts must be edited manually.


## notes
[^congdon_2018]: Ben Congdon, "Switching from Jekyll to Hugo", 6 Jun 2018, url https://benjamincongdon.me/blog/2018/06/06/Switching-from-Jekyll-to-Hugo/ [20240425].
[^guo_2018]: Danny Guo, "Migrating from Jekyll to Hugo", 24 Jun 2018, url https://www.dannyguo.com/blog/migrating-from-jekyll-to-hugo [20240425].
[^jing_2020]: Chen Hui Jing, "Migrating from Jekyll to Hugo", 29 Apr 2020, url https://chenhuijing.com/blog/migrating-from-jekyll-to-hugo/ [20240425].
[^newman_2022]: Marcus R.A. Newman, "Adventures in making this website:
rendering LaTeX maths", 28 Nov 2022, url https://prefetch.eu/blog/2022/website-adventures-maths/ [20240425].
[^richards_2020]: Clark Richards, "Migrating this site from Github+Jekyll to Netlify+Hugo (with the amazing blogdown package)", 30 Aug 2024, url https://www.clarkrichards.org/2020/08/30/migrating-to-hugo-with-blogdown/ [20240425].
[^wang_2024]:  XiaoFeng Wang, "Migrate from Jekyll to Hugo", Luddy School, Indiana University Bloomington, 10 Mar 2014, url https://homes.luddy.indiana.edu/xw7/post/migrate-from-jekyll/ [20240425].
