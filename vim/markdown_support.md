###vim增加markdown支持及实时预览
---
## 1. 语法高亮支持  
首先需要安装插件: [https://github.com/plasticboy/vim-markdown](https://github.com/plasticboy/vim-markdown), 如果用得pathogen,可以用下面得命令安装  

     cd ~/.vim/bundle  
     git clone https://github.com/plasticboy/vim-markdown  

## 2. 安装chrome的 markdown-preview 插件  
github 地址: [https://github.com/volca/markdown-preview](https://github.com/volca/markdown-preview)  
安装方法:   

- 先clone代码  
- setting->Extensions 勾选 Developer mode, 点击Load unpacked extension, 选中clone的代码文件夹  

## 3. 设置md文件默认打开程序为chrome(根据操作系统不同进行相应的设置)

随便编辑一个md文件，然后在vim command model下执行`!open %` 就会用默认的浏览器打开  
## 4. markdown syntax     
[http://wowubuntu.com/markdown/](http://wowubuntu.com/markdown/)  

参考资料:  

- [http://www.ooso.net/archives/611](http://www.ooso.net/archives/611)   
