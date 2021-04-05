# 适用于萌新的hexo自动部署


### 使用步骤

#### 第一步 使用代码 

git 下载[coding仓库](https://frednab.coding.net/public/dev/hexo-pre-install/git/files)代码

`git clone https://e.coding.net/frednab/dev/hexo-pre-install.git`


#### 第二步 修改配置

修改 **项目目录**下的**CNAME**文件里的域名


**其他文件不需要配置**

#### 第三步 更新文章

通过hexo new page 文章.md新建文档

或者在source/_posts目录下撰写自己的文章

#### 第四步 将源码推送到github

通过一下命令将该仓库里的源码推送到github仓库

**如果你是使用git clone方式下载的代码，建议删掉目录下的.git目录再执行如下操作**

```
git init //初始化仓库。
git add . //添加文件到暂存区。(注意有点号.)
git commit -m "更新说明" //将暂存区内容添加到仓库中。标识“更新说明”
git remote add origin XXXX.git  //添加到远程仓库操作，将xxxx.git设置为远程仓库origin
git push -u origin master  //推送master分支到origin仓库

```

提示操作成功后，代码将推送到github上的master分支，github自动部署将启动，将hexo文件自动部署到gh-pages分支

#### 第五步 开启pages

在github仓库 “Settings”选择“GitHub Pages” source项选择Branch:gh-pages
如图：![github pages设置](https://s.ufs.pub/images/2020/10/20201022095332.png)

即可使用由github自动部署的 pages 服务。


---
### 进阶操作

完成以上部署就可以正常使用由hexo生成，github自动部署的pages。你也可以通过以下操作扩展hexo进阶操作

#### 安装更多的hexo插件

通过`npm i XXX --save`插件安装适用于hexo的插件，使用--save可以将插件添加到项目依赖，这样在github自动部署时就能直接使用。

#### 使用github子模块

通过`git submodule add xxxx.git source/_posts ` 可以将你其他git仓库文章。github自动部署时会自动更新子模块里的文章。

#### 使用其他主题

通过`npm i xxx主题 --save`安装其他主题，然后再执行如下操作：

**使用npm uninstall 主题名将旧主题卸载**

1 将新主题的配置文件`_config.yml`改名为`_config.xxx主题.yml`，复制到根目录下

2 修改根目录下的`_config.yml`文件里的`theme: butterfly` 为`theme: xxx`主题

hexo会组合`_config.yml`和`_config.xxx主题.yml`里的内容实现相应的效果。

#### 其他操作请参照hexo教程