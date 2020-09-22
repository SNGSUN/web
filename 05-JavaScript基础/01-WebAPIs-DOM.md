# 01-WebAPIs-DOM

<a name="2d169ff1"></a>
## 1. Web API介绍


<a name="4ac327ea"></a>
### 1.1 API的概念

<br />API（Application Programming Interface，应用程序编程接口）是一些预先定义的函数，目的是提供应用程序与开发人员基于某软件或硬件得以访问一组例程的能力，而又无需访问源码，无需理解其内部工作机制细节，只需直接调用使用即可。<br />
<br />![1550719355829.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600780592110-d606b950-dbe7-4c00-b108-247fdc382ace.png#align=left&display=inline&height=277&margin=%5Bobject%20Object%5D&name=1550719355829.png&originHeight=277&originWidth=731&size=160848&status=done&style=none&width=731)<br />

> 举例解释什么是API。
> 例如，
> 	C语言中有一个函数 fopen()可以打开硬盘上的文件，这个函数对于我们来说，就是一个C语言提供的打开文件的工具。
> 	javascript中有一个函数alert()可以在页面弹一个提示框，这个函数就是js提供的一个弹框工具。
> 这些工具（函数）由编程语言提供，内部的实现已经封装好了，我们只要学会灵活的使用这些工具即可。



<a name="7a0c2b8f"></a>
### 1.2 Web  API的概念

<br />	Web API 是浏览器提供的一套操作浏览器功能和页面元素的 API ( BOM 和 DOM )。<br />
<br />	现阶段我们主要针对于浏览器讲解常用的 API , 主要针对浏览器做交互效果。比如我们想要浏览器弹出一个警示框， 直接使用 alert(‘弹出’)<br />
<br />	MDN 详细 API : [https://developer.mozilla.org/zh-CN/docs/Web/API](https://developer.mozilla.org/zh-CN/docs/Web/API)<br />
<br />	因为 Web API 很多，所以我们将这个阶段称为 Web APIs。<br />
<br />	此处的 Web API 特指浏览器提供的一系列API(很多函数或对象方法)，即操作网页的一系列工具。例如：操作html标签、操作页面地址的方法。<br />

<a name="efbc4cf7"></a>
### 1.3 API 和 Web  API 总结


1. API 是为我们程序员提供的一个接口，帮助我们实现某种功能，我们会使用就可以了，不必纠结内部如何实现
2. Web API 主要是针对于浏览器提供的接口，主要针对于浏览器做交互效果。
3. Web API 一般都有输入和输出（函数的传参和返回值），Web API 很多都是方法（函数）
4. 学习 Web API 可以结合前面学习内置对象方法的思路学习



<a name="1da10594"></a>
## 2. DOM 介绍


<a name="c3641dc2"></a>
### 2.1 什么是DOM

<br />	文档对象模型（Document Object Model，简称DOM），是 [W3C](https://baike.baidu.com/item/W3C) 组织推荐的处理[可扩展标记语言](https://baike.baidu.com/item/%E5%8F%AF%E6%89%A9%E5%B1%95%E7%BD%AE%E6%A0%87%E8%AF%AD%E8%A8%80)（html或者xhtml）的标准[编程接口](https://baike.baidu.com/item/%E7%BC%96%E7%A8%8B%E6%8E%A5%E5%8F%A3)。<br />
<br />	W3C 已经定义了一系列的 DOM 接口，通过这些 DOM 接口可以改变网页的内容、结构和样式。<br />

> DOM是W3C组织制定的一套处理 html和xml文档的规范，所有的浏览器都遵循了这套标准。



<a name="af186c0e"></a>
### 2.2. DOM树

<br />![1550731974575.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600780630002-da9ed29d-3d63-4b5b-b9fe-a15051edcad1.png#align=left&display=inline&height=301&margin=%5Bobject%20Object%5D&name=1550731974575.png&originHeight=301&originWidth=522&size=31016&status=done&style=none&width=522)<br />
<br />DOM树 又称为文档树模型，把文档映射成树形结构，通过节点对象对其处理，处理的结果可以加入到当前的页面。<br />

- 文档：一个页面就是一个文档，DOM中使用document表示
- 节点：网页中的所有内容，在文档树中都是节点（标签、属性、文本、注释等），使用node表示
- 标签节点：网页中的所有标签，通常称为元素节点，又简称为“元素”，使用element表示


<br />![1550732362134.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600780653980-80c43c5d-a329-42ad-b053-80f73437a3d5.png#align=left&display=inline&height=44&margin=%5Bobject%20Object%5D&name=1550732362134.png&originHeight=44&originWidth=296&size=9325&status=done&style=none&width=296)<br />

<a name="8b6011c7"></a>
## 3. 获取元素

<br />为什么要获取页面元素？<br />
<br />例如：我们想要操作页面上的某部分(显示/隐藏，动画)，需要先获取到该部分对应的元素，再对其进行操作。<br />

<a name="8ed22d5f"></a>
### 3.1. 根据ID获取


```javascript
语法：document.getElementById(id)
作用：根据ID获取元素对象
参数：id值，区分大小写的字符串
返回值：元素对象 或 null
```

<br />**案例代码**<br />

```javascript
<body>
    <div id="time">2019-9-9</div>
    <script>
        // 因为我们文档页面从上往下加载，所以先得有标签 所以我们script写到标签的下面
        var timer = document.getElementById('time');
        console.log(timer);
        console.log(typeof timer);
        // console.dir 打印我们返回的元素对象 更好的查看里面的属性和方法
        console.dir(timer);
    </script>
</body>
```


<a name="706ecf90"></a>
### 3.2. 根据标签名获取元素


```
语法：document.getElementsByTagName('标签名') 或者 element.getElementsByTagName('标签名') 
作用：根据标签名获取元素对象
参数：标签名
返回值：元素对象集合（伪数组，数组元素是元素对象）
```

<br />**案例代码**<br />

```javascript
<body>
    <ul>
        <li>知否知否，应是等你好久11</li>
        <li>知否知否，应是等你好久22</li>
        <li>知否知否，应是等你好久33</li>
        <li>知否知否，应是等你好久44</li>
        <li>知否知否，应是等你好久55</li>
    </ul>
    <ul id="nav">
        <li>生僻字</li>
        <li>生僻字</li>
        <li>生僻字</li>
        <li>生僻字</li>
        <li>生僻字</li>
    </ul>
    <script>
        // 1.返回的是 获取过来元素对象的集合 以伪数组的形式存储的
        var lis = document.getElementsByTagName('li');
        console.log(lis);
        console.log(lis[0]);
        // 2. 我们想要依次打印里面的元素对象我们可以采取遍历的方式
        for (var i = 0; i < lis.length; i++) {
            console.log(lis[i]);
        }
        // 3. element.getElementsByTagName()  可以得到这个元素里面的某些标签
        var nav = document.getElementById('nav'); // 这个获得nav 元素
        var navLis = nav.getElementsByTagName('li');
        console.log(navLis);
    </script>
</body>
```

<br />![1550733441663.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600780733686-60fb388e-df54-4c33-be1b-0d7aa5685a13.png#align=left&display=inline&height=115&margin=%5Bobject%20Object%5D&name=1550733441663.png&originHeight=115&originWidth=566&size=6350&status=done&style=none&width=566)<br />
<br />注意：getElementsByTagName()获取到是动态集合，即：当页面增加了标签，这个集合中也就增加了元素。<br />

<a name="9d956458"></a>
### 3.3. H5新增获取元素方式

<br />![1550733518278.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600780742007-a57d64dc-355d-4a82-80ba-68fd4f84fa11.png#align=left&display=inline&height=200&margin=%5Bobject%20Object%5D&name=1550733518278.png&originHeight=200&originWidth=750&size=15178&status=done&style=none&width=750)<br />![1550733734425.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600780768711-fd90b236-e0e0-41a9-aacc-20be98fd391c.png#align=left&display=inline&height=83&margin=%5Bobject%20Object%5D&name=1550733734425.png&originHeight=83&originWidth=795&size=4595&status=done&style=none&width=795)<br />
<br />**案例代码**<br />

```javascript
<body>
    <div class="box">盒子1</div>
    <div class="box">盒子2</div>
    <div id="nav">
        <ul>
            <li>首页</li>
            <li>产品</li>
        </ul>
    </div>
    <script>
        // 1. getElementsByClassName 根据类名获得某些元素集合
        var boxs = document.getElementsByClassName('box');
        console.log(boxs);
        // 2. querySelector 返回指定选择器的第一个元素对象  切记 里面的选择器需要加符号 .box  #nav
        var firstBox = document.querySelector('.box');
        console.log(firstBox);
        var nav = document.querySelector('#nav');
        console.log(nav);
        var li = document.querySelector('li');
        console.log(li);
        // 3. querySelectorAll()返回指定选择器的所有元素对象集合
        var allBox = document.querySelectorAll('.box');
        console.log(allBox);
        var lis = document.querySelectorAll('li');
        console.log(lis);
    </script>
</body>
```


<a name="0a360e47"></a>
### 3.4 获取特殊元素（body，html）

<br />![1550733794816.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600780801286-bea4226f-9016-4df9-a475-a0549c2c2db7.png#align=left&display=inline&height=272&margin=%5Bobject%20Object%5D&name=1550733794816.png&originHeight=272&originWidth=748&size=12010&status=done&style=none&width=748)<br />

<a name="0e0577ee"></a>
## 4. 事件基础


<a name="0b54815f"></a>
### 4.1. 事件概述

<br />JavaScript 使我们有能力创建动态页面，而事件是可以被 JavaScript 侦测到的行为。<br />
<br />简单理解： **触发--- 响应机制**。<br />
<br />	网页中的每个元素都可以产生某些可以触发 JavaScript 的事件，例如，我们可以在用户点击某按钮时产生一个 事件，然后去执行某些操作。<br />

<a name="3496014b"></a>
### 4.2. 事件三要素


- 事件源（谁）：触发事件的元素
- 事件类型（什么事件）： 例如 click 点击事件
- 事件处理程序（做啥）：事件触发后要执行的代码(函数形式)，事件处理函数


<br />**案例代码**<br />

```javascript
<body>
    <button id="btn">唐伯虎</button>
    <script>
        // 点击一个按钮，弹出对话框
        // 1. 事件是有三部分组成  事件源  事件类型  事件处理程序   我们也称为事件三要素
        //(1) 事件源 事件被触发的对象   谁  按钮
        var btn = document.getElementById('btn');
        //(2) 事件类型  如何触发 什么事件 比如鼠标点击(onclick) 还是鼠标经过 还是键盘按下
        //(3) 事件处理程序  通过一个函数赋值的方式 完成
        btn.onclick = function() {
            alert('点秋香');
        }
    </script>
</body>
```


<a name="8dd7a79f"></a>
### 4.3. 执行事件的步骤

<br />![1550734387056.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600780836519-1012afd6-cd8f-4029-a587-cd62969c827b.png#align=left&display=inline&height=114&margin=%5Bobject%20Object%5D&name=1550734387056.png&originHeight=114&originWidth=660&size=6843&status=done&style=none&width=660)<br />
<br />**案例代码**<br />

```javascript
<body>
    <div>123</div>
    <script>
        // 执行事件步骤
        // 点击div 控制台输出 我被选中了
        // 1. 获取事件源
        var div = document.querySelector('div');
        // 2.绑定事件 注册事件
        // div.onclick 
        // 3.添加事件处理程序 
        div.onclick = function() {
            console.log('我被选中了');
        }
    </script>
</body>
```


<a name="81548a9f"></a>
### 4.4. 常见的鼠标事件

<br />![1550734506084.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600780855867-bdeede60-cd80-40cc-9e55-5b75f0df4900.png#align=left&display=inline&height=318&margin=%5Bobject%20Object%5D&name=1550734506084.png&originHeight=318&originWidth=714&size=59847&status=done&style=none&width=714)<br />

<a name="a6009b29"></a>
### 4.5. 分析事件三要素


- 下拉菜单三要素
- 关闭广告三要素



<a name="a3a31273"></a>
## 5. 操作元素

<br />	JavaScript的 DOM 操作可以改变网页内容、结构和样式，我们可以利用 DOM 操作元素来改变元素里面的内容、属性等。（注意：这些操作都是通过元素对象的属性实现的）<br />

<a name="59f55f03"></a>
### 5.1. 改变元素内容（获取或设置）
![1550735016756.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600780881534-3dff9944-08cf-47b4-9370-f8ce30e5c040.png#align=left&display=inline&height=200&margin=%5Bobject%20Object%5D&name=1550735016756.png&originHeight=200&originWidth=700&size=12055&status=done&style=none&width=700)<br />
<br />**innerText改变元素内容**<br />

```javascript
<body>
    <button>显示当前系统时间</button>
    <div>某个时间</div>
    <p>1123</p>
    <script>
        // 当我们点击了按钮，  div里面的文字会发生变化
        // 1. 获取元素 
        var btn = document.querySelector('button');
        var div = document.querySelector('div');
        // 2.注册事件
        btn.onclick = function() {
            // div.innerText = '2019-6-6';
            div.innerHTML = getDate();
        }
        function getDate() {
            var date = new Date();
            // 我们写一个 2019年 5月 1日 星期三
            var year = date.getFullYear();
            var month = date.getMonth() + 1;
            var dates = date.getDate();
            var arr = ['星期日', '星期一', '星期二', '星期三', '星期四', '星期五', '星期六'];
            var day = date.getDay();
            return '今天是：' + year + '年' + month + '月' + dates + '日 ' + arr[day];
        }
    </script>
</body>
```

<br />**innerText和innerHTML的区别**<br />

- 获取内容时的区别：


<br />	innerText会去除空格和换行，而innerHTML会保留空格和换行<br />

- 设置内容时的区别：


<br />	innerText不会识别html，而innerHTML会识别<br />
<br />**案例代码**<br />

```javascript
<body>
    <div></div>
    <p>
        我是文字
        <span>123</span>
    </p>
    <script>
        // innerText 和 innerHTML的区别 
        // 1. innerText 不识别html标签 非标准  去除空格和换行
        var div = document.querySelector('div');
        // div.innerText = '<strong>今天是：</strong> 2019';
        // 2. innerHTML 识别html标签 W3C标准 保留空格和换行的
        div.innerHTML = '<strong>今天是：</strong> 2019';
        // 这两个属性是可读写的  可以获取元素里面的内容
        var p = document.querySelector('p');
        console.log(p.innerText);
        console.log(p.innerHTML);
    </script>
</body>
```


<a name="50317f92"></a>
### 5.2. 常用元素的属性操作

<br />![1550735556297.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600780917226-b6bfebe1-f46d-4677-acf8-3edc3a69180e.png#align=left&display=inline&height=131&margin=%5Bobject%20Object%5D&name=1550735556297.png&originHeight=131&originWidth=687&size=4581&status=done&style=none&width=687)<br />
<br />**获取属性的值**<br />

> 元素对象.属性名


<br />**设置属性的值**<br />

> 元素对象.属性名 = 值


<br />**案例代码**<br />

```javascript
<body>
    <button id="ldh">刘德华</button>
    <button id="zxy">张学友</button> <br>
    <img src="images/ldh.jpg" alt="" title="刘德华">
    <script>
        // 修改元素属性  src
        // 1. 获取元素
        var ldh = document.getElementById('ldh');
        var zxy = document.getElementById('zxy');
        var img = document.querySelector('img');
        // 2. 注册事件  处理程序
        zxy.onclick = function() {
            img.src = 'images/zxy.jpg';
            img.title = '张学友思密达';
        }
        ldh.onclick = function() {
            img.src = 'images/ldh.jpg';
            img.title = '刘德华';
        }
    </script>
</body>
```


<a name="8b5ab643"></a>
### 1.5.3. 案例：分时问候

<br />![1550735858049.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600780956695-89435147-1550-44b6-b836-4ae1a91d1da4.png#align=left&display=inline&height=230&margin=%5Bobject%20Object%5D&name=1550735858049.png&originHeight=230&originWidth=673&size=16629&status=done&style=none&width=673)<br />
<br />![1550735877145.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600780974500-b477e5c3-be02-415e-9b7b-09bf28e6c396.png#align=left&display=inline&height=182&margin=%5Bobject%20Object%5D&name=1550735877145.png&originHeight=182&originWidth=666&size=18341&status=done&style=none&width=666)<br />

<a name="f7636d9f"></a>
### 5.4. 表单元素的属性操作

<br />![1550736039005.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600780998637-d4ddd7c0-233e-4243-bae9-fa2138ad1a37.png#align=left&display=inline&height=106&margin=%5Bobject%20Object%5D&name=1550736039005.png&originHeight=106&originWidth=702&size=5101&status=done&style=none&width=702)<br />
<br />**获取属性的值**<br />

> 元素对象.属性名


<br />**设置属性的值**<br />

> 元素对象.属性名 = 值
> 表单元素中有一些属性如：disabled、checked、selected，元素对象的这些属性的值是布尔型。


<br />**案例代码**<br />

```javascript
<body>
    <button>按钮</button>
    <input type="text" value="输入内容">
    <script>
        // 1. 获取元素
        var btn = document.querySelector('button');
        var input = document.querySelector('input');
        // 2. 注册事件 处理程序
        btn.onclick = function() {
            // 表单里面的值 文字内容是通过 value 来修改的
            input.value = '被点击了';
            // 如果想要某个表单被禁用 不能再点击 disabled  我们想要这个按钮 button禁用
            // btn.disabled = true;
            this.disabled = true;
            // this 指向的是事件函数的调用者 btn
        }
    </script>
</body>
```


<a name="8a75e46b"></a>
### 5.5. 案例：仿京东显示密码

<br />![1550736330331.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781022045-15f09181-afb7-49e8-80e4-51331a727bee.png#align=left&display=inline&height=343&margin=%5Bobject%20Object%5D&name=1550736330331.png&originHeight=343&originWidth=728&size=24332&status=done&style=none&width=728)<br />
<br />![1550736346822.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781043764-0d84d963-3b47-4945-bdde-2884bc138001.png#align=left&display=inline&height=185&margin=%5Bobject%20Object%5D&name=1550736346822.png&originHeight=185&originWidth=660&size=19943&status=done&style=none&width=660)<br />

<a name="5263da70"></a>
### 5.6. 样式属性操作

<br />我们可以通过 JS 修改元素的大小、颜色、位置等样式。<br />
<br />**常用方式**<br />![1550736488634.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781070407-0b2dbb14-a7b1-4665-a998-350d0a8a83cb.png#align=left&display=inline&height=88&margin=%5Bobject%20Object%5D&name=1550736488634.png&originHeight=88&originWidth=644&size=4994&status=done&style=none&width=644)
<a name="4f32bbe8"></a>
#### 方式1：通过操作style属性


> 元素对象的style属性也是一个对象！
> 元素对象.style.样式属性 = 值;


<br />![1550736620181.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781091155-3eff5212-607c-44ec-9a0c-83fbe539ab65.png#align=left&display=inline&height=135&margin=%5Bobject%20Object%5D&name=1550736620181.png&originHeight=135&originWidth=708&size=6977&status=done&style=none&width=708)<br />
<br />**案例代码**<br />

```javascript
<body>
    <div></div>
    <script>
        // 1. 获取元素
        var div = document.querySelector('div');
        // 2. 注册事件 处理程序
        div.onclick = function() {
            // div.style里面的属性 采取驼峰命名法 
            this.style.backgroundColor = 'purple';
            this.style.width = '250px';
        }
    </script>
</body>
```


<a name="3b6e5434"></a>
#### 案例：淘宝点击关闭二维码

<br />![1550736843659.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781112578-35ddc5d4-2804-4e23-887a-b9cd6cf57d7e.png#align=left&display=inline&height=272&margin=%5Bobject%20Object%5D&name=1550736843659.png&originHeight=272&originWidth=582&size=46178&status=done&style=none&width=582)<br />
<br />![1550736881832.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781131519-7f7c8cda-7ee5-43f7-beca-a5387aa96d40.png#align=left&display=inline&height=130&margin=%5Bobject%20Object%5D&name=1550736881832.png&originHeight=130&originWidth=667&size=11181&status=done&style=none&width=667)<br />

<a name="4e0eb8f3"></a>
#### 案例：循环精灵图背景

<br />![1550736940082.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781149751-16262d83-d35e-4890-bf83-4ab8e72a9041.png#align=left&display=inline&height=303&margin=%5Bobject%20Object%5D&name=1550736940082.png&originHeight=303&originWidth=658&size=28612&status=done&style=none&width=658)<br />![1550736956754.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781163197-36a155c3-bc42-4863-9dd2-1033049824bf.png#align=left&display=inline&height=179&margin=%5Bobject%20Object%5D&name=1550736956754.png&originHeight=179&originWidth=693&size=15846&status=done&style=none&width=693)<br />

<a name="56e21331"></a>
#### 案例：显示隐藏文本框内容
![1550737006593.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781194413-d3637cdf-71c0-4fa4-9ad0-87e40de317d4.png#align=left&display=inline&height=252&margin=%5Bobject%20Object%5D&name=1550737006593.png&originHeight=252&originWidth=708&size=24780&status=done&style=none&width=708)<br />![1550737019729.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781224220-1d3aa63f-c856-4c17-af2d-852e37f9714e.png#align=left&display=inline&height=159&margin=%5Bobject%20Object%5D&name=1550737019729.png&originHeight=159&originWidth=688&size=15200&status=done&style=none&width=688)<br />
<br />

<a name="e1cf21dc"></a>
#### 方式2：通过操作className属性


> 元素对象.className = 值;
> 因为class是关键字，所有使用className。

![1550737214510.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781238057-3dfec8c6-8324-40e9-b07a-11f89c735790.png#align=left&display=inline&height=135&margin=%5Bobject%20Object%5D&name=1550737214510.png&originHeight=135&originWidth=708&size=9091&status=done&style=none&width=708)<br />
<br />**案例代码**<br />

```javascript
<body>
    <div class="first">文本</div>
    <script>
        // 1. 使用 element.style 获得修改元素样式  如果样式比较少 或者 功能简单的情况下使用
        var test = document.querySelector('div');
        test.onclick = function() {
            // this.style.backgroundColor = 'purple';
            // this.style.color = '#fff';
            // this.style.fontSize = '25px';
            // this.style.marginTop = '100px';

            // 2. 我们可以通过 修改元素的className更改元素的样式 适合于样式较多或者功能复杂的情况
            // 3. 如果想要保留原先的类名，我们可以这么做 多类名选择器
            // this.className = 'change';
            this.className = 'first change';
        }
    </script>
</body>
```


<a name="41e22765"></a>
#### 案例：密码框格式提示错误信息
![1550737269546.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781268777-2b9b900f-27c0-43e0-8ab4-6045e99bd8a6.png#align=left&display=inline&height=223&margin=%5Bobject%20Object%5D&name=1550737269546.png&originHeight=223&originWidth=734&size=21728&status=done&style=none&width=734)<br />![1550737284218.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781282154-b4728be3-59cb-4e4b-8250-4fafae9fc355.png#align=left&display=inline&height=186&margin=%5Bobject%20Object%5D&name=1550737284218.png&originHeight=186&originWidth=704&size=19428&status=done&style=none&width=704)
<a name="028441e3"></a>
### 5.7. 排他思想

<br />如果有同一组元素，我们想要某一个元素实现某种样式， 需要用到循环的排他思想算法：<br />

1. 所有元素全部清除样式（干掉其他人）
2. 给当前元素设置样式 （留下我自己）
3. 注意顺序不能颠倒，首先干掉其他人，再设置自己

![1550914482628.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781337682-f2355062-617f-438e-9996-8de78ed0c57d.png#align=left&display=inline&height=67&margin=%5Bobject%20Object%5D&name=1550914482628.png&originHeight=67&originWidth=294&size=3964&status=done&style=none&width=294)
```javascript
    <button>按钮1</button>
    <button>按钮2</button>
    <button>按钮3</button>
    <button>按钮4</button>
    <button>按钮5</button>
    <script>
        // 1. 获取所有按钮元素
        var btns = document.getElementsByTagName('button');
        // btns得到的是伪数组  里面的每一个元素 btns[i]
        for (var i = 0; i < btns.length; i++) {
            btns[i].onclick = function() {
                // (1) 我们先把所有的按钮背景颜色去掉  干掉所有人
                for (var i = 0; i < btns.length; i++) {
                    btns[i].style.backgroundColor = '';
                }
                // (2) 然后才让当前的元素背景颜色为pink 留下我自己
                this.style.backgroundColor = 'pink';

            }
        }
    </script>
```


<a name="ee680ad7"></a>
#### 案例：百度换肤
![1550914640677.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781369840-2e912171-754c-487c-8099-46a5a69a1a3e.png#align=left&display=inline&height=256&margin=%5Bobject%20Object%5D&name=1550914640677.png&originHeight=256&originWidth=699&size=277047&status=done&style=none&width=699)<br />![1550914663042.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781407703-4e688176-0b88-4315-915c-4669dbaa3c75.png#align=left&display=inline&height=197&margin=%5Bobject%20Object%5D&name=1550914663042.png&originHeight=197&originWidth=725&size=17576&status=done&style=none&width=725)
```javascript
<body>
    <ul class="baidu">
        <li><img src="images/1.jpg"></li>
        <li><img src="images/2.jpg"></li>
        <li><img src="images/3.jpg"></li>
        <li><img src="images/4.jpg"></li>
    </ul>
    <script>
        // 1. 获取元素 
        var imgs = document.querySelector('.baidu').querySelectorAll('img');
        // console.log(imgs);
        // 2. 循环注册事件 
        for (var i = 0; i < imgs.length; i++) {
            imgs[i].onclick = function() {
                // this.src 就是我们点击图片的路径   images/2.jpg
                // console.log(this.src);
                // 把这个路径 this.src 给body 就可以了
                document.body.style.backgroundImage = 'url(' + this.src + ')';
            }
        }
    </script>
</body>
```


<a name="1a6e3797"></a>
#### 案例：表格隔行变色

<br />![1550914791881.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781425956-2558a05c-d11e-4a7a-9758-8ec3e12d0130.png#align=left&display=inline&height=153&margin=%5Bobject%20Object%5D&name=1550914791881.png&originHeight=153&originWidth=776&size=62583&status=done&style=none&width=776)<br />![1550914812202.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781443659-c1a7903d-9056-4058-8a1d-a13db662058e.png#align=left&display=inline&height=168&margin=%5Bobject%20Object%5D&name=1550914812202.png&originHeight=168&originWidth=733&size=15663&status=done&style=none&width=733)<br />

```javascript
    <script>
        // 1.获取元素 获取的是 tbody 里面所有的行
        var trs = document.querySelector('tbody').querySelectorAll('tr');
        // 2. 利用循环绑定注册事件
        for (var i = 0; i < trs.length; i++) {
            // 3. 鼠标经过事件 onmouseover
            trs[i].onmouseover = function() {
                    // console.log(11);
                    this.className = 'bg';
                }
                // 4. 鼠标离开事件 onmouseout
            trs[i].onmouseout = function() {
                this.className = '';
            }
        }
    </script>
```


<a name="250265e5"></a>
#### 案例：全选

<br />![1550914980274.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781458113-1f7844d2-6b3f-4d7c-b433-00e730c5c972.png#align=left&display=inline&height=260&margin=%5Bobject%20Object%5D&name=1550914980274.png&originHeight=260&originWidth=864&size=43769&status=done&style=none&width=864)<br />![1550915005393.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781470441-52a3c1aa-8603-4bb1-af18-49151d1d91eb.png#align=left&display=inline&height=179&margin=%5Bobject%20Object%5D&name=1550915005393.png&originHeight=179&originWidth=749&size=19772&status=done&style=none&width=749)<br />

```javascript
    <script>
        // 1. 全选和取消全选做法：  让下面所有复选框的checked属性（选中状态） 跟随 全选按钮即可
        // 获取元素
        
        var j_cbAll = document.getElementById('j_cbAll'); 
        var j_tbs = document.getElementById('j_tb').getElementsByTagName('input'); 
        // 全选按钮注册事件
        j_cbAll.onclick = function() {
                // this.checked 当前复选框的选中状态
                console.log(this.checked);
                for (var i = 0; i < j_tbs.length; i++) {
                    j_tbs[i].checked = this.checked;
                }
         }
         // 给所有的子复选框注册单击事件
        for (var i = 0; i < j_tbs.length; i++) {
            j_tbs[i].onclick = function() {
                // flag 控制全选按钮是否选中
                var flag = true;
                // 每次点击下面的复选框都要循环检查者4个小按钮是否全被选中
                for (var i = 0; i < j_tbs.length; i++) {
                    if (!j_tbs[i].checked) {
                        flag = false;
                        break; 
                    }
                }
                // 设置全选按钮的状态
                j_cbAll.checked = flag;
            }
        }
    </script>
```


<a name="40f6caff"></a>
### 5.8. 自定义属性操作


<a name="7adb0a43"></a>
#### 获取属性值

<br />![1550915376339.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781513484-4233925f-51da-40a4-b5d4-29f735f2a89a.png#align=left&display=inline&height=236&margin=%5Bobject%20Object%5D&name=1550915376339.png&originHeight=236&originWidth=742&size=13448&status=done&style=none&width=742)<br />

```javascript
    <div id="demo" index="1" class="nav"></div>
    <script>
        var div = document.querySelector('div');
        // 1. 获取元素的属性值
        // (1) element.属性
        console.log(div.id);
        //(2) element.getAttribute('属性')  get得到获取 attribute 属性的意思 我们程序员自己添加的属性我们称为自定义属性 index
        console.log(div.getAttribute('id'));
        console.log(div.getAttribute('index'));
	</script>
```


<a name="22e68e83"></a>
#### 设置属性值
![1550915445026.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781550382-d761ea8f-b1af-4fb6-940b-f3da815ae304.png#align=left&display=inline&height=279&margin=%5Bobject%20Object%5D&name=1550915445026.png&originHeight=279&originWidth=695&size=13844&status=done&style=none&width=695)<br />

```javascript
        // 2. 设置元素属性值
        // (1) element.属性= '值'
        div.id = 'test';
        div.className = 'navs';
        // (2) element.setAttribute('属性', '值');  主要针对于自定义属性
        div.setAttribute('index', 2);
        div.setAttribute('class', 'footer'); // class 特殊  这里面写的就是
```


<a name="2e5089e5"></a>
#### 移出属性
![1550915513137.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781559913-2a312877-9f49-4e02-86af-4a010a525a30.png#align=left&display=inline&height=50&margin=%5Bobject%20Object%5D&name=1550915513137.png&originHeight=50&originWidth=624&size=2020&status=done&style=none&width=624)<br />

```javascript
// class 不是className
// 3 移除属性 removeAttribute(属性)    
 div.removeAttribute('index');
```


<a name="c366fcaa"></a>
#### 案例：tab栏
![1550915567627.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781595462-e9264368-a66b-4e3e-af77-e04101d4c9bc.png#align=left&display=inline&height=272&margin=%5Bobject%20Object%5D&name=1550915567627.png&originHeight=272&originWidth=786&size=78888&status=done&style=none&width=786)<br />![1550915590707.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781603921-ca44b826-0a35-4956-80c9-5c89f1571cd7.png#align=left&display=inline&height=290&margin=%5Bobject%20Object%5D&name=1550915590707.png&originHeight=290&originWidth=744&size=32592&status=done&style=none&width=744)<br />
<br />

```javascript
    <script>
        // 获取元素
        var tab_list = document.querySelector('.tab_list');
        var lis = tab_list.querySelectorAll('li');
        var items = document.querySelectorAll('.item');
        // for循环，给选项卡绑定点击事件
        for (var i = 0; i < lis.length; i++) {
            // 开始给5个小li 设置索引号 
            lis[i].setAttribute('index', i);
            lis[i].onclick = function() {
                // 1. 上的模块选项卡，当前这一个底色会是红色，其余不变（排他思想）
                // 干掉所有人 其余的li清除 class 这个类
                for (var i = 0; i < lis.length; i++) {
                    lis[i].className = '';
                }
                // 留下我自己 
                this.className = 'current';
                // 2. 下面的显示内容模块
                var index = this.getAttribute('index');
                console.log(index);
                // 干掉所有人 让其余的item 这些div 隐藏
                for (var i = 0; i < items.length; i++) {
                    items[i].style.display = 'none';
                }
                // 留下我自己 让对应的item 显示出来
                items[index].style.display = 'block';
            }
        }
    </script>
```


<a name="77e356c9"></a>
### 5.9. H5自定义属性

<br />自定义属性目的：是为了保存并使用数据。有些数据可以保存到页面中而不用保存到数据库中。<br />自定义属性获取是通过getAttribute(‘属性’) 获取。<br />但是有些自定义属性很容易引起歧义，不容易判断是元素的内置属性还是自定义属性。<br />
<br />H5给我们新增了自定义属性：<br />![1550915798516.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781631863-b4c56926-61b6-4aa7-8f13-ed80b8492f8c.png#align=left&display=inline&height=196&margin=%5Bobject%20Object%5D&name=1550915798516.png&originHeight=196&originWidth=705&size=11235&status=done&style=none&width=705)<br />![1550915815571.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781657955-6ae10c31-9a7f-4a4f-b2d1-057551fa75f7.png#align=left&display=inline&height=125&margin=%5Bobject%20Object%5D&name=1550915815571.png&originHeight=125&originWidth=691&size=9793&status=done&style=none&width=691)<br />

```javascript
    <div getTime="20" data-index="2" data-list-name="andy"></div>
    <script>
        var div = document.querySelector('div');
        // console.log(div.getTime);
        console.log(div.getAttribute('getTime'));
        div.setAttribute('data-time', 20);
        console.log(div.getAttribute('data-index'));
        console.log(div.getAttribute('data-list-name'));
        // h5新增的获取自定义属性的方法 它只能获取data-开头的
        // dataset 是一个集合里面存放了所有以data开头的自定义属性
        console.log(div.dataset);
        console.log(div.dataset.index);
        console.log(div.dataset['index']);
        // 如果自定义属性里面有多个-链接的单词，我们获取的时候采取 驼峰命名法
        console.log(div.dataset.listName);
        console.log(div.dataset['listName']);
    </script>
```


<a name="2ab75590"></a>
## 6. 节点操作


<a name="86c1b922"></a>
### 6.1. 节点概述

<br />	网页中的所有内容都是节点（标签、属性、文本、注释等），在DOM 中，节点使用 node 来表示。<br />	HTML DOM 树中的所有节点均可通过 JavaScript 进行访问，所有 HTML 元素（节点）均可被修改，也可以创建或删除。<br />![1550970944363.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781693964-c08ef13b-4f1f-464e-8a7f-d0219695bae8.png#align=left&display=inline&height=236&margin=%5Bobject%20Object%5D&name=1550970944363.png&originHeight=236&originWidth=432&size=21504&status=done&style=none&width=432)<br />
<br />	一般地，节点至少拥有nodeType（节点类型）、nodeName（节点名称）和nodeValue（节点值）这三个基本属性。<br />![1550970986988.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781708863-17bade03-00f9-4052-9d65-579fca4d3236.png#align=left&display=inline&height=148&margin=%5Bobject%20Object%5D&name=1550970986988.png&originHeight=148&originWidth=666&size=9988&status=done&style=none&width=666)<br />

<a name="20fa2644"></a>
### 6.2. 节点层级

<br />	利用 DOM 树可以把节点划分为不同的层级关系，常见的是**父子兄层级关系**。<br />   ![1550971058781.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781729674-c9aa3691-7eed-40a1-a100-5b1c4ce49b4f.png#align=left&display=inline&height=237&margin=%5Bobject%20Object%5D&name=1550971058781.png&originHeight=237&originWidth=432&size=21662&status=done&style=none&width=432)<br />

<a name="c46fb302"></a>
### 6.3. 父级节点
![1550971196686.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781745112-1e3430d3-cf34-4c7b-bfb8-36e9bfa85c06.png#align=left&display=inline&height=155&margin=%5Bobject%20Object%5D&name=1550971196686.png&originHeight=155&originWidth=702&size=8687&status=done&style=none&width=702)<br />

```javascript
    <div class="demo">
        <div class="box">
            <span class="erweima">×</span>
        </div>
    </div>
    <script>
        // 1. 父节点 parentNode
        var erweima = document.querySelector('.erweima');
        // var box = document.querySelector('.box');
        // 得到的是离元素最近的父级节点(亲爸爸) 如果找不到父节点就返回为 null
        console.log(erweima.parentNode);
    </script>
```


<a name="f78dc2c6"></a>
### 6.4. 子节点

<br />**所有子节点**<br />![1550971263925.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781771792-f806229c-d4c1-4d54-a28f-041561f4f4e3.png#align=left&display=inline&height=174&margin=%5Bobject%20Object%5D&name=1550971263925.png&originHeight=174&originWidth=696&size=14859&status=done&style=none&width=696)<br />
<br />**子元素节点**<br />![1550971325828.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781783288-86e0a836-d7ae-4b4f-b6c2-872d8815a461.png#align=left&display=inline&height=167&margin=%5Bobject%20Object%5D&name=1550971325828.png&originHeight=167&originWidth=712&size=14360&status=done&style=none&width=712)<br />

```javascript
    <ul>
        <li>我是li</li>
        <li>我是li</li>
        <li>我是li</li>
        <li>我是li</li>
    </ul>
    <script>
        // DOM 提供的方法（API）获取
        var ul = document.querySelector('ul');
        var lis = ul.querySelectorAll('li');
        // 1. 子节点  childNodes 所有的子节点 包含 元素节点 文本节点等等
        console.log(ul.childNodes);
        console.log(ul.childNodes[0].nodeType);
        console.log(ul.childNodes[1].nodeType);
        // 2. children 获取所有的子元素节点 也是我们实际开发常用的
        console.log(ul.children);
    </script>
```

<br />**第1个子节点**<br />![1550973610223.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781812159-9dcc7acb-7470-44ec-be58-b3e4c70d7764.png#align=left&display=inline&height=91&margin=%5Bobject%20Object%5D&name=1550973610223.png&originHeight=91&originWidth=700&size=5704&status=done&style=none&width=700)<br />
<br />**最后1个子节点**<br />
<br />![1550971825493.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781823975-a5297e93-321c-4110-9273-5e892099713a.png#align=left&display=inline&height=104&margin=%5Bobject%20Object%5D&name=1550971825493.png&originHeight=104&originWidth=693&size=6289&status=done&style=none&width=693)<br />**第1个子元素节点**<br />![1550972014509.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781837146-918c253c-8ff7-43fa-9d02-7ca0bad44b39.png#align=left&display=inline&height=89&margin=%5Bobject%20Object%5D&name=1550972014509.png&originHeight=89&originWidth=694&size=5898&status=done&style=none&width=694)<br />
<br />**最后1个子元素节点**<br />![1550972106485.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781845430-2198b70c-f1be-4af0-a001-36ab941ed169.png#align=left&display=inline&height=143&margin=%5Bobject%20Object%5D&name=1550972106485.png&originHeight=143&originWidth=697&size=8907&status=done&style=none&width=697)<br />
<br />	实际开发中，firstChild 和 lastChild 包含其他节点，操作不方便，而 firstElementChild 和 lastElementChild 又有兼容性问题，那么我们如何获取第一个子元素节点或最后一个子元素节点呢？<br />![1550972648014.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781887701-8972f851-57ae-4322-ab63-aae53b591def.png#align=left&display=inline&height=119&margin=%5Bobject%20Object%5D&name=1550972648014.png&originHeight=119&originWidth=760&size=7625&status=done&style=none&width=760)<br />

```javascript
    <ol>
        <li>我是li1</li>
        <li>我是li2</li>
        <li>我是li3</li>
        <li>我是li4</li>
        <li>我是li5</li>
    </ol>
    <script>
        var ol = document.querySelector('ol');
        // 1. firstChild 第一个子节点 不管是文本节点还是元素节点
        console.log(ol.firstChild);
        console.log(ol.lastChild);
        // 2. firstElementChild 返回第一个子元素节点 ie9才支持
        console.log(ol.firstElementChild);
        console.log(ol.lastElementChild);
        // 3. 实际开发的写法  既没有兼容性问题又返回第一个子元素
        console.log(ol.children[0]);
        console.log(ol.children[ol.children.length - 1]);
    </script>
```


<a name="1453d6dd"></a>
### 6.5. 案例：新浪下拉菜单
![1550974934894.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781924211-d9e40dba-ac3c-46d8-8e4d-1d24b405e92c.png#align=left&display=inline&height=222&margin=%5Bobject%20Object%5D&name=1550974934894.png&originHeight=222&originWidth=362&size=63449&status=done&style=none&width=362)<br />
<br />![1550975025608.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781938163-bafc2e95-78f0-47b4-b6b3-4ae39f285788.png#align=left&display=inline&height=137&margin=%5Bobject%20Object%5D&name=1550975025608.png&originHeight=137&originWidth=724&size=11718&status=done&style=none&width=724)<br />![1550975049176.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600781955945-ac507e79-5660-40d8-b2fa-f0d9c07a4787.png#align=left&display=inline&height=58&margin=%5Bobject%20Object%5D&name=1550975049176.png&originHeight=58&originWidth=714&size=3512&status=done&style=none&width=714)
```javascript
    <script>
        // 1. 获取元素
        var nav = document.querySelector('.nav');
        var lis = nav.children; // 得到4个小li
        // 2.循环注册事件
        for (var i = 0; i < lis.length; i++) {
            lis[i].onmouseover = function() {
                this.children[1].style.display = 'block';
            }
            lis[i].onmouseout = function() {
                this.children[1].style.display = 'none';
            }
        }
    </script>
```


<a name="90c9bfc9"></a>
### 6.6. 兄弟节点

<br />**下一个兄弟节点**<br />
<br />![1550973538696.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600782084169-83b6c263-c797-4ab7-87b8-8f0468d4a1a9.png#align=left&display=inline&height=100&margin=%5Bobject%20Object%5D&name=1550973538696.png&originHeight=100&originWidth=707&size=5779&status=done&style=none&width=707)<br />
<br />**上一个兄弟节点**<br />
<br />![1550973558511.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600782102240-f35a9b6b-7c94-497f-b932-4889e6eaaa53.png#align=left&display=inline&height=96&margin=%5Bobject%20Object%5D&name=1550973558511.png&originHeight=96&originWidth=705&size=6056&status=done&style=none&width=705)<br />

```javascript
    <div>我是div</div>
    <span>我是span</span>
    <script>
        var div = document.querySelector('div');
        // 1.nextSibling 下一个兄弟节点 包含元素节点或者 文本节点等等
        console.log(div.nextSibling);
        console.log(div.previousSibling);
        // 2. nextElementSibling 得到下一个兄弟元素节点
        console.log(div.nextElementSibling);
        console.log(div.previousElementSibling);
    </script>
```

<br />**下一个兄弟元素节点（有兼容性问题）**<br />
<br />![1550973610223.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600782129139-eecb9ae1-94b1-4ea9-a6df-ce96eb321824.png#align=left&display=inline&height=91&margin=%5Bobject%20Object%5D&name=1550973610223.png&originHeight=91&originWidth=700&size=5704&status=done&style=none&width=700)<br />
<br />**上一个兄弟元素节点（有兼容性问题）**<br />
<br />![1550973630150.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600782163948-29c0be76-3037-4cc4-8ff0-73f5fdff0d06.png#align=left&display=inline&height=100&margin=%5Bobject%20Object%5D&name=1550973630150.png&originHeight=100&originWidth=703&size=6235&status=done&style=none&width=703)<br />![1550973722805.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600782186693-06db20f3-b4ec-4736-bbac-259cc797cbe7.png#align=left&display=inline&height=40&margin=%5Bobject%20Object%5D&name=1550973722805.png&originHeight=40&originWidth=702&size=3502&status=done&style=none&width=702)<br />![1550973799759.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600782205826-3aabe09a-a019-4c84-87aa-fceec4d4b42e.png#align=left&display=inline&height=68&margin=%5Bobject%20Object%5D&name=1550973799759.png&originHeight=68&originWidth=684&size=4335&status=done&style=none&width=684)<br />

```javascript
   function getNextElementSibling(element) {
      var el = element;
      while (el = el.nextSibling) {
        if (el.nodeType === 1) {
            return el;
        }
      }
      return null;
    }
```


<a name="13962172"></a>
### 6.7. 创建节点

<br />![1550975514321.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600782223492-2bbf90aa-8858-458c-978a-d93a9544f048.png#align=left&display=inline&height=139&margin=%5Bobject%20Object%5D&name=1550975514321.png&originHeight=139&originWidth=709&size=11563&status=done&style=none&width=709)
<a name="9e377fdd"></a>
### 6.8. 添加节点
![1550975640170.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600782229925-8ed7fa25-1e33-40eb-95c0-556e81369d61.png#align=left&display=inline&height=266&margin=%5Bobject%20Object%5D&name=1550975640170.png&originHeight=266&originWidth=732&size=16705&status=done&style=none&width=732)<br />

```javascript
    <ul>
        <li>123</li>
    </ul>
    <script>
        // 1. 创建节点元素节点
        var li = document.createElement('li');
        // 2. 添加节点 node.appendChild(child)  node 父级  child 是子级 后面追加元素
        var ul = document.querySelector('ul');
        ul.appendChild(li);
        // 3. 添加节点 node.insertBefore(child, 指定元素);
        var lili = document.createElement('li');
        ul.insertBefore(lili, ul.children[0]);
        // 4. 我们想要页面添加一个新的元素 ： 1. 创建元素 2. 添加元素
    </script>
```


<a name="330e9613"></a>
### 6.9. 案例：简单版发布留言

<br />![1550975849302.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600782248439-25a88f97-d7bb-4ea7-9b2d-efcd7e0023d6.png#align=left&display=inline&height=152&margin=%5Bobject%20Object%5D&name=1550975849302.png&originHeight=152&originWidth=337&size=4575&status=done&style=none&width=337)<br />

```javascript
<body>
    <textarea name="" id=""></textarea>
    <button>发布</button>
    <ul>

    </ul>
    <script>
        // 1. 获取元素
        var btn = document.querySelector('button');
        var text = document.querySelector('textarea');
        var ul = document.querySelector('ul');
        // 2. 注册事件
        btn.onclick = function() {
            if (text.value == '') {
                alert('您没有输入内容');
                return false;
            } else {
                // console.log(text.value);
                // (1) 创建元素
                var li = document.createElement('li');
                // 先有li 才能赋值
                li.innerHTML = text.value;
                // (2) 添加元素
                // ul.appendChild(li);
                ul.insertBefore(li, ul.children[0]);
            }
        }
    </script>
</body>
```


<a name="123cef3c"></a>
### 6.10. 删除节点
![1551163384254(1).png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600782292251-f35e5232-d42a-450c-ab88-02587cb3b9ab.png#align=left&display=inline&height=58&margin=%5Bobject%20Object%5D&name=1551163384254%281%29.png&originHeight=58&originWidth=699&size=1709&status=done&style=none&width=699)<br />
<br />node.removeChild() 方法从 node节点中删除一个子节点，返回删除的节点。<br />

```javascript
    <button>删除</button>
    <ul>
        <li>熊大</li>
        <li>熊二</li>
        <li>光头强</li>
    </ul>
    <script>
        // 1.获取元素
        var ul = document.querySelector('ul');
        var btn = document.querySelector('button');
        // 2. 删除元素  node.removeChild(child)
        // ul.removeChild(ul.children[0]);
        // 3. 点击按钮依次删除里面的孩子
        btn.onclick = function() {
            if (ul.children.length == 0) {
                this.disabled = true;
            } else {
                ul.removeChild(ul.children[0]);
            }
        }
    </script>
```


<a name="08d1da49"></a>
### 6.11. 案例：删除留言

<br />![1551163586475.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600782304739-853a7f40-0a5d-4d48-a964-6dae119deeac.png#align=left&display=inline&height=210&margin=%5Bobject%20Object%5D&name=1551163586475.png&originHeight=210&originWidth=361&size=12786&status=done&style=none&width=361)<br />![1551163635501.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600782339964-2fbee4ff-b661-4d1c-89d0-f133a985cc83.png#align=left&display=inline&height=155&margin=%5Bobject%20Object%5D&name=1551163635501.png&originHeight=155&originWidth=718&size=16513&status=done&style=none&width=718)<br />

```javascript
    <textarea name="" id=""></textarea>
    <button>发布</button>
    <ul>

    </ul>
    <script>
        // 1. 获取元素
        var btn = document.querySelector('button');
        var text = document.querySelector('textarea');
        var ul = document.querySelector('ul');
        // 2. 注册事件
        btn.onclick = function() {
            if (text.value == '') {
                alert('您没有输入内容');
                return false;
            } else {
                // console.log(text.value);
                // (1) 创建元素
                var li = document.createElement('li');
                // 先有li 才能赋值
                li.innerHTML = text.value + "<a href='javascript:;'>删除</a>";
                // (2) 添加元素
                // ul.appendChild(li);
                ul.insertBefore(li, ul.children[0]);
                // (3) 删除元素 删除的是当前链接的li  它的父亲
                var as = document.querySelectorAll('a');
                for (var i = 0; i < as.length; i++) {
                    as[i].onclick = function() {
                        // 删除的是 li 当前a所在的li  this.parentNode;
                        ul.removeChild(this.parentNode);
                    }
                }
            }
        }
    </script>
```


<a name="4653895d"></a>
### 6.12. 复制（克隆）节点
![1551163763825.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600782348157-9bdeae0b-d3b1-4cba-b169-5ddc86e27d06.png#align=left&display=inline&height=248&margin=%5Bobject%20Object%5D&name=1551163763825.png&originHeight=248&originWidth=726&size=17428&status=done&style=none&width=726)<br />

```javascript
    <ul>
        <li>1111</li>
        <li>2</li>
        <li>3</li>
    </ul>
    <script>
        var ul = document.querySelector('ul');
        // 1. node.cloneNode(); 括号为空或者里面是false 浅拷贝 只复制标签不复制里面的内容
        // 2. node.cloneNode(true); 括号为true 深拷贝 复制标签复制里面的内容
        var lili = ul.children[0].cloneNode(true);
        ul.appendChild(lili);
    </script>
```


<a name="92df66e6"></a>
### 6.13. 案例：动态生成表格
![1551163900675.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600782364885-36ef8d85-15db-41dd-8643-a53280f1030c.png#align=left&display=inline&height=268&margin=%5Bobject%20Object%5D&name=1551163900675.png&originHeight=268&originWidth=718&size=44314&status=done&style=none&width=718)<br />
<br />

```javascript
    <script>
        // 1.先去准备好学生的数据
        var datas = [{
            name: '魏璎珞',
            subject: 'JavaScript',
            score: 100
        }, {
            name: '弘历',
            subject: 'JavaScript',
            score: 98
        }, {
            name: '傅恒',
            subject: 'JavaScript',
            score: 99
        }, {
            name: '明玉',
            subject: 'JavaScript',
            score: 88
        }, {
            name: '大猪蹄子',
            subject: 'JavaScript',
            score: 0
        }];
        // 2. 往tbody 里面创建行： 有几个人（通过数组的长度）我们就创建几行
        var tbody = document.querySelector('tbody');
		// 遍历数组
        for (var i = 0; i < datas.length; i++) { 
            // 1. 创建 tr行
            var tr = document.createElement('tr');
            tbody.appendChild(tr);
            // 2. 行里面创建单元格td 单元格的数量取决于每个对象里面的属性个数  
            // 使用for in遍历学生对象
            for (var k in datas[i]) { 
                // 创建单元格 
                var td = document.createElement('td');
                // 把对象里面的属性值 datas[i][k] 给 td  
                td.innerHTML = datas[i][k];
                tr.appendChild(td);
            }
            // 3. 创建有删除2个字的单元格 
            var td = document.createElement('td');
            td.innerHTML = '<a href="javascript:;">删除 </a>';
            tr.appendChild(td);

        }
        // 4. 删除操作 开始 
        var as = document.querySelectorAll('a');
        for (var i = 0; i < as.length; i++) {
            as[i].onclick = function() {
                // 点击a 删除 当前a 所在的行(链接的爸爸的爸爸)  node.removeChild(child)  
                tbody.removeChild(this.parentNode.parentNode)
            }
        }
    </script>
```


<a name="4f632014"></a>
### 6.14. 创建元素的三种方式
![1551164214925.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600782415551-c5979ee1-ab24-4ce0-9212-d04485d8f3b0.png#align=left&display=inline&height=346&margin=%5Bobject%20Object%5D&name=1551164214925.png&originHeight=346&originWidth=759&size=28273&status=done&style=none&width=759)<br />

```javascript
    <script>
        // 三种创建元素方式区别 
        // 1. document.write() 创建元素  如果页面文档流加载完毕，再调用这句话会导致页面重绘
         var btn = document.querySelector('button');
         btn.onclick = function() {
             document.write('<div>123</div>');
         }

        // 2. innerHTML 创建元素
        var inner = document.querySelector('.inner');
         for (var i = 0; i <= 100; i++) {
             inner.innerHTML += '<a href="#">百度</a>'
         }
        var arr = [];
        for (var i = 0; i <= 100; i++) {
            arr.push('<a href="#">百度</a>');
        }
        inner.innerHTML = arr.join('');
        // 3. document.createElement() 创建元素
        var create = document.querySelector('.create');
        for (var i = 0; i <= 100; i++) {
            var a = document.createElement('a');
            create.appendChild(a);
        }
    </script>
```


<a name="ec817116"></a>
### 6.15. innerTHML和createElement效率对比

<br />**innerHTML字符串拼接方式（效率低）**<br />

```javascript
<script>
    function fn() {
        var d1 = +new Date();
        var str = '';
        for (var i = 0; i < 1000; i++) {
            document.body.innerHTML += '<div style="width:100px; height:2px; border:1px solid blue;"></div>';
        }
        var d2 = +new Date();
        console.log(d2 - d1);
    }
    fn();
</script>
```

<br />**createElement方式（效率一般）**<br />

```javascript
<script>
    function fn() {
        var d1 = +new Date();

        for (var i = 0; i < 1000; i++) {
            var div = document.createElement('div');
            div.style.width = '100px';
            div.style.height = '2px';
            div.style.border = '1px solid red';
            document.body.appendChild(div);
        }
        var d2 = +new Date();
        console.log(d2 - d1);
    }
    fn();
</script>
```

<br />**innerHTML数组方式（效率高）**<br />

```javascript
<script>
    function fn() {
        var d1 = +new Date();
        var array = [];
        for (var i = 0; i < 1000; i++) {
            array.push('<div style="width:100px; height:2px; border:1px solid blue;"></div>');
        }
        document.body.innerHTML = array.join('');
        var d2 = +new Date();
        console.log(d2 - d1);
    }
    fn();
</script>
```


<a name="c589cccd"></a>
## 7. DOM的核心总结

<br />![1551164669434.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600782448099-0200d4b4-5659-458a-b3a8-18b4df3fbb35.png#align=left&display=inline&height=111&margin=%5Bobject%20Object%5D&name=1551164669434.png&originHeight=111&originWidth=681&size=13014&status=done&style=none&width=681)<br />![1551164715018.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600782543589-bf671fb3-73df-4c47-b18f-258e2e18bb5a.png#align=left&display=inline&height=296&margin=%5Bobject%20Object%5D&name=1551164715018.png&originHeight=296&originWidth=799&size=35359&status=done&style=none&width=799)<br />
<br />关于dom操作，我们主要针对于元素的操作。主要有创建、增、删、改、查、属性操作、事件操作。<br />

<a name="4d23fede"></a>
### 7.1. 创建
![1551164797164.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600782566617-e271f33d-78c9-4583-8427-26001b00fc4c.png#align=left&display=inline&height=115&margin=%5Bobject%20Object%5D&name=1551164797164.png&originHeight=115&originWidth=691&size=3357&status=done&style=none&width=691)
<a name="b1a66064"></a>
### 7.2. 增加
![1551164829832.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600782577148-8187e337-840b-4a59-bc23-001649ae9655.png#align=left&display=inline&height=85&margin=%5Bobject%20Object%5D&name=1551164829832.png&originHeight=85&originWidth=720&size=2188&status=done&style=none&width=720)
<a name="79447a62"></a>
### 7.3. 删
![1551164872533.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600782601349-c05b29b2-0cc6-49a0-a98e-8dcc6354c1e2.png#align=left&display=inline&height=49&margin=%5Bobject%20Object%5D&name=1551164872533.png&originHeight=49&originWidth=695&size=1216&status=done&style=none&width=695)
<a name="55680a1b"></a>
### 7.4. 改
![1551164907830.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600782621672-7b913de5-4b6e-4289-b867-926c659b51c2.png#align=left&display=inline&height=191&margin=%5Bobject%20Object%5D&name=1551164907830.png&originHeight=191&originWidth=731&size=13388&status=done&style=none&width=731)
<a name="27fa2009"></a>
### 7.5. 查
![1551164936214.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600782641560-ebec0e20-36a1-4290-8f06-0f10ab85fb60.png#align=left&display=inline&height=181&margin=%5Bobject%20Object%5D&name=1551164936214.png&originHeight=181&originWidth=703&size=14839&status=done&style=none&width=703)
<a name="105d18eb"></a>
### 1.7.6. 属性操作
![1551164985383.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600782662541-73033e62-677e-4624-9f75-df9e56073655.png#align=left&display=inline&height=157&margin=%5Bobject%20Object%5D&name=1551164985383.png&originHeight=157&originWidth=722&size=8338&status=done&style=none&width=722)<br />

<a name="74afdc15"></a>
### 7.7. 事件操作（重点）


<a name="d45d5e59"></a>
## 8. 事件高级


<a name="e5f6b657"></a>
### 8.1. 注册事件（2种方式）
![1551165252019.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600782721061-ada379a1-83ef-4ab8-a2a7-6e9793a439c0.png#align=left&display=inline&height=361&margin=%5Bobject%20Object%5D&name=1551165252019.png&originHeight=361&originWidth=867&size=33824&status=done&style=none&width=867)<br />

<a name="9b6788b0"></a>
### 8.2 事件监听


<a name="840e51a8"></a>
#### addEventListener()事件监听（IE9以后支持）
![1551165364122.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600782749125-6d1f67e3-3816-46e4-83e3-e4e9477ec6c0.png#align=left&display=inline&height=61&margin=%5Bobject%20Object%5D&name=1551165364122.png&originHeight=61&originWidth=707&size=2574&status=done&style=none&width=707)<br />
<br />eventTarget.addEventListener()方法将指定的监听器注册到 eventTarget（目标对象）上，当该对象触发指定的事件时，就会执行事件处理函数。<br />![1551165604792.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600782769732-decfaace-347f-476a-b2d1-3d8cebecc6c1.png#align=left&display=inline&height=145&margin=%5Bobject%20Object%5D&name=1551165604792.png&originHeight=145&originWidth=707&size=15166&status=done&style=none&width=707)
<a name="f64bb2ec"></a>
#### attacheEvent()事件监听（IE678支持）
![1551165781836.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600782806179-f3b974f8-77b4-4fe3-aa45-402bd6e16102.png#align=left&display=inline&height=52&margin=%5Bobject%20Object%5D&name=1551165781836.png&originHeight=52&originWidth=696&size=2438&status=done&style=none&width=696)<br />	eventTarget.attachEvent()方法将指定的监听器注册到 eventTarget（目标对象） 上，当该对象触发指定的事件时，指定的回调函数就会被执行。<br />![1551165843912.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600782834355-35f95595-9953-4f79-91f6-a6404f030a6e.png#align=left&display=inline&height=145&margin=%5Bobject%20Object%5D&name=1551165843912.png&originHeight=145&originWidth=657&size=12032&status=done&style=none&width=657)<br />

```javascript
<button>传统注册事件</button>
<button>方法监听注册事件</button>
<button>ie9 attachEvent</button>
<script>
    var btns = document.querySelectorAll('button');
    // 1. 传统方式注册事件
    btns[0].onclick = function() {
        alert('hi');
    }
    btns[0].onclick = function() {
            alert('hao a u');
        }
   // 2. 事件侦听注册事件 addEventListener 
   // (1) 里面的事件类型是字符串 必定加引号 而且不带on
   // (2) 同一个元素 同一个事件可以添加多个侦听器（事件处理程序）
    btns[1].addEventListener('click', function() {
        alert(22);
    })
    btns[1].addEventListener('click', function() {
            alert(33);
    })
    // 3. attachEvent ie9以前的版本支持
    btns[2].attachEvent('onclick', function() {
        alert(11);
    })
</script>
```


<a name="9fc5d5d8"></a>
#### 事件监听兼容性解决方案

<br />封装一个函数，函数中判断浏览器的类型：<br />![1551166023885.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600782861984-18c91b62-e1c0-47c9-a6ff-6695bb927285.png#align=left&display=inline&height=266&margin=%5Bobject%20Object%5D&name=1551166023885.png&originHeight=266&originWidth=643&size=14451&status=done&style=none&width=643)<br />

<a name="906caff4"></a>
### 8.3. 删除事件（解绑事件）
![1551166185410.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600782876458-ecf8341e-91f2-4eb9-9624-97bf0d01aa7d.png#align=left&display=inline&height=241&margin=%5Bobject%20Object%5D&name=1551166185410.png&originHeight=241&originWidth=737&size=11860&status=done&style=none&width=737)<br />

```javascript
    <div>1</div>
    <div>2</div>
    <div>3</div>
    <script>
        var divs = document.querySelectorAll('div');
        divs[0].onclick = function() {
            alert(11);
            // 1. 传统方式删除事件
            divs[0].onclick = null;
        }
        // 2. removeEventListener 删除事件
        divs[1].addEventListener('click', fn) // 里面的fn 不需要调用加小括号
        function fn() {
            alert(22);
            divs[1].removeEventListener('click', fn);
        }
        // 3. detachEvent
        divs[2].attachEvent('onclick', fn1);

        function fn1() {
            alert(33);
            divs[2].detachEvent('onclick', fn1);
        }
    </script>
```

<br />**删除事件兼容性解决方案 **<br />![1551166332453.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600782913813-51c3dc4b-31cb-46c3-b3a3-4895008da3f9.png#align=left&display=inline&height=269&margin=%5Bobject%20Object%5D&name=1551166332453.png&originHeight=269&originWidth=713&size=13650&status=done&style=none&width=713)<br />

<a name="b0307ab0"></a>
### 8.4. DOM事件流


> ```
html中的标签都是相互嵌套的，我们可以将元素想象成一个盒子装一个盒子，document是最外面的大盒子。
当你单击一个div时，同时你也单击了div的父元素，甚至整个页面。

那么是先执行父元素的单击事件，还是先执行div的单击事件 ？？？
```


<br />![1551166423144.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600782940438-1c65b4a7-20c8-4324-8a3a-1c2c5b21987b.png#align=left&display=inline&height=70&margin=%5Bobject%20Object%5D&name=1551166423144.png&originHeight=70&originWidth=696&size=8024&status=done&style=none&width=696)
> 比如：我们给页面中的一个div注册了单击事件，当你单击了div时，也就单击了body，单击了html，单击了document。

![1551166555833.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600782966824-81ad27fa-63d7-4463-8d5b-c8938828dc77.png#align=left&display=inline&height=196&margin=%5Bobject%20Object%5D&name=1551166555833.png&originHeight=196&originWidth=268&size=25905&status=done&style=none&width=268)<br />![1551166581552.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600783013534-f8430db4-7be3-4dff-81c5-c5c855e416a8.png#align=left&display=inline&height=72&margin=%5Bobject%20Object%5D&name=1551166581552.png&originHeight=72&originWidth=751&size=11105&status=done&style=none&width=751)
> ```
当时的2大浏览器霸主谁也不服谁！
IE 提出从目标元素开始，然后一层一层向外接收事件并响应，也就是冒泡型事件流。
Netscape（网景公司）提出从最外层开始，然后一层一层向内接收事件并响应，也就是捕获型事件流。

江湖纷争，武林盟主也脑壳疼！！！

最终，w3c 采用折中的方式，平息了战火，制定了统一的标准 —--— 先捕获再冒泡。
现代浏览器都遵循了此标准，所以当事件发生时，会经历3个阶段。
```


<br />DOM 事件流会经历3个阶段：<br />

1. 捕获阶段
2. 当前目标阶段
3. 冒泡阶段


<br />	我们向水里面扔一块石头，首先它会有一个下降的过程，这个过程就可以理解为从最顶层向事件发生的最具体元素（目标点）的捕获过程；之后会产生泡泡，会在最低点（ 最具体元素）之后漂浮到水面上，这个过程相当于事件冒泡。<br />![1551169007768.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600783046631-da40c585-f7d3-4ddd-ba48-4c7067543a1f.png#align=left&display=inline&height=271&margin=%5Bobject%20Object%5D&name=1551169007768.png&originHeight=271&originWidth=498&size=25051&status=done&style=none&width=498)

**事件冒泡**<br />

```javascript
    <div class="father">
        <div class="son">son盒子</div>
    </div>
    <script>
        // onclick 和 attachEvent（ie） 在冒泡阶段触发
        // 冒泡阶段 如果addEventListener 第三个参数是 false 或者 省略 
        // son -> father ->body -> html -> document
        var son = document.querySelector('.son');
		// 给son注册单击事件
        son.addEventListener('click', function() {
            alert('son');
        }, false);
		// 给father注册单击事件
        var father = document.querySelector('.father');
        father.addEventListener('click', function() {
            alert('father');
        }, false);
		// 给document注册单击事件，省略第3个参数
        document.addEventListener('click', function() {
            alert('document');
        })
    </script>
```

<br />**事件捕获**<br />

```javascript
    <div class="father">
        <div class="son">son盒子</div>
    </div>
    <script>
        // 如果addEventListener() 第三个参数是 true 那么在捕获阶段触发
        // document -> html -> body -> father -> son
         var son = document.querySelector('.son');
		// 给son注册单击事件，第3个参数为true
         son.addEventListener('click', function() {
             alert('son');
         }, true);
         var father = document.querySelector('.father');
		// 给father注册单击事件，第3个参数为true
         father.addEventListener('click', function() {
             alert('father');
         }, true);
		// 给document注册单击事件，第3个参数为true
        document.addEventListener('click', function() {
            alert('document');
        }, true)
    </script>
```


<a name="1256b82b"></a>
### 8.5. 事件对象


<a name="7b881ba4"></a>
#### 什么是事件对象

<br />事件发生后，跟事件相关的一系列信息数据的集合都放到这个对象里面，这个对象就是事件对象。<br />
<br />比如：<br />

1. 谁绑定了这个事件。
2. 鼠标触发事件的话，会得到鼠标的相关信息，如鼠标位置。
3. 键盘触发事件的话，会得到键盘的相关信息，如按了哪个键。



<a name="d86c2228"></a>
#### 事件对象的使用

<br />事件触发发生时就会产生事件对象，并且系统会以实参的形式传给事件处理函数。<br />
<br />所以，在事件处理函数中声明1个形参用来接收事件对象。<br />
<br />

<a name="42e679f9"></a>
#### 事件对象的兼容性处理

<br />事件对象本身的获取存在兼容问题：<br />

1. 标准浏览器中是浏览器给方法传递的参数，只需要定义形参 e 就可以获取到。
2. 在 IE6~8 中，浏览器不会给方法传递参数，如果需要的话，需要到 window.event 中获取查找。


<br />

```
只要“||”前面为false, 不管“||”后面是true 还是 false，都返回 “||” 后面的值。
只要“||”前面为true, 不管“||”后面是true 还是 false，都返回 “||” 前面的值。
```


```javascript
    <div>123</div>
    <script>
        var div = document.querySelector('div');
        div.onclick = function(e) {
                // 事件对象
                e = e || window.event;
                console.log(e);
        }
    </script>
```


<a name="f7a68b16"></a>
#### 事件对象的属性和方法

<br />

<a name="5db9703a"></a>
#### e.target 和 this 的区别


- this 是事件绑定的元素（绑定这个事件处理函数的元素） 。
- e.target 是事件触发的元素。



> ```
常情况下terget 和 this是一致的，
但有一种情况不同，那就是在事件冒泡时（父子元素有相同事件，单击子元素，父元素的事件处理函数也会被触发执行），
	这时候this指向的是父元素，因为它是绑定事件的元素对象，
	而target指向的是子元素，因为他是触发事件的那个具体元素对象。
```



```javascript
    <div>123</div>
    <script>
        var div = document.querySelector('div');
        div.addEventListener('click', function(e) {
            // e.target 和 this指向的都是div
            console.log(e.target);
            console.log(this);

        });
    </script>
```

<br />事件冒泡下的e.target和this<br />

```javascript
    <ul>
        <li>abc</li>
        <li>abc</li>
        <li>abc</li>
    </ul>
    <script>
        var ul = document.querySelector('ul');
        ul.addEventListener('click', function(e) {
              // 我们给ul 绑定了事件  那么this 就指向ul  
              console.log(this); // ul

              // e.target 触发了事件的对象 我们点击的是li e.target 指向的就是li
              console.log(e.target); // li
        });
    </script>
```


<a name="56325c21"></a>
### 8.6 阻止默认行为


> html中一些标签有默认行为，例如a标签被单击后，默认会进行页面跳转。



```javascript
    <a href="http://www.baidu.com">百度</a>
    <script>
        // 2. 阻止默认行为 让链接不跳转 
        var a = document.querySelector('a');
        a.addEventListener('click', function(e) {
             e.preventDefault(); //  dom 标准写法
        });
        // 3. 传统的注册方式
        a.onclick = function(e) {
            // 普通浏览器 e.preventDefault();  方法
            e.preventDefault();
            // 低版本浏览器 ie678  returnValue  属性
            e.returnValue = false;
            // 我们可以利用return false 也能阻止默认行为 没有兼容性问题
            return false;
        }
    </script>
```


<a name="b739bba2"></a>
### 8.7 阻止事件冒泡

<br />事件冒泡本身的特性，会带来的坏处，也会带来的好处。<br />
<br />

```javascript
    <div class="father">
        <div class="son">son儿子</div>
    </div>
    <script>
        var son = document.querySelector('.son');
		// 给son注册单击事件
        son.addEventListener('click', function(e) {
            alert('son');
            e.stopPropagation(); // stop 停止  Propagation 传播
            window.event.cancelBubble = true; // 非标准 cancel 取消 bubble 泡泡
        }, false);

        var father = document.querySelector('.father');
		// 给father注册单击事件
        father.addEventListener('click', function() {
            alert('father');
        }, false);
		// 给document注册单击事件
        document.addEventListener('click', function() {
            alert('document');
        })
    </script>
```

<br />**阻止事件冒泡的兼容性处理**<br />
<br />

<a name="023ff870"></a>
### 8.8 事件委托

<br />事件冒泡本身的特性，会带来的坏处，也会带来的好处。<br />

<a name="fd2d7888"></a>
#### 什么是事件委托


```
把事情委托给别人，代为处理。
```

<br />事件委托也称为事件代理，在 jQuery 里面称为事件委派。<br />

> 说白了就是，不给子元素注册事件，给父元素注册事件，把处理代码在父元素的事件中执行。


<br />**生活中的代理：**<br />
<br />
<br />**js事件中的代理：**<br />
<br />

<a name="15483017"></a>
#### 事件委托的原理

<br />	给父元素注册事件，利用事件冒泡，当子元素的事件触发，会冒泡到父元素，然后去控制相应的子元素。<br />

<a name="bde49ae6"></a>
#### 事件委托的作用


- 我们只操作了一次 DOM ，提高了程序的性能。
- 动态新创建的子元素，也拥有事件。



```javascript
    <ul>
        <li>知否知否，点我应有弹框在手！</li>
        <li>知否知否，点我应有弹框在手！</li>
        <li>知否知否，点我应有弹框在手！</li>
        <li>知否知否，点我应有弹框在手！</li>
        <li>知否知否，点我应有弹框在手！</li>
    </ul>
    <script>
        // 事件委托的核心原理：给父节点添加侦听器， 利用事件冒泡影响每一个子节点
        var ul = document.querySelector('ul');
        ul.addEventListener('click', function(e) {
            // e.target 这个可以得到我们点击的对象
            e.target.style.backgroundColor = 'pink';
        })
    </script>
```


<a name="7f889163"></a>
## 9. 常用鼠标事件

<br />

<a name="d1da23e8"></a>
### 9.1 案例：禁止选中文字和禁止右键菜单

<br />

```javascript
<body>
    我是一段不愿意分享的文字
    <script>
        // 1. contextmenu 我们可以禁用右键菜单
        document.addEventListener('contextmenu', function(e) {
                e.preventDefault();
        })
        // 2. 禁止选中文字 selectstart
        document.addEventListener('selectstart', function(e) {
            e.preventDefault();
        })
    </script>
</body>
```


<a name="32ea3d6e"></a>
### 9.2 鼠标事件对象

<br />

<a name="27dd997f"></a>
### 9.3 获取鼠标在页面的坐标


```javascript
    <script>
        // 鼠标事件对象 MouseEvent
        document.addEventListener('click', function(e) {
            // 1. client 鼠标在可视区的x和y坐标
            console.log(e.clientX);
            console.log(e.clientY);
            console.log('---------------------');

            // 2. page 鼠标在页面文档的x和y坐标
            console.log(e.pageX);
            console.log(e.pageY);
            console.log('---------------------');

            // 3. screen 鼠标在电脑屏幕的x和y坐标
            console.log(e.screenX);
            console.log(e.screenY);

        })
    </script>
```


<a name="f8881b51"></a>
### 9.4 案例：跟随鼠标的天使

<br />
<br />

```javascript
    <img src="images/angel.gif" alt="">
    <script>
        var pic = document.querySelector('img');
        document.addEventListener('mousemove', function(e) {
        	// 1. mousemove只要我们鼠标移动1px 就会触发这个事件
        	// 2.核心原理： 每次鼠标移动，我们都会获得最新的鼠标坐标， 
            // 把这个x和y坐标做为图片的top和left 值就可以移动图片
        	var x = e.pageX;
        	var y = e.pageY;
        	console.log('x坐标是' + x, 'y坐标是' + y);
        	//3 . 千万不要忘记给left 和top 添加px 单位
        	pic.style.left = x - 50 + 'px';
        	pic.style.top = y - 40 + 'px';
    	});
    </script>
```


<a name="9ab1095f"></a>
## 10. 常用的键盘事件


<a name="af8fbdb7"></a>
### 10.1 键盘事件

<br />
<br />

```javascript
    <script>
        // 常用的键盘事件
        //1. keyup 按键弹起的时候触发 
        document.addEventListener('keyup', function() {
            console.log('我弹起了');
        })

        //3. keypress 按键按下的时候触发  不能识别功能键 比如 ctrl shift 左右箭头啊
        document.addEventListener('keypress', function() {
                console.log('我按下了press');
        })
        //2. keydown 按键按下的时候触发  能识别功能键 比如 ctrl shift 左右箭头啊
        document.addEventListener('keydown', function() {
                console.log('我按下了down');
        })
        // 4. 三个事件的执行顺序  keydown -- keypress -- keyup
    </script>
```


<a name="4ef43b9c"></a>
### 10.2 键盘事件对象

<br />
<br />
<br />**使用keyCode属性判断用户按下哪个键**<br />

```javascript
    <script>
        // 键盘事件对象中的keyCode属性可以得到相应键的ASCII码值
        document.addEventListener('keyup', function(e) {
            console.log('up:' + e.keyCode);
            // 我们可以利用keycode返回的ASCII码值来判断用户按下了那个键
            if (e.keyCode === 65) {
                alert('您按下的a键');
            } else {
                alert('您没有按下a键')
            }
        })
        document.addEventListener('keypress', function(e) {
            // console.log(e);
            console.log('press:' + e.keyCode);
        })
    </script>
```


<a name="d58503fe"></a>
### 10.3 案例：模拟京东按键输入内容

<br />当我们按下 s 键， 光标就定位到搜索框（文本框获得焦点）。<br />
<br />

> 注意：触发获得焦点事件，可以使用 元素对象.focus()



```javascript
    <input type="text">
    <script>
        // 获取输入框
        var search = document.querySelector('input');
		// 给document注册keyup事件
        document.addEventListener('keyup', function(e) {
            // 判断keyCode的值
            if (e.keyCode === 83) {
                // 触发输入框的获得焦点事件
                search.focus();
            }
        })
    </script>
```


<a name="3ee447e4"></a>
### 10.4 案例：模拟京东快递单号查询

<br />要求：当我们在文本框中输入内容时，文本框上面自动显示大字号的内容。<br />
<br />
<br />

```javascript
    <div class="search">
        <div class="con">123</div>
        <input type="text" placeholder="请输入您的快递单号" class="jd">
    </div>
    <script>
        // 获取要操作的元素
        var con = document.querySelector('.con');
        var jd_input = document.querySelector('.jd');
		// 给输入框注册keyup事件
        jd_input.addEventListener('keyup', function() {
				// 判断输入框内容是否为空
                if (this.value == '') {
                    // 为空，隐藏放大提示盒子
                    con.style.display = 'none';
                } else {
                    // 不为空，显示放大提示盒子，设置盒子的内容
                    con.style.display = 'block';
                    con.innerText = this.value;
                }
            })
        // 给输入框注册失去焦点事件，隐藏放大提示盒子
        jd_input.addEventListener('blur', function() {
                con.style.display = 'none';
            })
        // 给输入框注册获得焦点事件
        jd_input.addEventListener('focus', function() {
            // 判断输入框内容是否为空
            if (this.value !== '') {
                // 不为空则显示提示盒子
                con.style.display = 'block';
            }
        })
    </script>
```
