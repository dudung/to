+++
title = 'html unordered list'
date = 2024-04-07T03:25:00+07:00
draft = false
math = true
tags = ['html', 'ul', 'li', 'css']
url = '0003'
authors = ['viridi']
+++
The use of HTML &lt;ul&gt; element and customization its &lt;li&gt; element <!--more-->


## intro
In a HTML file an unordered list of items, which is typically rendered as a bulleted list, is represented by the `<ul>` HTML element [^mdncontributors_2024] with the items represented by some `<li>` elements [^leverenz_2023]. Marker for the bullet of `<li>` element can be set to disc, circle, square, or without marker using CSS `list-style-type` property of the element [^fitzgerald_2023]. Further customization using CSS makes the choices for the bullet unlimited [^lemonaki_2021] and it is also possible to change the `<li>` elements layout, e.g. arranged in horizontal direction [^singh_2024], for website navigation bar [^roy_2022].

Some simple examples of using `<ul>` and `<li>` elements, with default style using only HTML, using CSS only, also with the help of CSS selectors [^rajora_2023], are given here.


## default
Following HTML code

```html
There are some animals that able to
<ul>
<li>fly</li>
<li>swim</li>
<li>run</li>
</ul>
and many others.
```

will produce

{{< div "background: #f8f8f8; padding: 10px 20px;" >}}
There are some animals that able to
<ul>
<li>fly</li>
<li>swim</li>
<li>run</li>
</ul>
and do many others.
{{< /div >}}

as the result. An unordered list can also be placed in other an unordered list. Let us advance the previous as follow

```html
There are some animals that able to
<ul>
  <li>fly</li>
  <ul>
    <li>bird</li>
    <li>bat</li>
    <li>butterfly</li>
  </ul>
  <li>swim</li>
  <ul>
    <li>fish</li>
    <li>octopus</li>
    <li>cetacean</li>
    <ul>
      <li>dolphin</li>
      <li>porpoise</li>
      <li>whale</li>
      <ul>
        <li>orca</li>
        <li>narwhal</li>
        <li>beluga</li>
      </ul>
    </ul>
    <li>crocodile</li>
  </ul>
  <li>run</li>
  <ul>
    <li>ostrich</li>
    <li>cheetah</li>
    <li>lizard</li>
    <li>spider</li>
  </ul>
</ul>
and do many others.
```

to produce

{{< div "background: #f8f8f8; padding: 10px 20px;" >}}
There are some animals that able to
<ul>
  <li>fly</li>
  <ul>
    <li>bird</li>
    <li>bat</li>
    <li>butterfly</li>
  </ul>
  <li>swim</li>
  <ul>
    <li>fish</li>
    <li>octopus</li>
    <li>cetacean</li>
    <ul>
      <li>dolphin</li>
      <li>porpoise</li
>
      <li>whale</li>
      <ul>
        <li>orca</li>
        <li>narwhal</li>
        <li>beluga</li>
      </ul>
    </ul>
    <li>crocodile</li>
  </ul>
  <li>run</li>
  <ul>
    <li>ostrich</li>
    <li>cheetah</li>
    <li>lizard</li>
    <li>spider</li>
  </ul>
</ul>
and do many others.
{{< /div >}}

In a `<ul>` element every `<li>` element can be substitued with another `<ul>` element, which makes nested unordered list. Notice that indentations are used just to make the code easier to read but do not affect the result, e.g.

```html
There are some animals that able to
<ul>
  <li>fly</li>
  <ul><li>bird</li><li>bat</li><li>butterfly</li></ul>
  <li>swim</li>
  <ul><li>fish</li><li>octopus</li><li>cetacean</li>
    <ul><li>dolphin</li><li>porpoise</li><li>whale</li>
      <ul><li>orca</li><li>narwhal</li><li>beluga</li></ul>
    </ul>
    <li>crocodile</li>
  </ul>
  <li>run</li>
  <ul><li>ostrich</li><li>cheetah</li><li>lizard</li><li>spider</li></ul>
</ul>
and do many others.
```

will produce the same as previous result, but as it can be seen, it is not so easy to read compared to previous code.


## border
Before using CSS to customize a unordered list, let us first use CSS to show area of `<ul>` and `<li>` elements. Following code

```html
<style>
ul.fruit0 {
  border: 1px solid blue;
  > li {
    border: 1px solid red;
  }
}
</style>

<ul class="fruit0">
  <li>Apple</li>
  <li>Banana</li>
  <li>Cucumber</li>
  <li>Durian</li>
</ul>
```

will produce

{{< div "background: #f8f8f8; padding: 10px 20px;" >}}
<style>
ul.fruit0 {
  border: 1px solid blue;
  > li {
    border: 1px solid red;
  }
}
</style>

<ul class="fruit0">
  <li>Apple</li>
  <li>Banana</li>
  <li>Cucumber</li>
  <li>Durian</li>
</ul>
{{< /div >}}

showing area of `<ul>` and `<li>` elements with blue and red borders, respectively.


## margin
Let us modify margin of the `<ul>` element first from its default value to `50px 40px 30px 20px` and

{{< div "background: #f8f8f8; padding: 10px 20px;" >}}
<style>
ul.fruit1 {
  border: 1px solid blue;
  margin: 50px 40px 30px 20px;
  > li {
    border: 1px solid red;
  }
}
</style>

<ul class="fruit1">
  <li>Apple</li>
  <li>Banana</li>
  <li>Cucumber</li>
  <li>Durian</li>
</ul>
{{< /div >}}

is the result. Top-margin is `50px`, right-margin is `40px`, bottom-margin is `30px`, and left-margin is `20px`. These margins if from its parent element. The modified sytle is

```css
ul.fruit1 {
  border: 1px solid blue;
  margin: 50px 40px 30px 20px;
  > li {
    border: 1px solid red;
  }
}
```

Notice the difference from previous `<style>` element. From now, if other HTML elements are the same, only content of `<style>` element is showed.

Let us now change only margin of `<li>` element as follow

```
ul.fruit2 {
  border: 1px solid blue;
  > li {
    border: 1px solid red;
    margin: 0px 100px 10px 40px;
  }
}
```

and get

{{< div "background: #f8f8f8; padding: 10px 20px;" >}}
<style>
ul.fruit2 {
  border: 1px solid blue;
  > li {
    border: 1px solid red;
    margin: 0px 100px 10px 40px;
  }
}
</style>

<ul class="fruit2">
  <li>Apple</li>
  <li>Banana</li>
  <li>Cucumber</li>
  <li>Durian</li>
</ul>
{{< /div >}}

as the result. Notice that those margins affecting layout of `<li>` elements inside its parent element, which is the `<ul>` element. It also affecting between elements within the same parent element.


## padding
After studying margin style in brief, let us now do that for padding.

Following style

```css
ul.fruit3 {
  border: 1px solid blue;
  padding: 40px 30px 20px 10px;
  > li {
    border: 1px solid red;
  }
}
```

will produce

{{< div "background: #f8f8f8; padding: 10px 20px;" >}}
<style>
ul.fruit3 {
  border: 1px solid blue;
  padding: 40px 30px 20px 10px;
  > li {
    border: 1px solid red;
  }
}
</style>

<ul class="fruit3">
  <li>Apple</li>
  <li>Banana</li>
  <li>Cucumber</li>
  <li>Durian</li>
</ul>
{{< /div >}}

as the result. Notice that padding is affecting its child elements, where in this case are the `<li>` elements.

Then following result is obtained

{{< div "background: #f8f8f8; padding: 10px 20px;" >}}
<style>
ul.fruit4 {
  border: 1px solid blue;
  > li {
    border: 1px solid red;
    padding: 40px 30px 20px 10px;
  }
}
</style>

<ul class="fruit4">
  <li>Apple</li>
  <li>Banana</li>
  <li>Cucumber</li>
  <li>Durian</li>
</ul>
{{< /div >}}

using

```css
ul.fruit4 {
  border: 1px solid blue;
  > li {
    border: 1px solid red;
    padding: 40px 30px 20px 10px;
  }
}
```

as the style. Since child element of a `<li>` element is fruit name, then in it adds padding inside the element.


## margin, border, padding
The three CSS properties, margin, border, and padding, have same value formats, which are

+ all-sides, e.g. `margin: 10px;`,
+ top-bottom right-left, e.g. `border: 4px 8px;`,
+ top right bottom left, e.g. `padding: 10px 30px 5px 20px;`.

Or it can also be set for each side separetely
+ top side only, e.g. `border-top: 10px;`,
+ right side only, e.g. `padding-right: 2px;`,
+ bottom side only, e.g. `margin-bottom: 5px;`,
+ left side only, e.g. `border-left: 4px;`.


## markers
There are four default options for `<li>` element bullet, which are three markers `disc`, `circle`, `square`, and addition no marker `none`. Let us use following code, where the style is set in each `<li>` element directly.

{{< div "background: #f8f8f8; padding: 10px 20px;" >}}
<ul>
  <li>Default</li>
  <li style='list-style-type: disc;'>Apple</li>
  <li style='list-style-type: circle;'>Banana</li>
  <li style='list-style-type: square;'>Coconut</li>
  <li style='list-style-type: none;'>Durian</li>
</ul>
{{< /div >}}

Above result is obtained using following code

```html
<ul>
  <li>Default</li>
  <li style='list-style-type: disc;'>Apple</li>
  <li style='list-style-type: circle;'>Banana</li>
  <li style='list-style-type: square;'>Coconut</li>
  <li style='list-style-type: none;'>Durian</li>
</ul>
```

Notice that default marker is `disc`.

Then, it is possible to user other markers for `<li>` element? Yes, it is possible.


## notes
[^fitzgerald_2023]: Anna Fitzgerald, "How to Create an Unordered List in HTML [+Examples]", HubSpot, 15 Aug 2023, url https://blog.hubspot.com/website/unordered-list-html [20240407].
[^lemonaki_2021]: Dionysia Lemonaki, "HTML Bullet Points – How to Create an Unordered List with the <ul> Tag Example", freeCodeCamp, 30 Sep 2021, url https://www.freecodecamp.org/news/html-bullet-points-how-to-create-an-unordered-list-with-the-ul-tag-example/ [20240407].
[^leverenz_2023]: Andy Leverenz, "HTML Element: li", Envato Tuts+, 24 Oct 2024, url https://webdesign.tutsplus.com/html-element-li--cms-107838a [20240407].
[^mdncontributors_2024]: MDN contributors, "<ul>: The Unordered List element", MDN Web Docs, moz:lla, 26 Mar 2024, url https://developer.mozilla.org/en-US/docs/Web/HTML/Element/ul [20240407].
[^rajora_2023]: Harish Rajora, "A Complete Guide to CSS Selectors", Medium, 10 Nov 2023, url https://medium.com/p/0cf15377e1c3 [20240407].
[^roy_2022]: Kasturi Roy, "Navigation bar design best practices", WebFlow, 7 Dec 2022, url https://webflow.com/blog/navigation-bar-design [20240407].
[^singh_2024]: Amit Singh, "HTML Unordered Lists", GeeksforGeeks, 15 Mar 2024, url https://www.geeksforgeeks.org/html-unordered-lists/ [20240407].
