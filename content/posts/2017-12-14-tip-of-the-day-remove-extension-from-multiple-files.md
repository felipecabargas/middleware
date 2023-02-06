---
title: '[TIL Tips] How to remove the extension of multiple files at once (CLI)'
tldr:
date: 2017-12-14
draft: false
tags:
  - development
---
This is another simple one (tested on both Linux & Mac):

```
find ./ -name '*.ext' | while read f; do mv "$f" "${f%.ext}"; done
```

Change `ext` for your desired extension.

Using `find` is better than using `replace` because the latter will replace the first match of `.ext` instead.
