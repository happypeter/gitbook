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

### 托管我的 gitbook

为了部署方便，我们把我们的 my-note 的内容结构稍微调整一下，把原有的所有的笔记都放到 content 文件夹中，也就是有这样的目录结构

```
cd my-note
cd content
ls
README.md  SUMMARY.md redux
```

为何要把内容都统一放到 content 文件夹呢？答案就是，托管到 github 上的内容，其实是一个**编译后** 的内容，而不是原始内容。现在我们把原始内容都放到 content 文件夹中，未来会把编译输出内容放到 my-note/gh-pages 文件夹中。

### 添加自动化脚本

上面的操作之后，如果我们再去运行：

```
gitbook serve
```

就会报错，因为文件找不着了。需要把命令改一下

```
gitbook serve ./content ./gh-pages
```

这样，我们就又可以启动成功了，同时，也会自动创建 gh-pages 文件夹，文件夹中的内容，就是编译后的输出。

每次启动的时候，都要敲长长的命令，很不方便，所以，我们就需要把命名简短化，具体就是去写成 **npm 脚本**。具体步骤如下：

第一步，把项目变成一个 nodejs 的项目：

```
cd my-note
npm init -y
```

然后，package.json 中添加这些代码：

```json
"scripts": {
 "start": "gitbook serve ./content ./gh-pages"
},
```

有了上面的 npm 脚本之后，我们如果我想在本地 4000 端口查看本书，只需要运行

```
npm start
```

就可以成功预览了。

注意，此时多个一个文件夹 gh-pages，这个文件夹中的内容，也不是我们自己写的，所以到 .gitignore 文件里面添加

```
gh-pages
```

然后再进行 git 做版本的操作。

### 部署书籍到 gh-pages

这一步，可以手动做：

- 第一步：编译项目，来把 md 文件翻译成 html 放到 gh-pages 文件夹
- 第二步，拷贝 gh-pages 中的所有文件，到本仓库的 gh-pages 分支，然后上传
- 第三步，以后每次修改完都需要拷贝到 gh-pages 分支，很麻烦

所以，我们采用一个 npm 包，来帮助我们完成上面的操作

```
cd my-note/
npm i --save gh-pages
```

然后创建 my-note/scripts/deploy-gh-pages.js

里面的内容是：

```
'use strict';

var ghpages = require('gh-pages');

main();

function main() {
    ghpages.publish('./gh-pages', console.error.bind(console));
}
```

上面的脚本的作用，就是把当前文件夹下的 gh-pages 文件夹中的所有内容，push 到本仓库的 gh-pages 分支。

然后添加一个 npm 脚本 `deploy` （ deploy 就是部署的意思），如下：

```json
"scripts": {
 "start": "gitbook serve ./content ./gh-pages",
 "deploy": "node ./scripts/deploy-gh-pages.js",
},
```

那么，可以来试试，保证 `npm start` 处于运行中的状态，然后运行

```
npm run deploy
```

注：如果最后返回 `undefined` 字样，表示没有出现错误，部署成功。

就可以把编译后的书稿 push 到远端仓库的 gh-pages 分支了。也就是可以到 https://happypeter.github.io/my-note 这个链接，看到书了。

这样，大功告成。
