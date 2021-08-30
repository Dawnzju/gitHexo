---
title: vimplus
top: false
cover: false
toc: true
mathjax: true
date: 2021-03-20 11:34:38
password:
summary:
tags:
- ReadMe
categories: ReadMe
---
Vimplus An automatic configuration program for vim  
Source https://github.com/chxuan/vimplus


## Install

>git clone https://github.com/Dawnzju/vim_dawnzju ~/.vimplus  
>cd ~/.vimplus  
>./install.sh //不加sudo  

## Configuration

- ~/.vimrc为vimplus的默认配置，一般不做修改  
- ~/.vimrc.custom.plugins为用户自定义插件列表，用户增加、卸载插件请修改该文件  
- ~/.vimrc.custom.config为用户自定义配置文件，一般性配置请放入该文件，可覆盖~/.vimrc里的配置  

## 
| 功能              | 快捷键               | 具体实现                        | 鼠标操作 |
|-----------------|-------------------|-----------------------------|------|
| 打开/关闭代码资源管理器    | <leader>n         |                             |      |
| Json格式整理        | <leader>j         | :%!python =-m json.tool<cr> |      |
| 打开term          | <leader>m         | :term<cr>                   |      |
| nmap            | <c-s>             | :w<cr>                      |      |
| vmap            | <C-S>             | <C-C>:update<CR>            |      |
| imap            | <C-S>             | <C-O>:update<CR>            |      |
| 开启鼠标            | mm                | :set mouse=a<cr>            |      |
| 关闭鼠标            | mmm               | :set mouse-=a<cr>           |      |
| 光标下移            | <c-j>             | <c-w>j                      |      |
| 光标右移            | <c-k>             | <c-w>k                      |      |
| 光标左移            | <c-h>             | <c-w>h                      |      |
| 光标上移            | <c-l>             | <c-w>l                      |      |
| 关闭              | Ctrl+W c          |                             |      |
| 横向切分窗口并打开文件     |                   | :sp <filename>              |      |
| 竖向切分窗口并打开文件     | <leader>x         | :vsp <filename>             |      |
| 上下分屏当前文件        | Ctrl+W s          |                             |      |
| 左右分屏当前文件        | Ctrl+W v          |                             |      |
|  复制当前选中到系统剪切板   | <leader><leader>y | :=+y                        | 复制 y |
|  将系统剪切板内容粘贴到vim | <leader><leader>p | :=+p                        | 中键   |
| 上一个             | n                 |                             |      |
| 下一个             | N                 |                             |      |
| 另存为             | :w 文件名            |                             |      |
| :tabe           | 在新标签页中编辑          |                             |      |
| :tabc           | 关闭当前标签页           |                             |      |
| ctrl s之后        | ctrl q            |                             |      |

