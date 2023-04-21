# 西工大主题-学士论文LaTeX模板



## 1. 简介

本项目是是在西北工业大学本科毕业设计论文格式的要求下的一份 LaTeX 文档，该文档有如下特点：

* 使用XeLaTeX，方便字体设置。中文支持使用xeCJK包。
* 用pgf/tikz宏包画成矢量校徽。
* 自制nwpulogo矢量字体，即毛体的“西北工业大学”六个字。
* 已做好封面

使用者无需修改导言区文档类型，直接在发布版的基础上修改章节标题，撰写内容，即可完成毕业设计论文任务。

对本篇论文的master结构做以下介绍：

- **appendix**文件夹为附录部分，包含毕设小结，致谢以及附录（相关代码等）。
- **chapters**文件夹为论文主要章节，可直接修改应用。
- **figures**文件夹内包含本文所用到的图片(已注明应用章节及图片名称)。
- **fonts**文件夹内包含本文正常使用所需安装字体，具体方法见（**3.字体问题**）。
- **preface**文件夹包含本文的中，英文摘要。
- **manuals**文件夹中包含常用LaTeX数学符号及数学公式。
- **references**文件夹包含本文引用文献的**BibTeX**格式整理。
- **settings**文件夹包含论文封面（可直接修改）、封面设置页（无需改动）及论文主设置页。
- **example.tex**为论文主题，**example.pdf**为论文编辑中实时的pdf格式显示。

## 2. 使用方法

先安装texlive，可以在tuna网站下载（https://mirrors.tuna.tsinghua.edu.cn/CTAN/systems/texlive/Images/）。

安装说明：https://zhuanlan.zhihu.com/p/64555335

| TeXLive Environment                                          | Status |
| ------------------------------------------------------------ | ------ |
| ![TeXLive2016](https://img.shields.io/badge/TeXLive-2016-3D6117.svg) | ✔️      |
| ![TeXLive2017](https://img.shields.io/badge/TeXLive-2017-3D6117.svg) | ✔️      |
| ![TeXLive2018](https://img.shields.io/badge/TeXLive-2018-3D6117.svg) | ✔️      |
| ![TeXLive2019](https://img.shields.io/badge/TeXLive-2019-3D6117.svg) | ✔️      |
| ![TeXLive2020](https://img.shields.io/badge/TeXLive-2020-3D6117.svg) | ✔️      |

1. 直接对 `example.tex` 文件进行修改，对应的摘要、章节内容、附录文件均已经默认生成，在此基础上加以修改即可
2. 如有必要，也可以请仿照 `example.tex` 在 *导言区* 引用 `\input{settings/thesis-setting}` 来直接设置文档格式为本科毕业设计论文格式
3. 如有必要，修改 `makefile` 文件的 `MAIN` 选项为自己 `tex` 文档的文件名


## 3. 字体问题


* 本模板出于排版美观考虑，使用的是 **Adobe** 字体（宋体，黑体，楷体，仿宋）

* `nwpuname.ttf` 是校名“西北工业大学”的字体文件，该文件只包含这6个汉字

* 将 `fonts` 文件夹中的字体 `nwpuname.ttf`和**Adobe** 字体（宋体，黑体，楷体，仿宋）放到`fc-list`可以找到的地方。Linux下放到`~/.fonts`，Windows下放到`C:\windows\Fonts`，并选择“为所有用户安装”以确保字体文件正确安装。Linux下安装完成后执行：

      xelatex main.tex
      bibtex main.tex
      xelatex main.tex
      xelatex main.tex



## 4. 注意事项以及常见问题

* **`Makefile` 问题**
  * 本模板提供了简单的 `Makefile` 文件来控制编译流程
  * 这份 `makefile` 中的 `close`, `clean` 以及 `wipe` 选项为 `windows` 专用, 并且假设使用了 `Acrobat` 打开了当前 pdf 文件
* **预创建文件及部分格式符说明**
  * `settings/cover.tex` 为论文的封面页
  * `settings/translation-cover.tex` 为本科毕业设计的文献翻译封面页
  * `settings/logo.tex` 是通过 `tikz` 生成的校徽矢量图形 ，如果觉得不好看也可以去形象识别系统下载对应版本，并自行替换
  * 字体大小（size）的控制命令统一前缀为 `s`
  * 字体格式（font）的控制命令统一前缀为 `f`
* **其他可能的模板使用问题**
  * 在编译过程中，如果遇到卡在字体缓冲问题，请先关闭当前进程，并用管理员模式打开命令提示符（或终端），键入 `fc-cache -f -v` 强制刷新字体缓存即可

## 5. 更新修改

* **2020.07.06**
  * 将正文内容的行间距从原模板的1.0调整为提交标准要求的1.25。
  * 为符合提交标准，将原模板中的中、英文摘要及目录页从目录中删去。
  * 将design-conclusion和references的字体及行间距调整为与正文统一。
  * 通过添加空白页以满足打印纸质版内容时从右侧奇数页开始章节的要求。
* **2023.4.10**
  * 在teseis-setting里面的必要库支持部分，加入了如下内容：

\usepackage{xcolor}

\usepackage{textgreek} % textgreek宏包提供了一些大写和小写的非数学模式下使用的希腊字母命令，这些命令可以在正文中直接使用，并与正文字体相同大小。输入时候按如下例子：'''$\textkappa$'''关于该宏包中公式的说明补充了textgreek.pdf文件在manual文件夹中。

\definecolor{grey}{RGB}{128,128,128}%手动定义灰色,这样就保证了和word的页眉一样
  * 在thesis-setting.tex中插入了\usepackage{amsmath}库，在example.tex引言部分插入了\renewcommand{\theequation}{\thechapter-\arabic{equation}}%公式按章编号,并将编号设置为(1-1)这样的格式
  * 在添加插图与表格控制部分，使用

%\captionsetup[table]{labelfont=bf,textfont=bf}
\usepackage{setspace}
\usepackage{caption}

% 设置五号黑体字体
\setCJKfamilyfont{songti}{SimSun}
\newcommand*{\myheading}[1]{\multicolumn{1}{c}{\textbf{\heiti\fontsize{9pt}{12pt}\selectfont #1}}}

% 设置表格字体及行距
\renewcommand{\arraystretch}{1.5}
\setlength{\tabcolsep}{8pt}
\setstretch{1.2}

% 设置表格标题格式
\captionsetup[table]{textfont=bf,labelsep=space,labelformat=simple,font={small},skip=0ex}

调整了表格格式
