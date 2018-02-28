---
layout: post
title: library vs. require in R
---

I've been long unsure about whether I should use `library()` or `require()` when loading a package in R.  [This post](https://yihui.name/en/2014/07/library-vs-require/) by Yihui Xie finally clarifies the issue for me.  Particularly memorable is the following principle/advice:

> When your code is going to fail, fail loudly, early, and with a relevant error message.
