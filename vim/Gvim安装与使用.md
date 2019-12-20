# Gvim安装与配置

## 隐藏菜单栏（win10系统下）

找到安装路径下的_vimrc文件。C:\Program Files (x86)\Vim

```
"Toggle Menu and Toolbar
set guioptions-=m
set guioptions-=T
map <silent> <F2> :if &guioptions =~# 'T' <Bar>
        \set guioptions-=T <Bar>
        \set guioptions-=m <bar>
    \else <Bar>
        \set guioptions+=T <Bar>
        \set guioptions+=m <Bar>
    \endif<CR>
```

现在按f2就可以方便的隐藏与显示菜单栏了。

## 插件的安装与使用

### 安装vim-plug

下载文件plug.vim到autoload文件夹下面

```
curl -fLo vim安装路径/autoload/plug.vim https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

 编辑.vimrc文件 

```
call plug#begin('~/.vim/plugged')
Plug 'beanworks/vim-phpfmt' #添加要安装的插件
call plug#end()
```

把想要的插件放进去。



## 主题安装

首先可以通过vim-plug安装插件，例如安装gruvbox主题。打开.vimrc文件做如下的修改：

```shell
call plug#begin('~/.vim/plugged')
Plug 'morhetz/gruvbox' "配色方案gruvbox
call plug#end()
```

添加要下载的文件。之后打开vim进入到vim-plug安装：

```vim
:PlugInstall
```

现在此主题已经安装好了，再打开.vimrc配置文件，添加以下语句：

```shll
"设置vim主题
colorscheme gruvbox
set background=dark
```

从新启动vim编辑器，这个时候就可以看到是新的主题了。

## 字体的修改

 编辑.vimrc文件 ，添加

```
"设置字体和大小
set guifont=Consolas:h14
```



## 乱码问题的解决

 编辑.vimrc文件 ，添加

```
"解决中文乱码
set fileencodings=utf-8
set termencoding=utf-8
set encoding=utf-8

"解决菜单乱码  
source $VIMRUNTIME/delmenu.vim  
source $VIMRUNTIME/menu.vim  
```

请参考： https://blog.csdn.net/haohaojian/article/details/50178691 

## vim leader键

 `leader` 键简单的说就是一个前缀键，可以自由设定，比如 spacemacs 的 leader 键就是空格键。 

```shell
" 设置 leader 键，例子为空号键，也可以设置为其他的 默认为"/"
let mapleader=" "
 
" 设置快捷键，关闭一个窗口
map <leader>wq :wq<CR>
```

这个例子中，在 [vim](https://mounui.com/tag/vim/) 中，在 normal-mode 下，按空格键+w+q 就可以保存文件退出窗口。
		基本上，合理地利用 leader 键，写代码的时候就可以在主键盘里完成大部分功能而且不用频繁地使用 ctrl 、 alt 等键。