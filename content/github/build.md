本节来在本地把我们的笔记编译成静态页面，未来方便托管到 github pages 静态网页服务之上。

### 修改文件夹结构

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

### 进行编译

只需要添加如下脚本：

```json
"scripts": {
 "build": "gitbook build ./content ./gh-pages"
},
```

然后命令行中运行

```
npm run build
```

即可。
