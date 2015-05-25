---
title: Use any Your Favorite Text Editors within irb
date: 2010/10/05
tags: IRB, Ruby
layout: post
---

Almost Ruby and Rails developers use Interactive Ruby Shell(irb) everyday to test 
their code snippets. We all understand how useful and important to us on this tool. 
But sometime I find a little bit difficult when I want to test a chunk of codes in irb 
because I have to write them line by line. Ruby has block, method, class, module, etc. 
So we can’t write them easily in irb. Tell you the truth, I made a lot of mistakes on 
closing blocks.

Have you ever thought you can use your favorite text editors within irb to solve 
the problems? Thank to [Jan Berkel](http://zegoggl.es/2009/04/integrating-vim-and-irb.html) 
and with help from [Charles Nutter](http://blog.headius.com/) who make our dream 
comes truth, you can use any your favorite text editors(I like Vim) within irb. 
And it is so easy to get it installed.

##Installation 
1. Install the interactive editor gem by running this at the command line:  
`gem install interactive_editor`
2. Create an `~/.irbrc` file if you don’t already have one, then paste the following into it:  

```ruby
require 'rubygems'
require 'interactive_editor'
```

You can see a demo on [Vimcasts](http://vimcasts.org/episodes/running-vim-within-irb)
