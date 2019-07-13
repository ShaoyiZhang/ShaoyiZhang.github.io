---
layout: post
title: Use vim-plug to manage plugins
comments: true
---
* content
{:toc}

When I started to use Vim, I chose vundle as the plugin manager. Recently, I tried out [vim-plug](https://github.com/junegunn/vim-plug) and prefers it over vundle for plug's the superior download speed(parallel downing). Here's how to install vim-plug and the .vimrc file I'm currently using.

<!--more-->
### Make sure you are using the full Vim
Ubuntu comes with Vim-tiny, which, as its name suggests, is tiny and lacks many features. Here's how to replace it with regular Vim.

{% highlight bash %}
sudo apt remove --assume-yes vim-tiny
sudo apt update
sudo apt install --assume-yes vim
{% endhighlight %}

### Install vim-plug
In shell, run
{% highlight bash %}
curl -fLo ~/.vim/autoload/plug.vim --create-dirs https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
{% endhighlight %}
### Install plugins using vim-plug
In your ~/.vimrc, add
{% highlight vim %}
" Specify a directory for plugins
" - Avoid using standard Vim directory names like 'plugin'
call plug#begin('~/.vim/plugged')

" Make sure you use single quotes
Plug 'scrooloose/nerdtree'
Plug 'Yggdroot/indentLine'
Plug 'Valloric/YouCompleteMe'
Plug 'tomasiser/vim-code-dark'
Plug 'itchyny/lightline.vim'
Plug 'tpope/vim-surround'
Plug 'altercation/vim-colors-solarized'
Plug 'junegunn/rainbow_parentheses.vim'

" Initialize plugin system
call plug#end()

" Use ctrl + n to open NERDTree
map <C-n> :NERDTreeToggle<CR>

" Open NERDTree automatically when vim starts up on opening a directory
autocmd StdinReadPre * let s:std_in=1
autocmd VimEnter * if argc() == 1 && isdirectory(argv()[0]) && !exists("s:std_in") | exe 'NERDTree' argv()[0] | wincmd p | ene | exe 'cd '.argv()[0] | endif

" Open a NERDTree automatically when vim starts up if no files were specified
autocmd StdinReadPre * let s:std_in=1
autocmd VimEnter * if argc() == 0 && !exists("s:std_in") | NERDTree | endif

" Close vim if the only window left open is a NERDTree
autocmd bufenter * if (winnr("$") == 1 && exists("b:NERDTree") && b:NERDTree.isTabTree()) | q | endif

syntax on
let g:solarized_termcolors=16
set t_Co=256
set background=light
colorscheme solarized
set number
set ruler
set history=1000
set autoindent
set smartindent
set expandtab
set showmatch
set tabstop=4
set softtabstop=4
set shiftwidth=4
set hlsearch
set scrolloff=3
let g:indentLine_enabled = 1
set showmode
set showcmd
set encoding=utf-8
filetype indent on
set wrap
set linebreak
set incsearch
set ignorecase
set smartcase
set autoread
set listchars=tab:»■,trail:■
set list
set cursorline
set wildmenu
set wildmode=longest:list,full
set laststatus=2 "always show status bar (lightline)
set noshowmode   "hide mode on bottom line
set backspace=indent,eol,start " make backspace work like most other programs
let g:lightline = { 'colorscheme': 'solarized'}
{% endhighlight %}
Then, inside Vim, run
{% highlight bash %}
:PlugInstall # Use :PluginInstall for Vundle
{% endhighlight %}
