# 05-移动web开发-flex布局

## 1.0传统布局和flex布局对比


### 1.1 传统布局


- 兼容性好
- 布局繁琐
- 局限性，不能再移动端很好的布局



### 1.2 flex布局


- 操作方便，布局极其简单，移动端使用比较广泛
- pc端浏览器支持情况比较差
- IE11或更低版本不支持flex或仅支持部分



### 1.3 建议


- 如果是pc端页面布局，还是采用传统方式
- 如果是移动端或者是不考虑兼容的pc则采用flex



## 2.0 flex布局原理


- flex 是 flexible Box 的缩写，意为"弹性布局"，用来为盒状模型提供最大的灵活性，任何一个容器都可以指定为 flex 布局。
- 当我们为父盒子设为 flex 布局以后，子元素的 float、clear 和 vertical-align 属性将失效。
- flex布局又叫伸缩布局 、弹性布局 、伸缩盒布局 、弹性盒布局
- 采用 Flex 布局的元素，称为 Flex 容器（flex container），简称"容器"。它的所有子元素自动成为容器成员，称为 Flex 项目（flex item），简称"项目"。


<br />**总结**：就是通过给父盒子添加flex属性，来控制子盒子的位置和排列方式<br />

## 3.0 父项常见属性


- flex-direction：设置主轴的方向
- justify-content：设置主轴上的子元素排列方式
- flex-wrap：设置子元素是否换行
- align-content：设置侧轴上的子元素的排列方式（多行）
- align-items：设置侧轴上的子元素排列方式（单行）
- flex-flow：复合属性，相当于同时设置了 flex-direction 和 flex-wrap



### 3.1 flex-direction设置主轴的方向


- 在 flex 布局中，是分为主轴和侧轴两个方向，同样的叫法有 ： 行和列、x 轴和y 轴
- 默认主轴方向就是 x 轴方向，水平向右
- 默认侧轴方向就是 y 轴方向，水平向下


<br />![1.JPG](https://cdn.nlark.com/yuque/0/2020/jpeg/1483858/1598358294506-fbbbd7ff-478a-4ff4-869a-3ba035abe302.jpeg#align=left&display=inline&height=283&margin=%5Bobject%20Object%5D&name=1.JPG&originHeight=283&originWidth=522&size=7478&status=done&style=none&width=522)<br />

- 注意： 主轴和侧轴是会变化的，就看 flex-direction 设置谁为主轴，剩下的就是侧轴。而我们的子元素是跟着主轴来排列的

![2.JPG](https://cdn.nlark.com/yuque/0/2020/jpeg/1483858/1598358439848-11cb0fa7-5f94-4d48-9510-c63d95e54374.jpeg#align=left&display=inline&height=216&margin=%5Bobject%20Object%5D&name=2.JPG&originHeight=216&originWidth=563&size=14165&status=done&style=none&width=563)<br />

### 3.2 justify-content 设置主轴上的子元素排列方式

<br />![3.JPG](https://cdn.nlark.com/yuque/0/2020/jpeg/1483858/1598358428372-cb45d90f-ae6d-47a8-89ee-043f64fc3858.jpeg#align=left&display=inline&height=290&margin=%5Bobject%20Object%5D&name=3.JPG&originHeight=290&originWidth=825&size=32161&status=done&style=none&width=825)<br />

### 3.3 flex-wrap设置是否换行


- 默认情况下，项目都排在一条线（又称”轴线”）上。flex-wrap属性定义，flex布局中默认是不换行的。
- nowrap 不换行
- wrap 换行



### 3.4 align-items 设置侧轴上的子元素排列方式（单行 ）


- 该属性是控制子项在侧轴（默认是y轴）上的排列方式  在子项为单项（单行）的时候使用
- flex-start 从头部开始
- flex-end 从尾部开始
- center 居中显示
- stretch 拉伸



### 3.5 align-content  设置侧轴上的子元素的排列方式（多行）

<br />设置子项在侧轴上的排列方式 并且只能用于子项出现 换行 的情况（多行），在单行下是没有效果的。<br />
<br />![4.JPG](https://cdn.nlark.com/yuque/0/2020/jpeg/1483858/1598358386971-cf36a1a1-f3f2-4b6f-b35b-d616078a4b94.jpeg#align=left&display=inline&height=327&margin=%5Bobject%20Object%5D&name=4.JPG&originHeight=327&originWidth=679&size=34684&status=done&style=none&width=679)<br />

### 3.6 align-content 和align-items区别


- align-items  适用于单行情况下， 只有上对齐、下对齐、居中和 拉伸
- align-content适应于换行（多行）的情况下（单行情况下无效）， 可以设置 上对齐、下对齐、居中、拉伸以及平均分配剩余空间等属性值。
- 总结就是单行找align-items  多行找 align-content



### 3.7 flex-flow 属性是 flex-direction 和 flex-wrap 属性的复合属性


```
flex-flow:row wrap;
```


## 4.0 flex布局子项常见属性


- flex子项目占的份数
- align-self控制子项自己在侧轴的排列方式
- order属性定义子项的排列顺序（前后顺序）



### 4.1 flex 属性

<br />flex 属性定义子项目分配剩余空间，用flex来表示占多少份数。<br />

```
.item {
    flex: <number>; /* 默认值 0 */
}
```


### 4.2 align-self控制子项自己在侧轴上的排列方式

<br />align-self 属性允许单个项目有与其他项目不一样的对齐方式，可覆盖 align-items 属性。<br />
<br />默认值为 auto，表示继承父元素的 align-items 属性，如果没有父元素，则等同于 stretch。<br />

```
span:nth-child(2) {
      /* 设置自己在侧轴上的排列方式 */
      align-self: flex-end;
}
```


### 4.3 order 属性定义项目的排列顺序

<br />数值越小，排列越靠前，默认为0。<br />
<br />注意：和 z-index 不一样。<br />

```
.item {
    order: <number>;
}
```


## 5.0 携程网首页案例制作

<br />携程网链接：[http://m.ctrip.com](http://m.ctrip.com)<br />

### 5.1 技术选型

<br />方案：我们采取单独制作移动页面方案<br />
<br />技术：布局采取flex布局<br />

### 5.2 搭建相关文件夹

<br />![5.JPG](https://cdn.nlark.com/yuque/0/2020/jpeg/1483858/1598358363346-25cd53a3-cb95-451a-9429-7f07b28edf6e.jpeg#align=left&display=inline&height=178&margin=%5Bobject%20Object%5D&name=5.JPG&originHeight=178&originWidth=432&size=6099&status=done&style=none&width=432)<br />

### 5.3 设置视口标签以及引入初始化样式


```
<meta name="viewport" content="width=device-width, user-scalable=no,initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">

<link rel="stylesheet" href="css/normalize.css">
<link rel="stylesheet" href="css/index.css">
```


### 5.4 常用初始化样式


```
body {
  max-width: 540px;
  min-width: 320px;
  margin: 0 auto;
  font: normal 14px/1.5 Tahoma,"Lucida Grande",Verdana,"Microsoft Yahei",STXihei,hei;
  color: #000;
  background: #f2f2f2;
  overflow-x: hidden;
  -webkit-tap-highlight-color: transparent;
}
```


### 5.5 模块名字划分

<br />![6.JPG](https://cdn.nlark.com/yuque/0/2020/jpeg/1483858/1598358371568-70a24da6-309c-490b-a293-529e9cb4b510.jpeg#align=left&display=inline&height=516&margin=%5Bobject%20Object%5D&name=6.JPG&originHeight=516&originWidth=656&size=45192&status=done&style=none&width=656)<br />

### 5.6 常用模块名字划分


![常用模块命名.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1598537316961-26acf945-5719-4084-ab7d-c722108318d3.png#align=left&display=inline&height=480&margin=%5Bobject%20Object%5D&name=%E5%B8%B8%E7%94%A8%E6%A8%A1%E5%9D%97%E5%91%BD%E5%90%8D.png&originHeight=480&originWidth=844&size=265759&status=done&style=none&width=844)<br />

### 5.7 常见flex布局思路

<br />![常见flex布局思路.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1598537421433-572b1d2a-0d18-4b29-a3f6-a436771df483.png#align=left&display=inline&height=323&margin=%5Bobject%20Object%5D&name=%E5%B8%B8%E8%A7%81flex%E5%B8%83%E5%B1%80%E6%80%9D%E8%B7%AF.png&originHeight=323&originWidth=946&size=32478&status=done&style=none&width=946)<br />

### 5.8 背景线性渐变
![渐变.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1598537475360-d2f2c7cc-a418-4515-8d9f-a6aa42e05950.png#align=left&display=inline&height=55&margin=%5Bobject%20Object%5D&name=%E6%B8%90%E5%8F%98.png&originHeight=55&originWidth=822&size=29297&status=done&style=none&width=822)
```css
background: linear-gradient(起始方向, 颜色1, 颜色2, ...);
background: -webkit-linear-gradient(left, red , blue);
background: -webkit-linear-gradient(left top, red , blue);
```
背景渐变必须添加浏览器私有前缀<br />起始方向可以是： 方位名词 或者 度数 ， 如果省略默认就是 top
