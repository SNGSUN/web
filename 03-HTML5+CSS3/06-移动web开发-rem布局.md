# 06-移动web开发-rem布局

## 0.0 思考方案 ？

<br />1. 页面布局文字能否随着屏幕大小变化而变化？<br />2. 流式布局和flex布局主要针对于宽度布局，那高度如何设置？<br />3. 怎么样让屏幕发生变化的时候元素高度和宽度等比例缩放？
## 1.0 rem基础


### 1.1 rem单位

<br />rem (root em)是一个相对单位，类似于em，em是父元素字体大小。<br />
<br />不同的是rem的基准是相对于html元素的字体大小。<br />
<br />比如，根元素（html）设置font-size=12px; 非根元素设置width:2rem; 则换成px表示就是24px。<br />

```
/* 根html 为 12px */
html {
   font-size: 12px;
}
/* 此时 div 的字体大小就是 24px */       
div {
    font-size: 2rem;
}
```

<br />rem的优势：父元素文字大小可能不一致， 但是整个页面只有一个html，可以很好来控制整个页面的元素大小。<br />

## 2.0 媒体查询


### 2.1 什么是媒体查询

<br />媒体查询（Media Query）是CSS3新语法。<br />

- 使用 @media查询，可以针对不同的媒体类型定义不同的样式
- [@media ](/media ) 可以针对不同的屏幕尺寸设置不同的样式 
- 当你重置浏览器大小的过程中，页面也会根据浏览器的宽度和高度重新渲染页面
- 目前针对很多苹果手机、Android手机，平板等设备都用得到多媒体查询

![手机.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1598539259267-ad68f9d4-1d7b-42d1-817f-a8c22b215eb4.png#align=left&display=inline&height=239&margin=%5Bobject%20Object%5D&name=%E6%89%8B%E6%9C%BA.png&originHeight=239&originWidth=622&size=107650&status=done&style=none&width=622)
### 2.2 媒体查询语法规范


- 用 @media开头 注意@符号
- mediatype  媒体类型
- 关键字 and  not  only
- media feature 媒体特性必须有小括号包含



```
@media mediatype and|not|only (media feature) {
    CSS-Code;
}
```


1. mediatype 查询类型


<br />       将不同的终端设备划分成不同的类型，称为媒体类型<br />![1.jpg](https://cdn.nlark.com/yuque/0/2020/jpeg/1483858/1598538312832-a651c06a-7841-4973-9567-10aa93977eeb.jpeg#align=left&display=inline&height=193&margin=%5Bobject%20Object%5D&name=1.jpg&originHeight=193&originWidth=915&size=9309&status=done&style=none&width=915)

2. 关键字


<br />       关键字将媒体类型或多个媒体特性连接到一起做为媒体查询的条件。<br />

- and：可以将多个媒体特性连接到一起，相当于“且”的意思。
- not：排除某个媒体类型，相当于“非”的意思，可以省略。
- only：指定某个特定的媒体类型，可以省略。



3. 媒体特性<br />每种媒体类型都具体各自不同的特性，根据不同媒体类型的媒体特性设置不同的展示风格。我们暂且了解三个。<br />注意他们要加小括号包含

![2.jpg](https://cdn.nlark.com/yuque/0/2020/jpeg/1483858/1598538336474-36bba7d3-7068-4b24-9f0a-7d8f13c15e05.jpeg#align=left&display=inline&height=195&margin=%5Bobject%20Object%5D&name=2.jpg&originHeight=195&originWidth=918&size=13395&status=done&style=none&width=918)

4. 媒体查询书写规则<br />注意： 为了防止混乱，媒体查询我们要按照从小到大或者从大到小的顺序来写,但是我们最喜欢的还是从小到大来写，这样代码更简洁

![3.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1598538365935-de21b213-cd95-4377-bba8-5c7d4e6f457c.png#align=left&display=inline&height=445&margin=%5Bobject%20Object%5D&name=3.png&originHeight=445&originWidth=1034&size=54287&status=done&style=none&width=1034)
### 2.3 案例：根据页面宽度改变背景变色
#### 案例：实现思路
① 按照从大到小的或者从小到大的思路<br />② 注意我们有最大值 max-width 和最小值 min-width都是包含等于的<br />③ 当屏幕小于540像素， 背景颜色变为蓝色 （x <= 539） <br />④ 当屏幕大于等于540像素 并且小于等于 969像素的时候 背景颜色为 绿色 ( 540=<x <= 969） <br />⑤ 当屏幕大于等于 970像素的时候，背景颜色为红色 （ x >= 970）
#### 媒体查询书写规则
注意： 为了防止混乱，媒体查询我们要按照从小到大或者从大到小的顺序来写,但是我们最喜欢的还是从小到大来写，这样代码更简洁。<br />![媒体查询.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1598539594004-de1b65d4-c4a0-4a42-a026-3b6d283e9786.png#align=left&display=inline&height=446&margin=%5Bobject%20Object%5D&name=%E5%AA%92%E4%BD%93%E6%9F%A5%E8%AF%A2.png&originHeight=446&originWidth=929&size=19469&status=done&style=none&width=929)<br />**2.3 媒体查询+rem实现元素动态大小变化**<br />rem单位是跟着html来走的，有了rem页面元素可以设置不同大小尺寸<br />媒体查询可以根据不同设备宽度来修改样式<br />媒体查询+rem 就可以实现不同设备宽度，实现页面元素大小的动态变化
### 2.4 引入资源（理解）

<br />当样式比较繁多的时候，我们可以针对不同的媒体使用不同 stylesheets（样式表）。<br />原理，就是直接在link中判断设备的尺寸，然后引用不同的css文件。

#### 1. 语法规范
```css
<link rel="stylesheet" media="mediatype and|not|only (media feature)" href="mystylesheet.css">
```
#### 2. 示例
```css
<link rel="stylesheet" href="styleA.css" media="screen and (min-width: 400px)">
```
## 3.0 less 基础


### 3.1 维护css弊端

<br />CSS 是一门非程序式语言，没有变量、函数、SCOPE（作用域）等概念。<br />

- CSS 需要书写大量看似没有逻辑的代码，CSS 冗余度是比较高的。
- 不方便维护及扩展，不利于复用。
- CSS 没有很好的计算能力
- 非前端开发工程师来讲，往往会因为缺少 CSS 编写经验而很难写出组织良好且易于维护的 CSS 代码项目。



### 3.2 Less 介绍

<br />Less（LeanerStyle Sheets 的缩写）是一门 CSS扩展语言，也成为CSS预处理器。<br />
<br />做为 CSS的一种形式的扩展，它并没有减少CSS的功能，而是在现有的CSS语法上，为CSS加入程序式语言的特性。<br />
<br />它在CSS 的语法基础之上，引入了变量，Mixin（混入），运算以及函数等功能，大大简化了 CSS 的编写，并且降低了 CSS的维护成本，就像它的名称所说的那样，Less可以让我们用更少的代码做更多的事情。<br />
<br />Less中文网址：[http://](http://lesscss.cn/)[less](http://lesscss.cn/)[css.cn/](http://lesscss.cn/)<br />
<br />常见的CSS预处理器：Sass、Less、Stylus<br />
<br />一句话：Less是一门 CSS 预处理语言，它扩展了CSS的动态特性。<br />

### 3.3 Less安装

<br />① 安装nodejs，可选择版本(8.0)，网址：[http://nodejs.cn/download/](http://nodejs.cn/download/)<br />② 检查是否安装成功，使用cmd命令（win10是window+r 打开运行输入cmd）  ---输入“node –v”查看版本即可<br />③ 基于nodejs在线安装Less，使用cmd命令“npm install -g less”即可<br />④ 检查是否安装成功，使用cmd命令“ lessc -v ”查看版本即可<br />![node.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1598540148049-cb75a5e6-c1e3-4a54-90b5-6c21b70083a8.png#align=left&display=inline&height=230&margin=%5Bobject%20Object%5D&name=node.png&originHeight=230&originWidth=877&size=45565&status=done&style=none&width=877)
### 3.4 Less 使用
我们首先新建一个后缀名为less的文件， 在这个less文件里面书写less语句。<br />
#### Less 变量
变量是指没有固定的值，可以改变的。因为我们CSS中的一些颜色和数值等经常使用。<br />

```
@变量名:值;
```


- 必须有@为前缀
- 不能包含特殊字符
- 不能以数字开头
- 大小写敏感



```
@color: pink;
```


#### Less 编译
Less 编译 vocode Less 插件<br />Easy LESS 插件用来把less文件编译为css文件<br />安装完毕插件，重新加载下 vscode。<br />只要保存一下Less文件，会自动生成CSS文件。<br />![4.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1598538402096-363a2dfa-60cd-454f-9261-7349c593e161.png#align=left&display=inline&height=513&margin=%5Bobject%20Object%5D&name=4.png&originHeight=513&originWidth=822&size=140091&status=done&style=none&width=822)
#### Less 嵌套


```css
// 将css改为less
// 我们经常用到选择器的嵌套
#header .logo {
  width: 300px;
}
// Less 嵌套写法
#header {
    .logo {
       width: 300px;
    }
}
```

<br />如果遇见 （交集|伪类|伪元素选择器）

内层选择器的前面没有 & 符号，则它被解析为父选择器的后代；<br />如果有 & 符号，它就被解析为父元素自身或父元素的伪类。
```css
a:hover{
    color:red;
}
// Less 嵌套写法
a{
  &:hover{
      color:red;
  }
}
```


#### Less 运算

<br />任何数字、颜色或者变量都可以参与运算。就是Less提供了加（+）、减（-）、乘（*）、除（/）算术运算。<br />

```
/*Less 里面写*/
@witdh: 10px + 5;
div {
    border: @witdh solid red;
}
/*生成的css*/
div {
  border: 15px solid red;
}
/*Less 甚至还可以这样 */
width: (@width + 5) * 2;
```

<br />**注意：**

- 乘号（*）和除号（/）的写法
- 运算符中间左右有个空格隔开 1px + 5
- 对于两个不同的单位的值之间的运算，运算结果的值取第一个值的单位
- 如果两个值之间只有一个值有单位，则运算结果就取该单位
## 4.0 rem适配方案
### 4.1 rem适配方案

<br />1. 我们适配的目标是什么？<br />2. 怎么去达到这个目标的？<br />3. 在实际的开发当中使用？

1.让一些不能等比自适应的元素，达到当设备尺寸发生改变的时候，等比例适配当前设备。<br />2.使用媒体查询根据不同设备按比例设置html的字体大小，然后页面元素使用rem做尺寸单位，当html字体大小变化元素尺寸也会发生变化，从而达到等比缩放的适配。
### 4.2 rem 实际开发适配方案
**<br />① 按照设计稿与设备宽度的比例，动态计算并设置 html 根标签的 font-size 大小；（媒体查询）<br />② CSS 中，设计稿元素的宽、高、相对位置等取值，按照同等比例换算为 rem 为单位的值；<br />![淘宝.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1598541024141-c1e74aab-9fff-4b8d-9a2f-f163983cde2f.png#align=left&display=inline&height=408&margin=%5Bobject%20Object%5D&name=%E6%B7%98%E5%AE%9D.png&originHeight=408&originWidth=1056&size=482695&status=done&style=none&width=1056)
#### 技术方案：
① less+rem+媒体查询<br />② lflexible.js+rem<br />总结：<br />两种方案现在都存在。<br />方案2 更简单，现阶段大家无需了解里面的js代码。
#### rem实际开发适配方案1
![image.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1598541277934-d46009c7-fc36-4165-9b39-6ac05a1de896.png#align=left&display=inline&height=243&margin=%5Bobject%20Object%5D&name=image.png&originHeight=243&originWidth=884&size=35993&status=done&style=none&width=884)<br />一般情况下，我们以一套或两套效果图适应大部分的屏幕，放弃极端屏或对其优雅降级，牺牲一些效果<br />现在基本以750为准。
#### 动态设置 html 标签 font-size 大小
① 假设设计稿是750px<br />② 假设我们把整个屏幕划分为15等份（划分标准不一可以是20份也可以是10等份）<br />③ 每一份作为html字体大小，这里就是50px<br />④ 那么在320px设备的时候，字体大小为320/15就是  21.33px<br />⑤ 用我们页面元素的大小除以不同的 html字体大小会发现他们比例还是相同的<br />⑥ 比如我们以750为标准设计稿<br />⑦ 一个100_100像素的页面元素在  750屏幕下，  就是 100/ 50  转换为rem  是  2rem_2rem  比例是1比1<br />⑧ 320屏幕下，  html字体大小为21.33   则 2rem=  42.66px  此时宽和高都是 42.66  但是宽和高的比例还是 1比1<br />⑨ 但是已经能实现不同屏幕下  页面元素盒子等比例缩放的效果
#### 元素大小取值方法
①最后的公式：页面元素的rem值 =  页面元素值（px） /  （屏幕宽度  /  划分的份数）<br />②屏幕宽度/划分的份数就是 htmlfont-size 的大小<br />③或者：页面元素的rem值 =  页面元素值（px） /  html font-size 字体大小
#### 
## 5.0 苏宁首页

<br />苏宁首页地址 ：[苏宁首页](m.suning.com)<br />![苏宁易购.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1598541464662-ddcdaef6-c327-4c6d-bffc-af3bba4eb37a.png#align=left&display=inline&height=708&margin=%5Bobject%20Object%5D&name=%E8%8B%8F%E5%AE%81%E6%98%93%E8%B4%AD.png&originHeight=708&originWidth=471&size=371097&status=done&style=none&width=471)
### 5.1 技术选型
方案：我们采取单独制作移动页面方案<br />技术：布局采取rem适配布局（less + rem  + 媒体查询）<br />设计图： 本设计图采用 750px 设计尺寸
### 5.2 搭建文件结构

<br />![5.jpg](https://cdn.nlark.com/yuque/0/2020/jpeg/1483858/1598538419371-aab1ddab-7d1d-4527-8528-76b99e3b9c14.jpeg#align=left&display=inline&height=263&margin=%5Bobject%20Object%5D&name=5.jpg&originHeight=263&originWidth=466&size=26817&status=done&style=none&width=466)<br />

### 5.3 设置视口标签以及引入初始化样式


```css
<meta name="viewport" content="width=device-width, user-scalable=no,
initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
<link rel="stylesheet" href="css/normalize.css">
```


### 5.4 设置公共common.less文件

- 新建common.less    设置好最常见的屏幕尺寸，利用媒体查询设置不同的html字体大小，因为除了首页其他页面也需要
- 我们关心的尺寸有 320px、360px、375px、384px、400px、414px、424px、480px、540px、720px、750px
- 划分的份数我们定为 15等份
- 因为我们pc端也可以打开我们苏宁移动端首页，我们默认html字体大小为 50px，注意这句话写到最上面
### 5.5 **新建index.less文件**
1. 新建index.less 这里面写首页的样式<br />2. 将刚才设置好的 common.less 引入到index.less里面 语法如下：
```css
// 在 index.less 中导入 common.less 文件
@import “common”
```
3. 生成index.css 引入到 index.html 里面
### 5.6 body样式
```css
body {
min-width: 320px;
width:15rem;
margin: 0 auto;
line-height: 1.5;
font-family: Arial,Helvetica;
background: #F2F2F2;
}
```
## 6.0 rem 适配方案2
### 6.1 简洁高效的rem适配方案flexible.js
手机淘宝团队出的简洁高效 移动端适配库<br />我们再也不需要在写不同屏幕的媒体查询，因为里面js做了处理<br />它的原理是把当前设备划分为10等份，但是不同设备下，比例还是一致的。<br />我们要做的，就是确定好我们当前设备的html 文字大小就可以了<br />比如当前设计稿是 750px， 那么我们只需要把 html 文字大小设置为 75px(750px / 10) 就可以<br />里面页面元素rem值： 页面元素的px 值 /  75<br />剩余的，让flexible.js来去算<br />github地址：[https://github.com/amfe/lib-flexible](https://link.jianshu.com/?t=https://github.com/amfe/lib-flexible)<br />总结：<br />因为flexible是默认将屏幕分为10等分<br />但是当屏幕大于750的时候希望不要再去重置html字体了<br />所以要自己通过媒体查询设置一下<br />并且要把权重提到最高<br />VSCode  px 转换rem 插件 cssrem<br />因为cssrem中css自动转化为rem是参照默认插件的16转换的所以需要自己配置<br />

### 6.2 VSCode px 转换rem 插件 cssrem
设置html字体大小基准值<br />1. 打开 设置 快捷键是 ctrl + 逗号<br />![image.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1598542305580-bfdb7ce4-baf0-4abd-9ae2-1ce582b5bc52.png#align=left&display=inline&height=479&margin=%5Bobject%20Object%5D&name=image.png&originHeight=479&originWidth=667&size=43187&status=done&style=none&width=667)<br />![6.jpg](https://cdn.nlark.com/yuque/0/2020/jpeg/1483858/1598538440294-745f0812-d0b7-4775-bf48-da6783cff5f0.jpeg#align=left&display=inline&height=536&margin=%5Bobject%20Object%5D&name=6.jpg&originHeight=536&originWidth=713&size=45113&status=done&style=none&width=713)<br />![7.jpg](https://cdn.nlark.com/yuque/0/2020/jpeg/1483858/1598538450458-cd0ee501-5baf-4b38-b8ca-17fe924b775e.jpeg#align=left&display=inline&height=544&margin=%5Bobject%20Object%5D&name=7.jpg&originHeight=544&originWidth=566&size=35944&status=done&style=none&width=566)
