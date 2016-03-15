#GitHub + Hexo 创建自己的静态博客

## 一、创建GitHub项目
1. 到`https://github.com`创建一个自己的账号；
2. 创建一个用于放置Blog内容的Repository(代码仓库)，Repository名为 `<username>.github.io`；
3. 在本地新建一个文件夹，并把创建好的Repository Clone到本地目录下；
4. CD到项目的根目录下，创建一个测试用的html文件：`printf "<h1>Testing page<h1> It works.\n" > index.html`
5. push到master分支，然后再浏览器中浏览测试的网页 `<username>.github.io`，如果出现刚才新建的页面就说明成功了；
6. 清空刚才的测试文件：
```
git rm -rf .
git commit -a -m "modify"
git push origin master
```

## 二、安装Hexo
1. 检查有没有安装npm，`npm -v`，如果出现版本信息的话，就OK
2. 检查有没有port，`port -v`，如果出现了版本信息的话，就OK
3. 去`http://www.macports.org/`下载安装Mac版的MacPort
4. 重启终端，使用`port -v`查看port的版本是否可用。如果出现版本信息的话，就OK。
5. 使用`sudo port -d sync`来更新MacPort套件，可能会出现一堆sources.conf的错误，解决方法是修改`/opt/local/etc/macports/sources.conf`文件的最后几行
```
//rsync://rsync.macports.org/release/tarballs/ports.tar [default]
#rsync://rsync.macports.org/release/ports/ [default]
http://www.macports.org/files/ports.tar.gz [default]
```
6. 使用`sudo port install -g npm`就能安装npm套件及NodeJS相关组件
## 三、使用Hexo创建、管理Blog
1. 新建一个文件夹`mkdir hexoBlog`
2. 创建一个hexo Blog `hexo init`进行初始化
3. `hexo server` 可以用来调试，在本地浏览器打开 `http://localhost:4000`可以调试本地的静态页面
4. 创建一个静态文章页面，`hexo new "post name"`，会创建到`/hexo/source/_posts`目录下
5. `hexo generate`生成一系列的CSS、HTML等内容
