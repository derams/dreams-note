# 如何用 Github 来做笔记？

首先，第一步，先安装 gitbook 包
```
npm install gitbook-cli -g
```
然后，创建一个文件夹，就是自己记载笔记的文件夹
```
mkdir my-note
```
然后执行
```
cd my-note
gitbook init
```
这样就可以生成两个文件
```
README.md的内容会显示在书皮上边
SUMMARY.md是目录
```
####启动服务器，查看和编辑书籍
```
gitbook serve
```
这样就可以启动一个服务器，然后到localhost：4000端口，就可以看到这本书了。
通过修改SUMMARY.md来添加书籍目录
```
#Summary

* [Introduction](README.md)
* 第一章
* [第一章：redux](./redux/index.md)
    * [第一节：状态复习](./redux/1-state.md)
    * [第二节：引入redux](./redux/2-hello-state.md)
    * [第三节：git安装及使用](./redux/3-git.md)
```
创建 git 文件夹，然后里边就可以写笔记了。其实 gitbook 本身的使用技巧基本就是这些了。
####托管我的 gitbook
首先到 github.com 上创建 my-note 仓库。
为了部署方便，我们把我们的 my-note的内容稍微调整一下，把原有的所有的内容都放到 content 文件夹中， 也就是有这样的目的结构
```js
→ my-note ls content
README.md  SUMMARY.md git
➜  my-note
```
然后，把当前项目变成一个 note.js 的项目
```
cd my-note
npm init
```
然后，在 package.json 中添加这些代码
```js
"scripts": {
 "start": "gitbook serve ./content ./gh-pages",
 "build": "gitbook build ./content ./gh-pages",
 "deploy": "node ./scripts/deploy-gh-pages.js",
 "publish": "npm run build && npm run deploy",
 "port": "lsof -i :35729"
},
```
有了上边的npm脚本后，我们如果想在本地 4000 端口查看本书，我们需要运行
```
npm start
```
在准备上传之前，先来创建个一个 .gitgnoree 文件，里面填写
```
gh-pages
```
然后运行
```
git init
git add -A
git commit -a -m"hello my book"
git remote add origin git@github.com:happypeter/my-note.git
git push -u origin master
```
上面这些完成后，github 的原始代码就被安全备份到 master 分支了。访问 https://github.com/derams/derams-note 可以看到这些内容。
####部署书籍到 gh-pages
这一步，可以手动做：

第一步：运行 npm run build ，来把 md 文件翻译成 html 放到 gh-pages 文件夹
第二步，拷贝 gh-pages 中的所有文件，到本仓库的 gh-pages 分支，然后上传
第三步，以后每次修改完都需要拷贝到 gh-pages 分支，很麻烦
所以，我们采用一个 npm 包，来帮助我们完成上面的操作
```
cd my-note/
npm i --save gh-pages
```
然后创建 my-note/scripts/deploy-gh-pages.js

里面的内容是：
```js
'use strict';

var ghpages = require('gh-pages');

main();

function main() {
    ghpages.publish('./gh-pages', console.error.bind(console));
}
```
这样，每次书稿有了修改，运行
```
npm run publish
```
就可以把书稿部署到 http://happypeter.github.io/my-note
