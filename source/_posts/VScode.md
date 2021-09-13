---
title: VScode Configuration and Insturctions
top: false
cover: false
toc: true
mathjax: true
date: 2021-08-20 11:34:38
password:
summary:
tags:
- ReadMe
categories: ReadMe
---

VScode 使用记录
https://code.visualstudio.com/docs/languages/json


## SSH 
应用: Remote SSH  
host 不需要加端口  

## markdown 
You can also right-click on the editor Tab and select Open Preview (Ctrl+Shift+V) or use the Command Palette (Ctrl+Shift+P) to run the Markdown: Open Preview to the Side command (Ctrl+K V)

## Json/html
Shift+Alt+F formatting

## Setting sync
步骤一：安装Settings Sync扩展
启动VSCode，搜索并安装Settings Sync扩展：

上传配置
按下 Shift + Alt + U

下载配置
按下 Shift + Alt + D

提示：如果上传配置成功，将会有消息显示在输出选项卡中。

按照如上步骤在新环境中配置Settings Sync扩展，然后按下Shift + Alt + D下载配置。

## MikTex latex
修改 “更新-> 检索源” 为随机宏  

## Sumatra PDF
修改vscode setting.json file SumatraPDF 路径  
### 正反向搜索
1. 配置反向搜索（PDF->Latex源文件） 
2. 反向搜索在SumatraPDF中设置。打开SumatraPDF，进入设置->选项 对话框，在“设置反向搜索命令行”处填入如下内容(是一行内容，不是2行！)：  
3. "C:\Users\Administrator\AppData\Local\Programs\Microsoft VS Code\Code.exe" "C:\Users\Administrator\AppData\Local\Programs\Microsoft VS Code\resources\app\out\cli.js" -r -g "%f:%l"    
4. 双击PDF中的任意一处即可跳转到VSCode中所对应的内容的源代码处  
5. 反向搜索：打开一个已经编译的TeX文件，ctrl+alt+v打开PDF文件，在正文中双击鼠标左键，会切换到了源文件的相应位置。  
6. 正向搜索：ctrl+alt+x，找到"navigator,select and edit"，点击第一项"syncTeX from cursor"(快捷键ctrl+alt+j)，会切换到PDF文件的相应位置。  

如果不成功，检查路径设置，或者文件名错误。 

