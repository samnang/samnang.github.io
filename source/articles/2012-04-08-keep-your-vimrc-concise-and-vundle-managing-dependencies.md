--- 
title: Keep your vimrc concise and Vundle managing dependencies
date: 2012/04/08
tags: Vim, Vundle, Tools
description: After I read some posts on Vim University, and especially a post on Don't be proud of an empty vimrc, then it helps me to think about revising my vimrc configuration.
layout: post
---

I have been using vimming for a year now, and it became my primary text editor by then. Before that time, I only used it for editing configuration files on ssh server. It worths learning Vim because it is almost used in my day to day freelancing job work for pair programming, and we find out using Vim + Screen GNU/Tmux increase our productivity and reduce friction on development.

After I read some posts on [Vim University](http://vimuniversity.com/), and especially a post on [Don't be proud of an empty vimrc](http://vimuniversity.com/posts/dont-be-proud-of-an-empty-vimrc), then it helps me to think about revising my vimrc configuration. I have switched to use [Vundle](https://github.com/gmarik/vundle) for managing vim plugins because I don't have to use [pathogen.vim](https://github.com/tpope/vim-pathogen/) with using git submodules or writing a Rake task to mange plugins. Vundle helps us to manage plugin as easy as you never though of:

<script src="https://gist.github.com/2338370.js?file=vimrc"></script>
<noscript>
    " Let Vundle manage Vundle
    Bundle 'gmarik/vundle'
    
    Bundle 'tpope/vim-rails'
    Bundle 'tpope/vim-rake'
    Bundle 'tpope/vim-fugitive'
    Bundle 'tpope/vim-surround'
    Bundle 'tpope/vim-endwise'
    Bundle 'scrooloose/nerdtree'
    Bundle 'kien/ctrlp.vim'
    Bundle 'msanders/snipmate.vim'
    Bundle 'ervandew/supertab'
    Bundle 'mileszs/ack.vim'
    Bundle 'scrooloose/nerdcommenter'
    Bundle 'scrooloose/syntastic'
    Bundle 'Raimondi/delimitMate'
    Bundle 'mattn/zencoding-vim'
    Bundle 'vim-scripts/IndexedSearch'
    Bundle 'vim-scripts/L9.git'
    Bundle 'vim-scripts/matchit.zip'
    Bundle 'godlygeek/tabular'
    Bundle 'git://gist.github.com/287147.git'
    
    Bundle 'tpope/vim-cucumber'
    Bundle 'tpope/vim-haml'
    Bundle 'pangloss/vim-javascript'
    Bundle 'kchmck/vim-coffee-script'
</noscript>

Of course, I also revised my [vimrc](https://github.com/samnang/dotfiles/blob/master/vimrc) configuration, and I also kept only minimum configuration that I understand and use it for my day to day job. I deleted some settings that I stole and didn't understand them from vary sources. At the end of the day, I have managed my vimrc has only about 100 lines. How is about yours?
