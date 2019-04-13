# ECNU-Undergraduate-LaTeX

### 华东师范大学本科生毕业论文模板

下载地址：[Link](https://github.com/YijunYuan/ECNU-Undergraduate-LaTeX/archive/master.zip)

本项目中`gb7714-2015.bbx`与`gb7714-2015.cbx`两个文件为[hushidong](https://github.com/hushidong)的所做满足GB/T7714-2015标准的[biblatex样式包](https://github.com/hushidong/biblatex-gb7714-2015)。

本模板提倡模块化的论文写作方式。所有tex文件，最终都会汇入到`main.tex`中进行编译。

### 各文件作用

#### `main.tex`

本模板的核心，控制着整个项目的结构。在这个文件中，你需要修改的只有文章正文的各个section所在的tex文件（在演示中，它们是`SectionA.tex`，...，`SectionE.tex`），它们被建议放置在`~/body/`中。当然，你可以随意地修改这些文件的名字和内容并进行删减与增补。语法可见本文件中的示例。

#### `packages_and_settings.tex`

这个文件用来载入宏包并进行各种格式设置。简而言之，请不要轻易修改，删除本文件中的任何内容，特别是不要修改宏包的加载顺序，除非你真的知道你在做什么。这真的非常重要！！！！！！！

总的来说，你唯一可能需要添加的是某些类似于定理的环境。本模板中已有了定理，引理，命题，解，证明等环境及对应的无编号环境。如果你要添加新的环境，可以模仿本文件中已有的做法。不过我们更希望把你的需求放到issue里。

#### `paper_info.tex`

本文件中定义了各种论文的基本信息，如作者名称，完成日期，中英文关键词等，需要你自己填写修改。

文件内容是不言自明的，相信你看了内容与注释就知道怎么弄了。

#### `~\preface\inner-cover.tex`

这个文件定义了内封面，请勿进行任何修改，除非你真的知道你在做什么。

#### `~\preface\abstract-CHS.tex, ~\preface\abstract-ENG.tex`

这个文件定义了中英文的摘要（事实上还有关键词，只是关键词已经在`paper_info.tex`中填写所以在这个文件中会自动调用，你就不用管了），内容同样是不言自明的，相信你看了内容就知道怎么弄了。

另外特别提醒：请不要添加额外的空行，否则关键词的显示可能会出现一定异常。

#### `~\body\SectionXXX.tex`

正如前文所提到的，这些文件定义了正文部分。这里我们按照Section进行文件分割并在`main.tex`中统一input以便管理。

这些文件包括了各种格式要求中提到的usecase和一些注意事项。我们不想对这部分作过多的解释，因为通过对比`main.pdf`与这部分源代码并不困难，而且正文中已经进行了部分解释。

#### `~\ending\Acknowledgement.tex`

这个文件定义了致谢的内容，请自行修改填写。

#### `~\ending\Appendix.tex`

这个文件定义了各个附件。需要指出的是，每个附件必须以`\apdx{title}`作为开头，其中`title`为该附件的标题。

另外，每个附件都是单独成页的。

#### `~\figures\logo.png`

封面使用的图片，请勿修改或删除。

#### `~\figures\inner-cover(contains_font).eps`

内封面图，请勿修改或删除。

#### `~\figures\figure_example1.jpg`

用来演示插入图片所使用的样例图片，使用方法请见`~\body\SectionD.tex`。

#### `~\reference\thesis-ref.bib`

存放了所有的参考文献条码。虽然本模板使用的biblatex系统可以处理多bib文件，但我们依然建议你把所有条目都放在这个文件中。

如果你真的需要使用另外的bib文件，请自行修改`main.tex`的第4行。

#### `gb7714-2015.bbx, gb7714-2015.cbx`

这两个文件是[hushidong](https://github.com/hushidong)的所做满足GB/T7714-2015标准的[biblatex样式包](https://github.com/hushidong/biblatex-gb7714-2015)，一般情况下你不需要也不应该对这两个文件进行任何操作。在此一起打包发布是为了方便模板使用者，感谢hushidong的作品。

### 使用方法与编译环境

我们强烈推荐使用VSCode+latexworkshop插件进行论文编写。main.tex中已经为其写好了Magic Macro（也就是开头三行），使用时仅需Ctrl+S即可，十分方便。

本模板在texlive 2018环境中编译通过，别的环境请自行测试。一般情况下不支持（也从不准备支持）CTex套装。

本模板使用了biblatex来进行文献管理，且使用了biber作为后端。如果需要完整编译一次，你需要依次进行以下操作：

```
xelatex main.tex
biber main.bcf
xelatex main.tex
xelatex main.tex
```

是的没错，xelatex指令一共要执行三次。最后的产物就是`main.pdf`。

### 打印模式（新！）

由于最后打印纸质版论文需要调整单面/双面等事项，比较麻烦，所以本模板提供了一个非常易用的开关来控制是否需要启动打印模式。

具体地说，在`main.tex`的第五行有一条命令`\def \PrintMode{} `，默认情况下是打开的，此时产生的pdf文件里会有一些空页，且奇数页与偶数页的layout是相反的，这样在打印时只要在打印机上选择双面打印即可获得满足纸质版要求的论文，不用再做其他调整，非常方便。

当然在使用电子版论文时，这样的空页与layout的调整是没有必要的。此时我们只要将这行命令注释以后重新编译即可。

### 尾注与附录

在`main.tex`中的第49与58行有命令`\theendnotes`与`\makeapdx`，分别用于控制尾注与附录的生成。如果你没有尾注或附注，请将对应的命令删除。

### 其他

相信使用这份模板的人并不都精通TeX系统，甚至连作者自己也算不上精通，所以有些问题也需要慢慢摸索修改。

总之欢迎开issue。但我们不接受如下issue：

* 我什么都不改，就编译失败了（作者回答：请检查你的toolchain并仔细阅读本README.md）
* 所有本README.md中已经提到的问题。

### 维护者：

* 袁轶君（Yijun Yuan）

