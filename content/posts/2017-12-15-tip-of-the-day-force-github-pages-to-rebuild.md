---
title: '[TIL Tips] How to force GitHub pages to rebuild'
tldr:
date: 2017-12-15
draft: false
tags:
  - development
---
This is both a `git` tip for some, but the only real usage that I have for this command is to force GitHub pages to rebuild this blog without making any changes to it:

```
git commit -m 'REBUILD ALL THE THINGS!' --allow-empty
git push origin master
```
