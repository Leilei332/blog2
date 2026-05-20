---
title: Spacevim配置
published: 2022-04-27
updated: 2022-04-29
tags: 
- 日志
- Vim
- 软件
- 编程
---


在Windows上试了一下Spacevim，装了coc自动补全插件后感觉还行，代码分析和Visual Studio Code一样快。

!! 安装
首先安装vim，再安装Spacevim配置文件。官网提供了自动安装脚本，可以自动为Vim和Neovim安装。

Debian安装方法：

```sh
sudo apt install vim vim-gtk3
```
安装完成后打开GVim，还会装一些插件，等待安装完成即可。

!! 配置
默认Spacevim没有代码补全功能，所以要进行配置。在`~/.SpaceVim.d/init.toml`的`[options]`里加入：

```toml
autocomplete_method = 'coc'
```
然后在下面加入：

```toml
[[layers]]
name = "lang#python"

[[layers]]
name = "lsp"
```
重启，Spacevim会自动安装一些插件，安装完成后重启，输入`:CocInstall coc-pyright`安装自动补全。

完成后重启，就可以在Python里面使用自动补全和语法检查功能了。

!! 外观
Spacevim默认使用SourceCodePro Nerd字体，可以在配置文件里改，在`[options]`加入`guifont="Sarasa Fixed SC:h14"`即可。目前不知道为什么在Linux下不生效。

配色也是可以改的，默认是`gruvbox`，这里建议改成`SpaceVim`配色。

!! 配置vimtex
vim可以配置vimtex插件来编写$$\LaTeX$$文档。首先要安装[[SumatraPDF|https://www.sumatrapdfreader.org/free-pdf-reader]]，然后在`init.toml`加入：

```toml
[[custom_plugins]]
name = 'lervag/vimtex'
```
打开Vim，等待插件安装完成，打开`init.vim`，加入：

```vim
let g:tex_flavor = 'latex'
let g:vimtex_quickfix_mode = 0
let g:vimtex_view_general_viewer = 'SumatraPDF'
let g:vimtex_view_general_options
\ = '-reuse-instance -forward-search @tex @line @pdf'
let g:vimtex_view_general_options_latexmk = '-reuse-instance'
```
重启，输入命令`:CocInstall coc-vimtex`安装补全插件。

打开一个tex文件，长按<<.kbd \>>再按两下<<.kbd L>>，vimtex就可以自动编译为PDF，每次保存PDF都会更新，要停止重复刚才操作就行了。

!! 参考
* [[使用 Neovim 和 vimtex 高效撰写 LaTeX 学术论文 |https://sspai.com/post/64080]]