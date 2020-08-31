# chapter1 latex安装与环境配置
## 1. 编辑器
我选择了vscode作为编辑工具，一方面它的暗色界面比较酷(....)，另一方面它有代码高亮，多行编辑等功能。vscode在官方网站https://code.visualstudio.com/ 上可以方便地下载到。
下载后安装一些latex常用的扩展包。
## 2. latex编译器
https://miktex.en.softonic.com/ 我用的时miktex。正常安装之后检查miktex会在环境变量的Path中添加路径，vscode无需再手动配置路径。
## 3. 更改/检查配置
在latex编辑界面按快捷键ctrl+shift+p调出搜索框，在框中输入setting.json打开配置文件。检查是否有如下配置：
```
{
    "editor.wordWrap": "on",
    "workbench.startupEditor": "newUntitledFile",
    "latex-workshop.latex.clean.fileTypes": [
        "*.aux",
        "*.bbl",
        "*.blg",
        "*.idx",
        "*.ind",
        "*.lof",
        "*.lot",
        "*.out",
        "*.toc",
        "*.acn",
        "*.acr",
        "*.alg",
        "*.glg",
        "*.glo",
        "*.gls",
        "*.ist",
        "*.fls",
        "*.log",
        "*.fdb_latexmk",
        "*.gz"
    ],
    "latex-workshop.view.pdf.viewer": "tab",
    "latex-workshop.latex.recipes": [
 {
            "name": "xelatex",
            "tools": [
              "xelatex",
              "xelatex"
            ]
          },
        {
            "name": "xelatexb",
            "tools": [
              "xelatex",
              "bibtex",
              "xelatex",
              "xelatex"
            ]
          },
        {
          "name": "latexmk",
          "tools": [
            "latexmk"
          ]
        },
        {
          "name": "pdflatex -> bibtex -> pdflatex*2",
          "tools": [
            "pdflatex",
            "bibtex",
            "pdflatex",
            "pdflatex"
          ]
        }
      ],
      "latex-workshop.latex.tools": [
        {
            "name": "xelatex",
            "command": "xelatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOC%"
            ]
        },
        {
          "name": "latexmk",
          "command": "latexmk",
          "args": [
            "-synctex=1",
            "-interaction=nonstopmode",
            "-file-line-error",
            "-pdf",
            "%DOC%"
          ]
        },
        {
          "name": "pdflatex",
          "command": "pdflatex",
          "args": [
            "-synctex=1",
            "-interaction=nonstopmode",
            "-file-line-error",
            "%DOC%"
          ]
        },
        {
          "name": "bibtex",
          "command": "bibtex",
          "args": [
            "%DOCFILE%"
          ]
        }
    ],
    "latex-workshop.latex.autoClean.run": "onBuilt",
    "editor.suggestSelection": "first",
    "vsintellicode.modify.editor.suggestSelection": "automaticallyOverrodeDefaultValue",
    "files.exclude": {
      "**/.classpath": true,
      "**/.project": true,
      "**/.settings": true,
      "**/.factorypath": true
    }
}
```
## 编译和预览
正常来说，ctrl+w保存后，编译器会用xelatex编译一遍。但这样是显示不了参考文献的。需要手动点击最左边选项栏的最下面TEX符号，再选择Command->Build Latex Project->Recipe:xelatexb进行完整的编译。
快捷键ctrl+alt+v可以预览编译结果。
