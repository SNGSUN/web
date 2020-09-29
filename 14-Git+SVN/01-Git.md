# 01-Git

## 1. Git基础![01.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1601382744473-5fe0e6ad-6445-40fe-91d4-06003cadec08.png#align=left&display=inline&height=282&margin=%5Bobject%20Object%5D&name=01.png&originHeight=282&originWidth=638&size=23244&status=done&style=none&width=638)


### 1.1 版本管理


#### 1.1.1 什么是版本管理


版本管理是一种记录文件变化的方式，以便将来查阅特定版本的文件内容。






#### 1.1.2 人为维护文档版本的问题


1. 文档数量多且命名不清晰导致文档版本混乱
2. 每次编辑文档需要复制，不方便
3. 多人同时编辑同一个文档，容易产生覆盖



![04.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1601382755048-c378dd9a-ebc5-41b7-85dd-9731ae231200.png#align=left&display=inline&height=213&margin=%5Bobject%20Object%5D&name=04.png&originHeight=213&originWidth=473&size=12916&status=done&style=none&width=473)


### 1.2 Git 是什么


Git是一个版本管理控制系统（缩写VCS），它可以在任何时间点，将文档的状态作为更新记录保存起来，也可以在任何时间点，将更新记录恢复回来。


![19.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1601382804320-4b3d259a-d407-4ab3-888c-fb928aa34665.png#align=left&display=inline&height=693&margin=%5Bobject%20Object%5D&name=19.png&originHeight=693&originWidth=970&size=46542&status=done&style=none&width=970)


### 1.3 Git 安装


[下载地址](https://git-scm.com/downloads)


在安装的过程中，所有选项使用默认值即可。


### 1.4 Git 基本工作流程
| git仓库 | 暂存区 | 工作目录 |
| --- | --- | --- |
| 用于存放提交记录 | 临时存放被修改文件 | 被Git管理的项目目录 |



![05.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1601382820294-f49c6c96-e221-425e-8360-7d88b359df41.png#align=left&display=inline&height=262&margin=%5Bobject%20Object%5D&name=05.png&originHeight=262&originWidth=571&size=10714&status=done&style=none&width=571)


### 1.5 Git 的使用


#### 1.5.1 Git 使用前配置


在使用 git 前，需要告诉 git 你是谁，在向 git 仓库中提交时需要用到。


1. 配置提交人姓名：`git config --global user.name 提交人姓名`
2. 配置提交人姓名：`git config --global user.email 提交人邮箱`
3. 查看git配置信息：`git config --list`



**注意**


1. 如果要对配置信息进行修改，重复上述命令即可。
2. 配置只需要执行一次。



#### 1.5.2 提交步骤


1. `git init` 初始化git仓库
2. `git status` 查看文件状态
3. `git add 文件列表` 追踪文件
4. `git commit -m 提交信息`  向仓库中提交代码
5. `git log` 查看提交记录



#### 1.5.3 撤销


- 用暂存区中的文件覆盖工作目录中的文件： `git checkout 文件`
- 将文件从暂存区中删除： `git rm --cached 文件`
- 将 git 仓库中指定的更新记录恢复出来，并且覆盖暂存区和工作目录：`git rest --hard commitID`



![07.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1601382777783-87b2136e-0317-4aa4-bf08-ca4fd0df106b.png#align=left&display=inline&height=257&margin=%5Bobject%20Object%5D&name=07.png&originHeight=257&originWidth=427&size=11344&status=done&style=none&width=427)


## 2. Git进阶


### 2.1 分支


为了便于理解，大家暂时可以认为分支就是当前工作目录中代码的一份副本。


使用分支，可以让我们从开发主线上分离出来，以免影响开发主线。


![08.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1601382845494-ff81fc6b-e1d9-422a-ad61-c3547c9b409f.png#align=left&display=inline&height=346&margin=%5Bobject%20Object%5D&name=08.png&originHeight=346&originWidth=562&size=8895&status=done&style=none&width=562)


#### 2.1.1 分支细分


1. 主分支（master）：第一次向 git 仓库中提交更新记录时自动产生的一个分支。

![06.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1601382863088-91d012a0-71a4-4e9d-b2a3-abd3dd016bad.png#align=left&display=inline&height=182&margin=%5Bobject%20Object%5D&name=06.png&originHeight=182&originWidth=582&size=12980&status=done&style=none&width=582)

2. 、开发分支（develop）：作为开发的分支，基于 master 分支创建。

![09.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1601382871545-ad6549a9-8d13-42f3-a4b6-bd0fd9667f36.png#align=left&display=inline&height=804&margin=%5Bobject%20Object%5D&name=09.png&originHeight=804&originWidth=534&size=25791&status=done&style=none&width=534)

3. 功能分支（feature）：作为开发具体功能的分支，基于开发分支创建

![10.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1601382880359-0e057dab-72a8-4d1a-8b90-6143f1f4be95.png#align=left&display=inline&height=714&margin=%5Bobject%20Object%5D&name=10.png&originHeight=714&originWidth=266&size=11795&status=done&style=none&width=266)


**功能分支 -> 开发分支 -> 主分支**


#### 2.1.2 分支命令


- `git branch` 查看分支
- `git branch 分支名称` 创建分支
- `git checkout 分支名称` 切换分支
- `git merge 来源分支` 合并分支
- `git branch -d 分支名称` 删除分支（分支被合并后才允许删除）（-D 强制删除）



### 2.2 暂时保存更改


在git中，可以暂时提取分支上所有的改动并存储，让开发人员得到一个干净的工作副本，临时转向其他工作。


使用场景：分支临时切换


- 存储临时改动：`git stash`
- 恢复改动：`git stash pop`



## 3. Github


在版本控制系统中，大约90%的操作都是在本地仓库中进行的：暂存，提交，查看状态或者历史记录等等。除此之外，如果仅仅只有你一个人在这个项目里工作，你永远没有机会需要设置一个远程仓库。


只有当你需要和你的开发团队共享数据时，设置一个远程仓库才有意义。你可以把它想象成一个 “文件管理服务器”，利用这个服务器可以与开发团队的其他成员进行数据交换。


### 3.1 注册


1. 访问[github](https://github.com/)首页，点击 Sign up 连接。（注册）

![11.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1601382927270-9a56908c-82dd-4273-b470-ce2502180e0b.png#align=left&display=inline&height=428&margin=%5Bobject%20Object%5D&name=11.png&originHeight=428&originWidth=800&size=100022&status=done&style=none&width=800)

2. 填写用户名、邮箱地址、GitHub登陆密码

![12.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1601382932939-ef0ecc5d-9138-425f-962c-43cde8339fc9.png#align=left&display=inline&height=541&margin=%5Bobject%20Object%5D&name=12.png&originHeight=541&originWidth=800&size=103737&status=done&style=none&width=800)

3. 选择计划

![13.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1601382941125-9d964bf0-253a-4a65-b774-3bfb697c354a.png#align=left&display=inline&height=726&margin=%5Bobject%20Object%5D&name=13.png&originHeight=726&originWidth=800&size=133323&status=done&style=none&width=800)

4. 填写 GitHub 问题

![14.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1601382949105-2293ed6b-73bd-4fc3-babc-ab990a6f329a.png#align=left&display=inline&height=649&margin=%5Bobject%20Object%5D&name=14.png&originHeight=649&originWidth=800&size=98490&status=done&style=none&width=800)

5. 验证邮箱

![15.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1601382957285-3f0cc42f-1b7f-445d-a1a8-dd7543528034.png#align=left&display=inline&height=303&margin=%5Bobject%20Object%5D&name=15.png&originHeight=303&originWidth=800&size=58265&status=done&style=none&width=800)

6. GitHub 个人中心

![16.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1601382965194-16f566c6-c790-4e42-acf8-512961f6b7e1.png#align=left&display=inline&height=438&margin=%5Bobject%20Object%5D&name=16.png&originHeight=438&originWidth=800&size=151193&status=done&style=none&width=800)


### 3.2 多人协作开发流程


- A在自己的计算机中创建本地仓库
- A在github中创建远程仓库
- A将本地仓库推送到远程仓库
- B克隆远程仓库到本地进行开发
- B将本地仓库中开发的内容推送到远程仓库
- A将远程仓库中的最新内容拉去到本地



![20.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1601383000696-11da72bd-fa7a-4163-a3ba-8afe32363894.png#align=left&display=inline&height=450&margin=%5Bobject%20Object%5D&name=20.png&originHeight=450&originWidth=808&size=80122&status=done&style=none&width=808)
![21.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1601383008214-f4c8ff97-17dd-4ad4-96a1-35e4588060e2.png#align=left&display=inline&height=450&margin=%5Bobject%20Object%5D&name=21.png&originHeight=450&originWidth=798&size=78899&status=done&style=none&width=798)


### 3.3 创建仓库


1. 填写仓库基本信息

![17.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1601383023476-4e731bdd-db69-4cde-b1de-d50988419204.png#align=left&display=inline&height=440&margin=%5Bobject%20Object%5D&name=17.png&originHeight=440&originWidth=800&size=59270&status=done&style=none&width=800)

2. 将本地仓库推送到远程仓库

![18.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1601383032307-04fd01ca-7068-433f-a633-9bd40fe12e8a.png#align=left&display=inline&height=546&margin=%5Bobject%20Object%5D&name=18.png&originHeight=546&originWidth=800&size=112649&status=done&style=none&width=800)

   1. git push 远程仓库地址 分支名称
   2. git push 远程仓库地址别名 分支名称
   3. git push -u 远程仓库地址别名 分支名称
-u 记住推送地址及分支，下次推送只需要输入git push即可
   4. git remote add 远程仓库地址别名 远程仓库地址



### 3.4 拉取操作


#### 3.4.1 克隆仓库


克隆远端数据仓库到本地：`git clone 仓库地址`


#### 3.4.2 拉取远程仓库中最新的版本


拉取远程仓库中最新的版本：`git pull 远程仓库地址 分支名称`


### 3.5 解决冲突


在多人同时开发一个项目时，如果两个人修改了同一个文件的同一个地方，就会发生冲突。冲突需要人为解决。


### 3.6 跨团队协作


1. 程序员 C fork仓库
2. 程序员 C 将仓库克隆在本地进行修改
3. 程序员 C 将仓库推送到远程
4. 程序员 C 发起pull reqest
5. 原仓库作者审核
6. 原仓库作者合并代码



### 3.7 ssh免登陆


https协议仓库地址：[https://github.com/itcast-frontEnd/git-demo.git](https://github.com/itcast-frontEnd/git-demo.git)


![22.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1601383056688-c80c3867-94db-4225-b4bf-74a7fe27df97.png#align=left&display=inline&height=696&margin=%5Bobject%20Object%5D&name=22.png&originHeight=696&originWidth=632&size=42468&status=done&style=none&width=632)


生成秘钥：`ssh-keygen`


秘钥存储目录：C:\Users\用户\.ssh


公钥名称：id_rsa.pub


私钥名称：id_rsa


![23.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1601383064145-0a602ba3-fa5d-4bb4-939c-155a691a8180.png#align=left&display=inline&height=354&margin=%5Bobject%20Object%5D&name=23.png&originHeight=354&originWidth=800&size=86972&status=done&style=none&width=800)


![24.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1601383075493-a10cb86a-ae82-4601-a78f-1ba1aece7b43.png#align=left&display=inline&height=450&margin=%5Bobject%20Object%5D&name=24.png&originHeight=450&originWidth=800&size=48478&status=done&style=none&width=800)


### 3.8 GIT忽略清单


将不需要被git管理的文件名字添加到此文件中，在执行git命令的时候，git就会忽略这些文件。


git忽略清单文件名称：**.gitignore**


将工作目录中的文件全部添加到暂存区：`git add .`
