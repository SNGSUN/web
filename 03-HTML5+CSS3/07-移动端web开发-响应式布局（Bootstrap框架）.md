# 07-移动端web开发-响应式布局（Bootstrap框架）

## 1.0 响应式开发原理


### 1.1 响应式开发原理


就是使用媒体查询针对不同宽度的设备进行布局和样式的设置，从而适配不同设备的目的。


设备的划分情况：


- 小于768的为超小屏幕（手机）
- 768~992之间的为小屏设备（平板）
- 992~1200的中等屏幕（桌面显示器）
- 大于1200的宽屏设备（大桌面显示器）



### 1.2 响应式布局容器


响应式需要一个父级做为布局容器，来配合子级元素来实现变化效果。
原理就是在不同屏幕下，通过媒体查询来改变这个布局容器的大小，再改变里面子元素的排列方式和大小，从而实现不同屏幕下，看到不同的页面布局和样式变化。


父容器版心的尺寸划分


   - 超小屏幕（手机，小于 768px）：设置宽度为 100%
   - 小屏幕（平板，大于等于 768px）：设置宽度为 750px
   - 中等屏幕（桌面显示器，大于等于 992px）：宽度设置为 970px
   - 大屏幕（大桌面显示器，大于等于 1200px）：宽度设置为 1170px



但是我们也可以根据实际情况自己定义划分


### 1.3 响应式布局案例
#### 案例：效果图
**![响应式案例.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1598706046030-8f4443a7-cb18-42c0-80ee-887b7bb740df.png#align=left&display=inline&height=555&margin=%5Bobject%20Object%5D&name=%E5%93%8D%E5%BA%94%E5%BC%8F%E6%A1%88%E4%BE%8B.png&originHeight=555&originWidth=1141&size=18079&status=done&style=none&width=1141)**
#### 案例：需求分析
① 当我们屏幕大于等于800像素，我们给nav宽度为800px，因为里面子盒子需要浮动，所以nav需要清除浮动。
② nav里面包含8个小li 盒子，每个盒子的宽度定为 100px， 高度为 30px，浮动一行显示。
③ 当我们屏幕缩放，宽度小于800像素的时候， nav盒子宽度修改为 100% 宽度。
④ nav里面的8个小li，宽度修改为 33.33%，这样一行就只能显示3个小li ，剩余下行显示。
## 2.0 bootstrap的介绍


### 2.1 Bootstrap简介


Bootstrap 来自 Twitter（推特），是目前最受欢迎的前端框架。Bootstrap 是基于HTML、CSS 和 JAVASCRIPT 的，它简洁灵活，使得 Web 开发更加快捷。


中文官网：**[http://www.bootcss.com/](http://www.bootcss.com/)**
官网：**[http://getbootstrap.com/](http://getbootstrap.com/)**
推荐使用：**[http://bootstrap.css88.com/](http://bootstrap.css88.com/) **


框架：顾名思义就是一套架构，它有一套比较完整的网页功能解决方案，而且控制权在框架本身，有预制样式库、组件和插件。使用者要按照框架所规定的某种规范进行开发。


### 2.2 bootstrap优点


- 标准化的html+css编码规范
- 提供了一套简洁、直观、强悍的组件
- 有自己的生态圈，不断的更新迭代
- 让开发更简单，提高了开发的效率



### 2.3 版本简介


2.x.x：停止维护,兼容性好,代码不够简洁，功能不够完善。


3.x.x：目前使用最多,稳定,但是放弃了IE6-IE7。对 IE8 支持但是界面效果不好,偏向用于开发响应式布局、移动设备优先的WEB 项目。


4.x.x：最新版，目前还不是很流行


### 2.4 bootstrap基本使用


在现阶段我们还没有接触JS相关课程，所以我们只考虑使用它的样式库。


Bootstrap 使用四步曲：


1. 创建文件夹结构
![1.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1598538724779-52b637e8-f66e-4dc5-bfb4-0541aeb66b69.png#align=left&display=inline&height=309&margin=%5Bobject%20Object%5D&name=1.png&originHeight=309&originWidth=852&size=30599&status=done&style=none&width=852)
2. 创建 html 骨架结构```
<!DOCTYPE html>
<html lang="zh-CN">
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <!-- 上述3个meta标签*必须*放在最前面，任何其他内容都*必须*跟随其后！ -->
    <title>Bootstrap 101 Template</title>

    <!-- Bootstrap -->
    <link href="css/bootstrap.min.css" rel="stylesheet">

    <!-- HTML5 shim and Respond.js for IE8 support of HTML5 elements and media queries -->
    <!-- WARNING: Respond.js doesn't work if you view the page via file:// -->
    <!--[if lt IE 9]>
      <script src="//cdn.bootcss.com/html5shiv/3.7.2/html5shiv.min.js"></script>
      <script src="//cdn.bootcss.com/respond.js/1.4.2/respond.min.js"></script>
    <![endif]-->
  </head>
  <body>
    <h1>你好，世界！</h1>

    <!-- jQuery (necessary for Bootstrap's JavaScript plugins) -->
    <script src="//cdn.bootcss.com/jquery/1.11.3/jquery.min.js"></script>
    <!-- Include all compiled plugins (below), or include individual files as needed -->
    <script src="js/bootstrap.min.js"></script>
  </body>
</html>
```

3. 引入相关样式文件```
<!-- Bootstrap 核心样式-->
<link rel="stylesheet" href="bootstrap/css/bootstrap.min.css">
```

4. 书写内容
直接拿Bootstrap 预先定义好的样式来使用
修改Bootstrap 原来的样式，注意权重问题
学好Bootstrap 的关键在于知道它定义了哪些样式，以及这些样式能实现什么样的效果



### 2.5 bootstrap布局容器


Bootstrap 需要为页面内容和栅格系统包裹一个 .container 或者.container-fluid 容器，它提供了两个作此用处的类。


.container


- 响应式布局的容器  固定宽度
- 大屏 ( >=1200px)  宽度定为 1170px
- 中屏 ( >=992px)   宽度定为  970px
- 小屏 ( >=768px)   宽度定为  750px
- 超小屏  (100%)



.container-fluid


- 流式布局容器 百分百宽度
- 占据全部视口（viewport）的容器。



### 2.6 bootstrap栅格系统
**栅格系统**英文为“grid systems”,也有人翻译为“网格系统”，它是指将页面布局划分为等宽的列，然后通
过列数的定义来模块化页面布局。


Bootstrap提供了一套响应式、移动设备优先的流式栅格系统，随着屏幕或视口（viewport）尺寸的增加，系统会自动分为最多12列。


栅格系统用于通过一系列的行（row）与列（column）的组合来创建页面布局，你的内容就可以放入这些创建好的布局中。
![图片.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1598706571592-e02c7d8d-e276-46da-aa28-125bc02a6e64.png#align=left&display=inline&height=234&margin=%5Bobject%20Object%5D&name=%E5%9B%BE%E7%89%87.png&originHeight=234&originWidth=1065&size=39032&status=done&style=none&width=1065)

- 按照不同屏幕划分为1~12 等份
- 行（row） 可以去除父容器作用15px的边距
- xs-extra small：超小； sm-small：小；  md-medium：中等； lg-large：大；
- 列（column）大于 12，多余的“列（column）”所在的元素将被作为一个整体另起一行排列
- 每一列默认有左右15像素的 padding
- 可以同时为一列指定多个设备的类名，以便划分不同份数  例如 class="col-md-4 col-sm-6"



栅格嵌套
![图片.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1598706682817-faa301f9-4a6b-46ce-9d73-dc5008dab51e.png#align=left&display=inline&height=70&margin=%5Bobject%20Object%5D&name=%E5%9B%BE%E7%89%87.png&originHeight=70&originWidth=1058&size=1765&status=done&style=none&width=1058)
栅格系统内置的栅格系统将内容再次嵌套。简单理解就是一个列内再分成若干份小列。我们可以通过添加一个新的 .row 元素和一系列 .col-sm-_ 元素到已经存在的 .col-sm-_
元素内。


```
<!-- 列嵌套 -->
 <div class="col-sm-4">
    <div class="row">
         <div class="col-sm-6">小列</div>
         <div class="col-sm-6">小列</div>
    </div>
</div>
```


列偏移
![图片.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1598706770634-c05bb467-cfd7-4979-8f3d-5da0e4407cfd.png#align=left&display=inline&height=66&margin=%5Bobject%20Object%5D&name=%E5%9B%BE%E7%89%87.png&originHeight=66&originWidth=991&size=3034&status=done&style=none&width=991)
使用 .col-md-offset-_ 类可以将列向右侧偏移。这些类实际是通过使用 _ 选择器为当前元素增加了左侧的边距（margin）。


```
 <!-- 列偏移 -->
  <div class="row">
      <div class="col-lg-4">1</div>
      <div class="col-lg-4 col-lg-offset-4">2</div>
  </div>
```


列排序
![图片.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1598706839672-518697f9-82cb-4f5d-b525-727c45cdbb5f.png#align=left&display=inline&height=158&margin=%5Bobject%20Object%5D&name=%E5%9B%BE%E7%89%87.png&originHeight=158&originWidth=1000&size=6049&status=done&style=none&width=1000)
通过使用 .col-md-push-_ 和 .col-md-pull-_ 类就可以很容易的改变列（column）的顺序。


```
 <!-- 列排序 -->
  <div class="row">
      <div class="col-lg-4 col-lg-push-8">左侧</div>
      <div class="col-lg-8 col-lg-pull-4">右侧</div>
  </div>
```


### 2.7 响应式工具


为了加快对移动设备友好的页面开发工作，利用媒体查询功能，并使用这些工具类可以方便的针对不同设备展示或隐藏页面内容。
![2.jpg](https://cdn.nlark.com/yuque/0/2020/jpeg/1483858/1598538743975-56f41598-987c-4001-9468-efdf210cf219.jpeg#align=left&display=inline&height=251&margin=%5Bobject%20Object%5D&name=2.jpg&originHeight=251&originWidth=925&size=16506&status=done&style=none&width=925)
Bootstrap 其他（按钮、表单、表格） 请参考Bootstrap 文档。
## 3.0 阿里百秀案例制作
![图片.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1598707005302-44e72802-194b-4150-917c-8be4fc27f2ed.png#align=left&display=inline&height=716&margin=%5Bobject%20Object%5D&name=%E5%9B%BE%E7%89%87.png&originHeight=716&originWidth=1344&size=638001&status=done&style=none&width=1344)
### 3.1 技术选型


方案：我们采取响应式页面开发方案
技术：bootstrap框架
设计图： 本设计图采用 1280px 设计尺寸
### 3.2. 页面布局分析
![图片.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1598707128870-d5c930d4-13f5-4df4-ad8f-e36ba4629842.png#align=left&display=inline&height=626&margin=%5Bobject%20Object%5D&name=%E5%9B%BE%E7%89%87.png&originHeight=626&originWidth=954&size=338679&status=done&style=none&width=954)
### 3.3 屏幕划分分析
① 屏幕缩放发现 中屏幕 和 大屏幕布局 是一致的。 因此我们列 定义为 col-md- 就可以了， md 是大于等于 970 以上的
② 屏幕缩放发现 小屏幕 布局发生变化，因此我们需要为 小屏幕根据需求改变布局
③ 屏幕缩放发现 超小屏幕布局又发生变化，因此我们需要为 超小屏幕根据需求改变布局
④ 策略： 我们先布局 md以上的 pc端布局，最后根据实际需求在修改 小屏幕 和 超小屏幕的 特殊布局样式
### 3.4 项目结构搭建


Bootstrap 使用四步曲：创建文件夹结构、创建 html 骨架结构、引入相关样式文件、书写内容
![1.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1598538724779-52b637e8-f66e-4dc5-bfb4-0541aeb66b69.png#align=left&display=inline&height=309&margin=%5Bobject%20Object%5D&name=1.png&originHeight=309&originWidth=852&size=30599&status=done&style=none&width=852)
### 
container宽度修改


因为本效果图采取 1280的宽度， 而Bootstrap 里面 container宽度 最大为 1170px，因此我们需要手动改下container宽度


```
 /* 利用媒体查询修改 container宽度适合效果图宽度  */
  @media (min-width: 1280px) { 
    .container { 
	width: 1280px; 
     } 
   }
```


