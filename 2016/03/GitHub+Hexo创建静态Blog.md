#GitHub + Hexo 创建自己的静态博客

## 一、创建GitHub项目
1. 到`https://github.com`创建一个自己的账号；
2. 创建一个用于放置Blog内容的Repository(代码仓库)，Repository名为 `<username>.github.io`；
3. 在本地新建一个文件夹，并把创建好的Repository Clone到本地目录下；
4. CD到项目的根目录下，创建一个测试用的html文件：`printf "<h1>Testing page</h1> It works.\n" > index.html`
5. push到master分支，然后再浏览器中浏览测试的网页 `<username>.github.io`，如果出现刚才新建的页面就说明成功了；
6. 创建一个没有父节点的分支，并清空刚才的测试文件：
```
git checkout --orphan gh-pages
git rm -rf .
git commit -a -m "modify"
git push origin master
```

## 二、安装`Hexo`
1. 检查有没有安装`npm`，`npm -v`，如果出现版本信息的话，就OK，直接第6步
2. 检查有没有`port`，`port -v`，如果出现了版本信息的话，就OK，直接第5步
3. 去`http://www.macports.org/`下载安装Mac版的`MacPort`
4. 重启终端，使用`port -v`查看`port`的版本是否可用。如果出现版本信息的话，就OK。
5. 使用`sudo port -d sync`来更新`MacPort`套件，可能会出现一堆`sources.conf`的错误，解决方法是修改`/opt/local/etc/macports/sources.conf`文件的最后几行
```
//rsync://rsync.macports.org/release/tarballs/ports.tar [default]
#rsync://rsync.macports.org/release/ports/ [default]
http://www.macports.org/files/ports.tar.gz [default]
```
6\.  然后使用`sudo port install -g npm`就能安装`npm`套件及`NodeJS`相关组件

## 三、使用`Hexo`创建、管理Blog

1. 新建一个文件夹`mkdir hexoBlog`
2. 创建一个hexo Blog : `hexo init`进行初始化
3. `hexo server` 可以用来调试，在本地浏览器打开 `http://localhost:4000`可以调试本地的静态页面
4. 创建一个静态文章页面，`hexo new "post name"`，会创建到`/hexo/source/_posts`目录下
5. `hexo generate`生成一系列的CSS、HTML等内容
6. 打开`_config.yml`配置文件，修改最后：
```
deploy:
  type: git
  repository: git@github.com:<username>/<username>.github.io
  branch: master
```
**注意：**每个冒号后面必须有一个空格，不然会出现语法错误。<br>
然后打开电脑的SSH：系统偏好设置-->共享-->远程登录<br>
`npm install hexo -deployer -git --save`<br>
`hexo g`<br>
`hexo d`  部署到github上page页面。

## 四、`Hexo`操作及美化
[一些操作和美化的方法](http://www.tuicool.com/articles/AfQnQjy/)
## 五、多平台操作
如果你有多台电脑，那么你就可能在多台设备上进行Blog内容的更新，对于Hexo来说，你就需要将你创建的Hexo目录在你的多个电脑上进行共享使用，然后才能进行Blog内容的更新。<br>
可以使用iCloud、百度云、Google Driver、Dropbox等进行内容的同步。<br>
下面还有一篇用`Dropbox`同步的教程：[教程](http://lucifr.com/2013/06/02/hexo-on-cloud-with-dropbox-and-vps/)
## 后记
遇到的问题及解决的渠道

[MacPort update](http://www.cnblogs.com/8586/archive/2012/12/02/2797911.html)<br>
[npm install](https://github.com/nodejs-tw/nodejs-wiki-book/blob/master/zh-tw/node_npm.rst)<br>
[hexo deploy](http://zhidao.baidu.com/link?url=5-PHhRLedH74rZJ-H07LzLKaAU2jyj8_oFbvzOfnJ9NNl4VXausjsrRIxAA_lCamKSCwV49tiPGuCLoqzf_4svIl6JMkmCwSX90gh2-jMoS)<br>
[SSH open share](http://blog.csdn.net/martin_liang/article/details/4002006)<br>
