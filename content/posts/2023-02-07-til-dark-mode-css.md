---
title: '[TIL Tips] Simple CSS-only Dark Mode support'
date: 2023-02-07
draft: false
tags:
  - development
---

![Dark Mode](/blog/darkmode.gif)

One of the features I loved about the new theme of the blog, was the auto-support for System-based Dark Mode. I wanted to also implement a similar theme on my [main homepage](https://felipe.codes).

Sadly, the implementation in the blog uses Javascript, and as a _extremely bad_ frontender I prefer to always avoid it, specially if it involves localStorage and I have to change the CSS anyways.

After some digging, I found info about [`prefers-color-scheme`](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-color-scheme) and I'm extremely impressed on how simple it is to implement: it only requires 2 `@media` queries.

You need to add these 2 blocks to your main CSS/SCSS file and you're done:

```css
@media (prefers-color-scheme: dark) {
 ...
}

@media (prefers-color-scheme: light) {
 ...
}
```

> You can also add a `no-preference` value in case the user hasn't declared a preference, but it only works in Safari and some mobile browsers.

In my case, this is the code I used on the website:

```scss
$background-light: #ffffff;
$background-dark: #202124;

$highlight-light: #ff0000;
$highlight-dark: #50fa7b;

$text: #272727;
$text-dark: #ffffff;

// Media queries
//
@media (prefers-color-scheme: dark) {
  body {
    background: $background-dark;
    color: $text-dark;
  }

  a{
    color: $text-dark;
  }

  a:hover {
    color: $highlight-dark;
  }

  h1#home-title {
    border-bottom: 5px solid $highlight-dark;
  }
}

@media (prefers-color-scheme: light) {
  body {
    background: $background-light;
  }

  a:hover {
    color: $highlight-light;
  }

  h1#home-title {
    border-bottom: 5px solid $highlight-light;
  }
}
```

I hope this is useful and I'm looking forward to seeing your websites _in the dark_.
