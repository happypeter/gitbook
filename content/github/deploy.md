### 托管我的 gitbook




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
