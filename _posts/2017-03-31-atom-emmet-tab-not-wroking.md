---
layout: post
title: "[Atom] emmet tab키가 작동이 안될 때"
date: 2017-03-31
tags: [Atom, emmet, error]
excerpt: "atom emmet tab"
comments: true
---

Atom - Keymap - keymap.cson 파일에 다음 내용 추가하고 저장하기.

{% highlight cson %} 'atom-text-editor:not([mini])':
  'tab': 'emmet:expand-abbreviation-with-tab'
{% endhighlight %}
