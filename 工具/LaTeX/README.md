# Tex Live下载与安装

[清华镜像CTAN文档](https://mirrors.tuna.tsinghua.edu.cn/help/CTAN/)

## 下载

[官网下载](https://www.tug.org/texlive/acquire-netinstall.html)

[清华镜像](https://mirrors.tuna.tsinghua.edu.cn/CTAN/systems/texlive/Images/)

官网速度特别慢，建议使用清华镜像。

# VS Code配置LaTeX

安装latex-workshop插件

修改设置auto Clean为onBuild

在recipes设置中的json文件下面这段作为第一段。

```json
{
    "name": "latexmk (lualatex)",
    "tools": [
        "lualatexmk"
    ]
},       
```

# Tex Live tlmgr管理器

## 管理器更新(使用清华镜像源)

```bash
tlmgr update --self --repository https://mirrors.tuna.tsinghua.edu.cn/CTAN/systems/texlive/tlnet
```

## 宏包更新(使用清华镜像源)

```bash
tlmgr update --all --repository https://mirrors.tuna.tsinghua.edu.cn/CTAN/systems/texlive/tlnet
```

# LaTeX学习与使用

[LaTeX教程](https://www.latexstudio.net/LearnLaTeX/)

## LaTeX常用宏包

ctex：中文格式宏包

geometry：页面设置宏包

titlesec：标题设置宏包

amsmath：数学公式宏包