+++
title = 'some html elements with js on hugo'
date = 2024-04-11T05:19:00+07:00
draft = false
math = true
tags = ['hugo', 'html', 'css', 'js']
url = '0007'
authors = ['viridi']
+++
Display HTML elements on Hugo with JS <!--more-->


## intro
One of the feature of Hugo static pages is its support to use JS for dynamic content, which is in this post only to show some HTML elements. Since Hugo does not allow to execute JS directly from its post, a shortcode 'js` is build within 8 lines of code.


## shortcode
In order to embed JS in Hugo posts, a shortcode named `js` is made with following content

```
{{- $seed := "foo" -}}
{{- $id := delimit (shuffle (split (md5 $seed) "" )) "" -}}
<div id="{{ $id }}">
<script>
let js = document.getElementById("{{ $id }}");
{{- .Inner | safeJS -}}
</script>
</div>
```

and called within post this way


```
{{</* js */>}}
console.log(js);
{{</* /js */>}}
```

where `js` is the container element, a `<div>` as parent element, of the script. As the result

{{< js >}}
console.log(js);
{{< /js >}}

```
<div id="bfde881d4f4bce8fcc426ccca5d54acd">
  <script>
    let js = document.getElementById("bfde881d4f4bce8fcc426ccca5d54acd");
    console.log(js);
  </script>
</div>
```

will be shown in browser JS console. Value of `id` will be generated randomly to assure that each script will have unique id.


## notes
..
