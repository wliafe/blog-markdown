# Tex Live下载与安装

## 下载

[官网下载](https://www.tug.org/texlive/acquire-netinstall.html)

[清华镜像](https://mirrors.tuna.tsinghua.edu.cn/CTAN/systems/texlive/Images/)

官网速度特别慢，建议使用清华镜像。

# VS Code配置LaTeX

安装latex-workshop插件

修改设置auto Clean为onBuild

在recipes设置中的json文件中添加下面这段。

```json
{
    "name": "pdflatex",
    "tools": [
        "pdflatex"
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