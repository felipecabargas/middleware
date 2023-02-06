---
title: '[TIL Tips] Iterate between Date objects in ruby'
tldr:
date: 2018-07-26
draft: false
tags:
  - development
---
Using the standard ruby `range`:

```ruby
(Date.new(2018, 01, 01)..Date.new(2018, 01, 30)).each do |date|
  # Do stuff with date
end
```

Using the `Date` method `upto`:

```ruby
Date.new(2018, 01, 01).upto(Date.new(2018, 01, 30)) do |date|
  # Do stuff with date
end
```
