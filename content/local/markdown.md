
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
