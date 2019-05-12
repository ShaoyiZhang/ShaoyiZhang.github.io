---
layout: post
title: Solarize Vim and Ubuntu terminal
---

After trying both dark and light  themes for serval month, I decided to use Solarized Light colorscheme for all editors and IDEs. I think the background color should match the surrounding to reduce eye tiredness. At work or at home, I always work/game in a bright area. Therefore, a lighter theme like Solarized Light is a natural choice for me.

<!--more-->
### Solarize Ubuntu terminal

{% highlight bash %}
sudo apt-get install dconf-cli
git clone https://github.com/Anthony25/gnome-terminal-colors-solarized.git
cd gnome-terminal-colors-solarized
./install.sh
{% endhighlight %}

### Solarize Vim
Add the following to your ~/.vimrc file. Assuming you are using **vim-plug** as a plugin manager
{% highlight bash %}
Plug 'altercation/vim-colors-solarized' # Use Plugin 'altercation/vim-colors-solarized' for Vundle
{% endhighlight %}
Inside Vim, run
{% highlight bash %}
:PlugInstall # Use :PluginInstall for Vundle
{% endhighlight %}
After the plugin is installed, add this to your ~/.vimrc
{% highlight bash %}
syntax on
let g:solarized_termcolors=16
set t_Co=256
set background=light
colorscheme solarized
{% endhighlight %}
If your terminal color looks ugly, you might want to tweak the value of solarized_termcolors and t_Co. For my Ubuntu 18.04, setting solarized_termcolors to 256 will give me a ugly unusable colorscheme.

