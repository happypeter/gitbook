### 第一部分：简介

- 功能强大
  - 自动实现搜索，翻页等功能
- 上手容易
  - 用 Markdown 书写即可

视频：gitbook-1-intro

### 第二部分：markdown 语法简介

- Markdown 是程序员写文档的标准语法
- 参考文档：https://coding.net/help/doc/project/markdown.html



### 用 Markdown 来记笔记

Markdown 跟 HTML 一样，是一种标签语言。但是 Markdown 语法特别简单，适合用来做笔记。


- [Markdown 语法参考](https://coding.net/help/doc/project/markdown.html)

Mardown 语法不是浏览器能直接支持的，所以需要先把 Mardown 语法写成的内容，编译成
HTML ，才能美观的显示出来。

那么 Github 就提供了这个编译环境。


例如，我们在 README.md 中填写

```
[百度](http://baidu.com)

<a href="http://baidu.com">百度</a>
```

提交保存之后，页面显示出完全一样的链接效果。

> 注意，添加内容的文件名，无所谓，但是后缀一定要 .md 不然无法编译成功


### Mardown 中添加语法高亮


什么是语法高亮？ 如果一段代码没有语法高亮，那么就是所有的字符都显示成一个颜色。但是通常编辑器中有语法高亮，也就是不同语法作用的字符串会显示成不同的颜色。

markdown 中，如果写成下面这样，最终显示的效果就是有语法高亮的：

    ```js
    console.log('hello');
    console.log('hello');

    console.log('hello');

    console.log('hello');
    ```

    ```css
    body {
      background: red;
    }
    ```

上面的内容会最终显示为：


```js
console.log('hello');
console.log('hello');

console.log('hello');

console.log('hello');
```

```css
body {
  background: red;
}
```

视频：gitbook-2-markdown


### p3: 安装 Gitbook 并创建笔记

根据[官网说明](https://github.com/GitbookIO/gitbook/blob/master/docs/setup.md) 第一步，先安装

```
npm install gitbook-cli -g
```


然后，创建一个笔记文件夹

```
mkdir my-note
```

然后执行

```
cd my-note
gitbook init
```

这样，可以生成两个文件

- README.md 的内容会显示在书皮上
- SUMMARY.md 是目录

启动服务器，查看和编辑书籍

```
gitbook serve
```

这样，可以启动一个服务器，然后到 localhost:4000 端口，就可以看到这本书了。

视频：gitbook-3-create

### p4: 修改笔记

可以修改 SUMMARY.md 来添加书籍目录

```
# Summary

- [Introduction](README.md)
- [第一章：redux](./redux/index.md)
  - [第一节：state 复习](./redux/1-state.md)
  - [第二节：你好 redux](./redux/2-hello-redux.md)
```

下一步，创建笔记文件，atom 到 redux 文件夹中创建 1-state.md 和 2-hello-redux.md 文件。

视频：gitbook4-change
