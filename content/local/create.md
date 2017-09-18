
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


视频：gitbook-1-intro
