---
title: Markdown风格指南
description: 我们在使用Markdown撰写文档的时候，除了熟练使用Markdown提供的标记语法之外，清晰的文档风格也很重要。本文试图探索一种良好的markdown风格，希望能够帮助你构建一篇排版清晰，结构分明的Markdown文章。
---
我们在使用Markdown撰写文档的时候，除了熟练使用Markdown提供的标记语法之外，清晰的文档风格也很重要。本文试图探索一种良好的markdown风格，希望能够帮助你构建一篇排版清晰，结构分明的Markdown文章。<!-- more --> 

## 文档布局

### 文档布局要素

通常，大多数文档都具有以下格式:

```markdown
# 文档名称

简短说明

目录

## 主题

内容 

## 参考资料

* https://link-to-more-info
```

### 文档布局风格说明

1. **文档名称**,建议使用一级标题，并且一级标题尽量和文件名一致。

2. **作者名**,可选的， 如果你要声明文档的所有权，请将其放在文档名称和简短说明之间。

3. **简短说明**，使用简短的文字(1-3个句子就够啦)，表达文档的中心思想。

4. **目录**,可选的，如果文档内容比较多，加上目录，可以让读者快速了解文章层次。建议使用`[标题](#标题)`的格式。因为它还可以让我们从目录跳转到标题所在位置。方便读者有选择性的阅读(回顾或对比)。模板如下:

   ```
   目录:
   1.  [Document layout](#document-layout)
   2.  [Character line limit](#character-line-limit)
   3.  [Trailing whitespace](#trailing-whitespace)
   4.  [Headings](#headings)
       1.  [ATX-style headings](#atx-style-headings)
       2.  [Add spacing to headings](#add-spacing-to-headings)
   5.  [Lists](#lists)
       1.  [Use lazy numbering for long lists](#use-lazy-numbering-for-long-lists)
       2.  [Nested list spacing](#nested-list-spacing)
   6.  [Code](#code)
       1.  [Inline](#inline)
       2.  [Codeblocks](#codeblocks)
       3.  [Declare the language](#declare-the-language)
       4.  [Escape newlines](#escape-newlines)
       5.  [Nest codeblocks within lists](#nest-codeblocks-within-lists)
   7.  [Links](#links)
       1.  [Use informative Markdown link titles](#use-informative-markdown-link-titles)
   8.  [Images](#images)
   9.  [Prefer lists to tables](#prefer-lists-to-tables)
   10. [Strongly prefer Markdown to HTML](#strongly-prefer-markdown-to-html)
   ```

5. **主题**，除文档名称外的标题，请从二级标题开始排版，二级标题的直接子标题应该是三级标题，三级标题直接子标题为四级子标题……以此类推嵌套，尽量避免跨级。

6. **参考资料**，可以将引用的文章，参考的资料等链接放在底部，并且用二级标题。供想要了解更多或未找到所需内容的读者使用。

## 标题

### ATX-style标题

建议使用1-6个`#`，对应标题1到6阶标题。

```
# H1
## H2
......
```

### 标题间距

在标题前后添加换行符以增加间距。

```
...text before

# H1

....text after
```

Note:有的Markdown编辑器(typora)，会自动在标题前后添加空行，在非源码模式下编辑的时候，就不需要再添加空行了，否则变成了标签前后各空两行。

## 内容

### 记忆中的差别

回忆上学那会儿，我们写作文是这样子的:

```
[空两格]xxxxxxxxxxxxxx......
xxxxxxxxxxxxxxxxxxxxxx。
[空两格]xxxxxxxxxxxxxx......
xxxxxxxxxxxxxxxxxxxxxx。
```

Markdown写文档建议从最左边开始写起，而且段落之间使用空行隔开。

```
xxxxxxxxxxxxxx......
xxxxxxxxxxxxxxxxxxxxxx。

xxxxxxxxxxxxxx......
xxxxxxxxxxxxxxxxxxxxxx。
```

## 嵌套列表

### 嵌套列表间距

嵌套列表，应该保持父节点的文本起始位置和子节点起始位置在一条垂直线上。

```
1. xxx......
   1. xxx......
```



## 代码

### 行内代码块

行内代码块，一般用于短代码(不超过一行)和字段名称。

### 代码块

代码块一般用于长超过一行的代码。

#### 声明语言

建议明确的声明语言,以便语法高亮显示。

#### 缩进的代码块有时候更清晰

建议在编写简短的片段时，使用缩进:

```markdown
你需要运行:
    hexo clean
然后:
    hexo g
再次:
    hexo d
```

#### 逃避换行

对于大多数命令行片段，最好不要使用任何换行符，在行尾添加一个反斜杠,否则从Markdown赋值到终端界面中，会将第一行的命令行片段当做整体执行。

```markdown
bazel run :target -- --flag --foo=longlonglonglonglongvalue \
--bar=anotherlonglonglonglonglonglonglonglonglonglongvalue
```

### 链接

建议尽量使用意思明确的短语来包装链接，而不是使用无意义的"此处"，"链接"。反例:

```
有关详细信息，请参阅语法指南：[ link ]（syntax_guide.md）。
或者，查看样式指南[ 此处 ]（style_guide.md）。
不要这样做。
```

正确的例子:

```
有关详细信息，请参阅[ 语法指南 ]（syntax_guide.md）。
或者，查看[ 样式指南 ]（style_guide.md）。
```

## 表格

表格适用于装载文字简短的句子,这样容易阅读。例如:

```markdown
| Transport        | Favored by     | Advantages                    |
| ---------------- | -------------- | ----------------------------- |
| Swallow          | Coconuts       | Otherwise unladen             |
| Bicycle          | Miss Gulch     | Weatherproof                  |
| X-34 landspeeder | Whiny farmboys | Cheap since the X-38 came out |
```

如果要使用表格去容纳比较长的文字，建议使用列表和副标题来代替去呈现相同的信息，并且以后方便修改。如果用表格去呈现长的文字，可能是这样子的:

```markdown
| Fruit | Attribute | Notes |
| ----- | --------- | ----- ||
| Apple  | [Juicy](https://example.com/SomeReallyReallyReallyReallyReallyReallyReallyReallyLongQuery), Firm, Sweet               | Apples keep doctors away.                             |
| Banana | [Convenient](https://example.com/SomeDifferentReallyReallyReallyReallyReallyReallyReallyReallyLongQuery), Soft, Sweet | Contrary to popular belief, most apes prefer mangoes. |
```

下面是使用列表和副标题来呈现:

```markdown
## Fruits

### Apple

* [Juicy](https://SomeReallyReallyReallyReallyReallyReallyReallyReallyReallyReallyReallyReallyReallyReallyReallyReallyLongURL)
* Firm
* Sweet

Apples keep doctors away.

### Banana

* [Convenient](https://example.com/SomeDifferentReallyReallyReallyReallyReallyReallyReallyReallyLongQuery)
* Soft
* Sweet

Contrary to popular belief, most apes prefer mangoes.
```



## 参考资料

[Markdown style guide](https://github.com/google/styleguide/blob/gh-pages/docguide/style.md)