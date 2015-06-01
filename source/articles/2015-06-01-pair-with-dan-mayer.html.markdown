---
title: Pair with Dan Mayer
date: 2015-06-01 16:54 UTC
tags: PairWithMe, RubyFriends
layout: post
---

[Dan Mayer](http://www.mayerdan.com/)(@danmayer) and I met each other on the internet when he had planned to 
visit Cambodia.  He pinged me on twitter, then we setup a plan to meet when he
was going to be here.  We had a great lunch together as we had planned and talked
about many different things from people to programming.

This week, we had a chance to have a #pairwithme session together. We looked at
few ideas to do in the session, then we decided to pick one idea is to do a spike
to create table of contents of a project's readme on Github. The idea is pretty simple. 
Everyone loves good documentations. For me whenever I come to a project's readme
that includes installation, Examples, Features, Development ..., I feel it's a 
good readme and it serves as a good documentation.

One problem that we usually face with a long good project's readme is when we have
to scroll up and down again and again when we want to navigate in different 
sections on the page which make me feel not good. What we are trying to solve 
is to grap all anchor links in readme and list them all on the page, then it helps us
be able to click on it to jump to that section easily. Dan posted about [our pairing as well](http://www.mayerdan.com/programming/2015/06/02/pair-programming-readme-toc/).

Below is the result from our spike or you get our bookmarklet([Readme TOC](javascript:(function(){function%20tocLink%28a%2Ce%2Cn%29%7Bvar%20s%3D%27%3Cli%20class%3D%22tooltipped%20tooltipped-w%22%20aria-label%3D%22%27+e+%27%22%3E%3Ca%20href%3D%22%27+n+%27%22%20aria-label%3D%22%27+e+%27%22class%3D%22js-selected-navigation-item%20sunken-menu-item%22%3E%3Cspan%20class%3D%22full-word%22%3E%27+e+%22%3C/span%3E%3C/a%3E%3C/li%3E%22%3Breturn%20s%7Dvar%20header%3D%22%3Cli%20class%3D%27tooltipped%20tooltipped-w%27%3E%3Cstrong%3E%26nbsp%3BTable%20of%20Contents%3C/strong%3E%3C/li%3E%22%2Crows%3D%5B%5D%3B%24%28%22a%5Bclass%3Danchor%22%29.each%28function%28a%2Ce%29%7B%24anchor%3D%24%28e%29%2C%24heading%3D%24anchor.parent%28%29%2Crows.push%28tocLink%28%24heading.prop%28%22tagName%22%29.toLowerCase%28%29%2C%24heading.text%28%29%2C%24anchor.attr%28%22href%22%29%29%29%7D%29%3Bvar%20template%3D%22%3Cdiv%20class%3D%27repository-sidebar%27%3E%3Cnav%20class%3D%27sunken-menu%20repo-nav%27%20role%3D%27navigation%27%3E%3Cdiv%20class%3D%27sunken-menu-separator%27%3E%3C/div%3E%3Cul%20class%3D%27sunken-menu-group%27%3E%22+header+rows.join%28%22%22%29+%22%3C/ul%3E%3C/nav%3E%3C/div%3E%22%3B%24%28%24%28%22.repository-with-sidebar.with-full-navigation%20.repository-sidebar%22%29%5B0%5D%29.append%28template%29%3B}());)):

![Github's Readme TOC](2015-06-01-pair-with-dan-mayer/github_readme_toc.jpg)

```js
function tocLink(heading, title, href) {
  var ele = '<li class="tooltipped tooltipped-w" aria-label="'+title+'">'+
    '<a href="'+href+'" aria-label="'+title+'"'+
    'class="js-selected-navigation-item sunken-menu-item">'+
    '<span class="full-word">'+title+'</span></a></li>'
   return ele;
}
 
var header = "<li class='tooltipped tooltipped-w'><strong>&nbsp;Table of Contents</strong></li>"
var rows = [];
 
$('a[class=anchor]').each(function(i, anchor) {
  $anchor = $(anchor);
  $heading = $anchor.parent();
  rows.push(
    tocLink(
      $heading.prop("tagName").toLowerCase(),
      $heading.text(),
      $anchor.attr('href')
    )
  );
})
 
var template = "<div class='repository-sidebar'><nav class='sunken-menu repo-nav' role='navigation'><div class='sunken-menu-separator'></div><ul class='sunken-menu-group'>"+
  header+rows.join('')+"</ul></nav></div>"
 
$($('.repository-with-sidebar.with-full-navigation .repository-sidebar')[0]).append(template);
```
