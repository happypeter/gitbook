### p5: 保存书稿到 github 仓库

首先到 github.com 上创建 my-note 仓库。

运行 gitbook serve 命令之后，生成临时文件夹 `_book` 这个不是我们写的，所以一定要放到 .gitignore 文件中，所以，我们就在 my-note 文件夹的顶级位置，创建 .gitignore 文件，内容如下

```
_book
node_modules
```

接下来我们想做的事情是：把书稿上传到 github.com/happypeter/my-note 这个仓库的 master 分支保存起来。具体步骤是：

```
cd my-note
git init
git add -A
git commit -m"msg"
git remote add origin git@github.com:happypeter/peter-note.git
git push -u origin master
```

最终达成的效果，就是访问 https://github.com/happypeter/my-note 就可以看到书的原稿了。

新系统会遇到 ssh key 相关的问题，这个可以参考本书对应的 github.com 章节。

视频：gitbook-5-push
