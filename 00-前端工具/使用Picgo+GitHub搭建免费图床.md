### 使用Picgo+GitHub搭建免费图床

**一、PicGo介绍**

PicGo是一款图片上传工具，目前支持SM.MS图床、腾讯云COS、微博图床、GitHub图床、七牛图床、Imgur图床、阿里云OSS、又拍云图床，未来将支持更多图床。

而这里边，SM.MS和Imgur有免费版也有收费版，腾讯云、七牛、阿里云、又拍云都是收费的，微博图床已经挂了。现在微软接管了GitHub以后，貌似公有仓库已经不限个数了，而且单个仓库容量已经放宽至2GB。这绝对够用了，不够就再建一个共有仓呗。那么，也就剩下GitHub安全、免费又可靠了。

PicGo项目地址：https://github.com/Molunerfinn/PicGo

**二、GitHub图床**

1. 创建GitHub图床之前，需要注册/登陆GitHub账号

2. 创建Repository

点击"New repository"按钮

![Repository.png](https://raw.githubusercontent.com/SNGSUN/Blog-images/master/Repository.png.jpg)

填写相关信息，创建一个存储图片的仓库

![Create a New Repository](https://raw.githubusercontent.com/SNGSUN/Blog-images/master/Create a New Repository.png)

3. 生成一个Token用于操作GitHub repository

回到主页，点击"Settings"按钮

![SNGSUN](https://raw.githubusercontent.com/SNGSUN/Blog-images/master/SNGSUN.png)

进入页面后，点击"Developer settings"按钮，点击"Personal access tokens"按钮

![Personal Access Tokens](https://raw.githubusercontent.com/SNGSUN/Blog-images/master/Personal Access Tokens.png)

填写描述，选择"repo"权限，然后点击"Generate token"按钮

![New personal access token](https://raw.githubusercontent.com/SNGSUN/Blog-images/master/New personal access token.png)



注：创建成功后，会生成一串token，这串token之后不会再显示，所以第一次看到的时候，可以建个文本文件好好保存，忘记了只有重新生成，每次都不一样。

 

**三、配置PicGo**

1. 下载安装并运行PicGo

   PicGo项目下载地址：https://github.com/Molunerfinn/PicGo

   PicGo蓝奏云下载地址：https://www.lanzous.com/b04abbw8h

2. 配置图床

之后按照这个配置格式配置即可！

![github设置.png](https://raw.githubusercontent.com/SNGSUN/Blog-images/master/github设置.png.jpg)

第一行：设定仓库名按照“账户名/仓库名的格式填写”，比如我的是：SNGSUN/Blog-images

第二行：统一填写 master

第三行：将之前的Token粘贴在这里

第四行：留空

第五行：自定义域名的作用是在上传图片后成功后，PicGo会将“自定义域名+上传的图片名”生成的访问链接，放到剪切板上

自定义域名：https://raw.githubusercontent.com/账户名/仓库名/master

比如我的是：https://raw.githubusercontent.com/SNGSUN/Blog-images/master

3. 上传图片

点击确定后就配置完成了，我们截图后点击`剪切板图片上传`，如果上传成功，拿到的外链放到Markdown中正常访问，就OK啦。

![上传.png](https://raw.githubusercontent.com/SNGSUN/Blog-images/master/上传.png.jpg)

4. 快捷键及相关配置

支持快捷键command+shift+p（macOS）或者control+shift+p（windows\linux）用以支持快捷上传剪贴板里的图片（第一张）。

PicGo支持自定义快捷键，使用方法见配置手册。

注：可以将快捷键设置为ctrl+shift+c

**总结**

将上面的步骤都设置好，每次截图之后，都可以按一下ctrl+shift+c，这样就会将剪切板上面的截图转化为在线网络图片链接，简直就是爽的不要不要的，关键是背靠 GitHub 和微软，比自建服务器都稳！