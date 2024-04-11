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
There are some static site generators, where one of the free ones is Hugo [^rajora_2023]. And one of the feature of Hugo static pages is its support to use JS for dynamic content, but in this post only feature to display some HTML elements is shown. Since normally Hugo does not allow to execute JS directly from its post [^m_2020] and it requires defining a shortcode [^pyth0n_2017], a shortcode `js` is provided, that has 10 lines of code.


## shortcode
In order to embed JS in Hugo posts, a shortcode named `js` is made with following content

```
{{- $seed := "foo" -}}
{{- $id := delimit (shuffle (split (md5 $seed) "" )) "" -}}
<div id="{{- $id -}}">
<script>
js = document.getElementById("{{- $id -}}");
var fn = "f_{{- $id -}}";
window[fn] = function() { {{- .Inner | safeJS -}} }
window[fn]();
</script>
</div>
```

Notice that `js` and `fn` variable are global variables and they are reused every time the shortcode is called. To avoid error message that a variable is already declared, all script in `.Inner` of Hugo shortoce is place inside a function whose name is generated randomly, each time the shortcode is called.

Then, the shortcode is called within a post this way


```
{{</* js */>}}
console.log(js);
{{</* /js */>}}
```

where `js` is the container element, a `<div>` as parent element, of the script. An as the result

{{< js >}}
console.log(js);
{{< /js >}}

```
<div id="4bc1ce45e8dcacdf44d6ccda2bcf588f">
  <script>
    js = document.getElementById("4bc1ce45e8dcacdf44d6ccda2bcf588f");
    var fn = "f_4bc1ce45e8dcacdf44d6ccda2bcf588f";
    window[fn] = function() {
    console.log(js);
    }
    window[fn]();
  </script>
</div>
```

will be shown in browser JS console [^vidas_2015]. Value of `id` will be generated randomly to assure that each script will have unique id.


## button
Let us now just display a button

{{< js >}}
let btn = document.createElement("button")
btn.innerHTML = "OK";
js.appendChild(btn);
{{< /js >}}

with following script

```
{{</* js */>}}
let btn = document.createElement("button")
btn.innerHTML = "OK";
js.appendChild(btn);
{{</* /js */>}}
```

You can click it or hover mouse pointer on it, but nothing happen since how response on such events have not been defined.

Now, 


## notes
[^m_2020]: n_m, "Hugo use inline javascript within posts", Stack Overflow 28 Jul 2020, url https://stackoverflow.com/a/63138441/9475509 [20240411].
[^pyth0n_2017]: Pyth0n, "Insert js in a Hugo post", Stack Overflow, 8 Mar 2017, url https://stackoverflow.com/a/42672833/9475509 [20240411].
[^rajora_2023]: Harish Rajora, "A Beginner’s Guide to Static Site Generator", Medium, 13 Dec 2023, url https://medium.com/p/806583fd81f3 [20240411].
[^vidas_2015]: Šime Vidas, Russ Bateman, "How do I open the JavaScript console in different browsers?", Webmasters Stack Exchange, 17 Oct 2019, url https://webmasters.stackexchange.com/a/77337/138202 [20240411].
