# 02-WebAPIs-BOM

## 1. BOM


### 1.1. 什么是BOM


	BOM（Browser Object Model）即浏览器对象模型，它提供了独立于内容而与浏览器窗口进行交互的对象，其核心对象是 window。


	BOM 由一系列相关的对象构成，并且每个对象都提供了很多方法与属性。


	BOM 缺乏标准，JavaScript 语法的标准化组织是 ECMA，DOM 的标准化组织是 W3C，BOM 最初是Netscape 浏览器标准的一部分。
![1551319264407.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828192288-54156da2-ca47-4a58-af4b-da00dee5e651.png#align=left&display=inline&height=207&margin=%5Bobject%20Object%5D&name=1551319264407.png&originHeight=207&originWidth=866&size=22267&status=done&style=none&width=866)




### 1.2. BOM的构成


BOM 比 DOM 更大，它包含 DOM。


![1551319344183.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828199725-432fd906-95d7-45ac-8a91-4c7baf653b0c.png#align=left&display=inline&height=214&margin=%5Bobject%20Object%5D&name=1551319344183.png&originHeight=214&originWidth=629&size=24548&status=done&style=none&width=629)


### 1.3. 顶级对象window


![1551319372909.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828206398-a0af94d0-d18b-4a42-b644-284337af7bf2.png#align=left&display=inline&height=191&margin=%5Bobject%20Object%5D&name=1551319372909.png&originHeight=191&originWidth=725&size=19036&status=done&style=none&width=725)


### 1.4. window对象的常见事件


#### 页面（窗口）加载事件（2种）


**第1种**


![1551319525109.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828233698-0c0ba039-f9c2-4971-b0cd-f59af12677d8.png#align=left&display=inline&height=134&margin=%5Bobject%20Object%5D&name=1551319525109.png&originHeight=134&originWidth=697&size=5040&status=done&style=none&width=697)


window.onload 是窗口 (页面）加载事件，**当文档内容完全加载完成**会触发该事件(包括图像、脚本文件、CSS 文件等), 就调用的处理函数。


![1551319600263.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828260346-8e2f685d-af72-4171-b72d-b5fb9982c178.png#align=left&display=inline&height=175&margin=%5Bobject%20Object%5D&name=1551319600263.png&originHeight=175&originWidth=717&size=15095&status=done&style=none&width=717)


**第2种**


![1551319620299.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828272186-5edb39d5-9478-4793-be54-b349c810be3c.png#align=left&display=inline&height=84&margin=%5Bobject%20Object%5D&name=1551319620299.png&originHeight=84&originWidth=692&size=3036&status=done&style=none&width=692)


	DOMContentLoaded 事件触发时，仅当DOM加载完成，不包括样式表，图片，flash等等。


	IE9以上才支持！！！


	如果页面的图片很多的话, 从用户访问到onload触发可能需要较长的时间, 交互效果就不能实现，必然影响用户的体验，此时用 DOMContentLoaded 事件比较合适。


```javascript
    <script>
        window.addEventListener('load', function() {
            var btn = document.querySelector('button');
            btn.addEventListener('click', function() {
                alert('点击我');
            })
        })
        window.addEventListener('load', function() {
            alert(22);
        })
        document.addEventListener('DOMContentLoaded', function() {
            alert(33);
        })
    </script>
```


#### 调整窗口大小事件


![1551319803117.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828296822-5af96799-3037-49ed-8af0-2b8205ea81eb.png#align=left&display=inline&height=117&margin=%5Bobject%20Object%5D&name=1551319803117.png&originHeight=117&originWidth=698&size=4575&status=done&style=none&width=698)


	window.onresize 是调整窗口大小加载事件,  当触发时就调用的处理函数。


注意：


1. 只要窗口大小发生像素变化，就会触发这个事件。
2. 我们经常利用这个事件完成响应式布局。 window.innerWidth 当前屏幕的宽度



```javascript
    <script>
        // 注册页面加载事件
        window.addEventListener('load', function() {
            var div = document.querySelector('div');
        	// 注册调整窗口大小事件
            window.addEventListener('resize', function() {
                // window.innerWidth 获取窗口大小
                console.log('变化了');
                if (window.innerWidth <= 800) {
                    div.style.display = 'none';
                } else {
                    div.style.display = 'block';
                }
            })
        })
    </script>
    <div></div>
```


### 1.5. 定时器（两种）


window 对象给我们提供了 2 个非常好用的方法-定时器。


- setTimeout()
- setInterval()



#### setTimeout() 炸弹定时器


##### 开启定时器


![1551320279307.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828317491-a0446c1e-3ae0-4de3-adb9-28ce41dc3a22.png#align=left&display=inline&height=50&margin=%5Bobject%20Object%5D&name=1551320279307.png&originHeight=50&originWidth=695&size=3377&status=done&style=none&width=695)


![1551320408854.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828338603-7bdba0b4-797b-4d43-b856-0f0a654480a5.png#align=left&display=inline&height=31&margin=%5Bobject%20Object%5D&name=1551320408854.png&originHeight=31&originWidth=687&size=4095&status=done&style=none&width=687)![1551320298981.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828330538-241d577c-4199-43af-9144-680b9274d9d4.png#align=left&display=inline&height=183&margin=%5Bobject%20Object%5D&name=1551320298981.png&originHeight=183&originWidth=667&size=16165&status=done&style=none&width=667)




> ```
普通函数是按照代码顺序直接调用。

简单理解： 回调，就是回头调用的意思。上一件事干完，再回头再调用这个函数。
例如：定时器中的调用函数，事件处理函数，也是回调函数。

以前我们讲的   element.onclick = function(){}   或者  element.addEventListener(“click”, fn);   里面的 函数也是回调函数。
```



```javascript
    <script>
        // 回调函数是一个匿名函数
         setTimeout(function() {
             console.log('时间到了');

         }, 2000);
        function callback() {
            console.log('爆炸了');
        }
		// 回调函数是一个有名函数
        var timer1 = setTimeout(callback, 3000);
        var timer2 = setTimeout(callback, 5000);
    </script>
```


##### 案例：5秒后关闭广告


![1551320924828.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828454311-9678025e-05d8-4090-b728-0e9ef58cd74a.png#align=left&display=inline&height=247&margin=%5Bobject%20Object%5D&name=1551320924828.png&originHeight=247&originWidth=162&size=29240&status=done&style=none&width=162)
![1551320959756.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828462313-6aee4775-be45-40e6-b864-e13f3870da1a.png#align=left&display=inline&height=119&margin=%5Bobject%20Object%5D&name=1551320959756.png&originHeight=119&originWidth=699&size=8393&status=done&style=none&width=699)


```javascript
<body>
    <img src="images/ad.jpg" alt="" class="ad">
    <script>
        // 获取要操作的元素
        var ad = document.querySelector('.ad');
		// 开启定时器
        setTimeout(function() {
            ad.style.display = 'none';
        }, 5000);
    </script>
</body>
```


##### 停止定时器


![1551321051001.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828482711-28fd82ec-1117-4bf2-b9f6-7cb8eaf1d1a8.png#align=left&display=inline&height=51&margin=%5Bobject%20Object%5D&name=1551321051001.png&originHeight=51&originWidth=703&size=1961&status=done&style=none&width=703)
![1551321064154.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828492586-1b81791e-21d1-4b73-8e1d-fbae9d40cb18.png#align=left&display=inline&height=148&margin=%5Bobject%20Object%5D&name=1551321064154.png&originHeight=148&originWidth=682&size=8756&status=done&style=none&width=682)


```javascript
    <button>点击停止定时器</button>
    <script>
        var btn = document.querySelector('button');
		// 开启定时器
        var timer = setTimeout(function() {
            console.log('爆炸了');
        }, 5000);
		// 给按钮注册单击事件
        btn.addEventListener('click', function() {
            // 停止定时器
            clearTimeout(timer);
        })
    </script>
```


#### setInterval() 闹钟定时器


##### 开启定时器


![1551321162158.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828517227-78e20ce9-d2e7-4f0f-8d6b-c31b13e4f984.png#align=left&display=inline&height=335&margin=%5Bobject%20Object%5D&name=1551321162158.png&originHeight=335&originWidth=715&size=29505&status=done&style=none&width=715)


```javascript
    <script>
        // 1. setInterval 
        setInterval(function() {
            console.log('继续输出');
        }, 1000);
    </script>
```


##### 案例：倒计时
![1551321298787.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828541639-58e4426e-45e1-404b-83c7-286fc96cb572.png#align=left&display=inline&height=272&margin=%5Bobject%20Object%5D&name=1551321298787.png&originHeight=272&originWidth=190&size=19400&status=done&style=none&width=190)
![1551321322188.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828550142-0b94e275-1212-4a3d-adca-f181943a4a46.png#align=left&display=inline&height=199&margin=%5Bobject%20Object%5D&name=1551321322188.png&originHeight=199&originWidth=729&size=22710&status=done&style=none&width=729)


```javascript
    <div>
        <span class="hour">1</span>
        <span class="minute">2</span>
        <span class="second">3</span>
    </div>
    <script>
        // 1. 获取元素（时分秒盒子） 
        var hour = document.querySelector('.hour'); // 小时的黑色盒子
        var minute = document.querySelector('.minute'); // 分钟的黑色盒子
        var second = document.querySelector('.second'); // 秒数的黑色盒子
        var inputTime = +new Date('2019-5-1 18:00:00'); // 返回的是用户输入时间总的毫秒数

        countDown(); // 我们先调用一次这个函数，防止第一次刷新页面有空白 

        // 2. 开启定时器
        setInterval(countDown, 1000);
		
        function countDown() {
            var nowTime = +new Date(); // 返回的是当前时间总的毫秒数
            var times = (inputTime - nowTime) / 1000; // times是剩余时间总的秒数 
            var h = parseInt(times / 60 / 60 % 24); //时
            h = h < 10 ? '0' + h : h;
            hour.innerHTML = h; // 把剩余的小时给 小时黑色盒子
            var m = parseInt(times / 60 % 60); // 分
            m = m < 10 ? '0' + m : m;
            minute.innerHTML = m;
            var s = parseInt(times % 60); // 当前的秒
            s = s < 10 ? '0' + s : s;
            second.innerHTML = s;
        }
    </script>
```


##### 停止定时器
![1551321444559.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828572279-d1525570-8918-4f8c-a358-2285a10bc0d8.png#align=left&display=inline&height=209&margin=%5Bobject%20Object%5D&name=1551321444559.png&originHeight=209&originWidth=705&size=10752&status=done&style=none&width=705)


#### 案例：发送短信倒计时


	点击按钮后，该按钮60秒之内不能再次点击，防止重复发送短信。


![1551321540676.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828585272-5fff68bb-cd2f-4c4c-995d-2ecb741fb13c.png#align=left&display=inline&height=40&margin=%5Bobject%20Object%5D&name=1551321540676.png&originHeight=40&originWidth=364&size=1355&status=done&style=none&width=364)
![1551321564247.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828595520-512111c1-c8ae-4ddf-afb8-978c6927ad15.png#align=left&display=inline&height=212&margin=%5Bobject%20Object%5D&name=1551321564247.png&originHeight=212&originWidth=693&size=19909&status=done&style=none&width=693)


```javascript
    手机号码： <input type="number"> <button>发送</button>
    <script>
        var btn = document.querySelector('button');
		// 全局变量，定义剩下的秒数
        var time = 3; 
		// 注册单击事件
        btn.addEventListener('click', function() {
            // 禁用按钮
            btn.disabled = true;
            // 开启定时器
            var timer = setInterval(function() {
                // 判断剩余秒数
                if (time == 0) {
                    // 清除定时器和复原按钮
                    clearInterval(timer);
                    btn.disabled = false;
                    btn.innerHTML = '发送';
                } else {
                    btn.innerHTML = '还剩下' + time + '秒';
                    time--;
                }
            }, 1000);
        });
    </script>
```


### 1.6. this指向问题


	this的指向在函数定义的时候是确定不了的，只有函数执行的时候才能确定this到底指向谁，一般情况下this的最终指向的是那个调用它的对象。


现阶段，我们先了解一下几个this指向


1. 全局作用域或者普通函数中this指向全局对象window（注意定时器里面的this指向window）
2. 方法调用中谁调用this指向谁
3. 构造函数中this指向构造函数的实例



```javascript
    <button>点击</button>
    <script>
        // this 指向问题 一般情况下this的最终指向的是那个调用它的对象
        // 1. 全局作用域或者普通函数中this指向全局对象window（ 注意定时器里面的this指向window）
        console.log(this);
        function fn() {
            console.log(this);
        }
        window.fn();
        window.setTimeout(function() {
            console.log(this);
        }, 1000);
        // 2. 方法调用中谁调用this指向谁
        var o = {
            sayHi: function() {
                console.log(this); // this指向的是 o 这个对象
            }
        }
        o.sayHi();
        var btn = document.querySelector('button');
        btn.addEventListener('click', function() {
                console.log(this); // 事件处理函数中的this指向的是btn这个按钮对象
            })
        // 3. 构造函数中this指向构造函数的实例
        function Fun() {
            console.log(this); // this 指向的是fun 实例对象
        }
        var fun = new Fun();
    </script>
```


### 1.7. location对象


#### 什么是 location 对象


![1551322091638.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828630047-48938715-4333-4ab5-9527-a93b031fa9cb.png#align=left&display=inline&height=56&margin=%5Bobject%20Object%5D&name=1551322091638.png&originHeight=56&originWidth=722&size=10273&status=done&style=none&width=722)


#### URL


![1551322373704.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828640418-faf88d13-9632-4902-ad92-0651df681bcd.png#align=left&display=inline&height=177&margin=%5Bobject%20Object%5D&name=1551322373704.png&originHeight=177&originWidth=723&size=17872&status=done&style=none&width=723)
![1551322387201.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828649702-c7145a50-8023-4848-8ce0-e2e825c45dc0.png#align=left&display=inline&height=240&margin=%5Bobject%20Object%5D&name=1551322387201.png&originHeight=240&originWidth=684&size=71663&status=done&style=none&width=684)
#### location 对象的属性


![1551322416716.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828670660-dc5db65a-3b2b-4a39-8963-ac8b11cfc273.png#align=left&display=inline&height=240&margin=%5Bobject%20Object%5D&name=1551322416716.png&originHeight=240&originWidth=705&size=60708&status=done&style=none&width=705)
![1551322438200.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828681073-01e627f8-a4a9-4ba0-9fd2-67567df9c8cb.png#align=left&display=inline&height=37&margin=%5Bobject%20Object%5D&name=1551322438200.png&originHeight=37&originWidth=704&size=1418&status=done&style=none&width=704)


#### 案例：5分钟自动跳转页面


![1551322496871.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828699501-da53614b-5917-4101-8a4d-c6412a14c493.png#align=left&display=inline&height=59&margin=%5Bobject%20Object%5D&name=1551322496871.png&originHeight=59&originWidth=578&size=8837&status=done&style=none&width=578)
![1551322517605.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828709532-dae6fe62-e6b2-47e1-a85d-213a348e9ae0.png#align=left&display=inline&height=118&margin=%5Bobject%20Object%5D&name=1551322517605.png&originHeight=118&originWidth=709&size=8419&status=done&style=none&width=709)


```javascript
    <button>点击</button>
    <div></div>
    <script>
        var btn = document.querySelector('button');
        var div = document.querySelector('div');
        btn.addEventListener('click', function() {
            // console.log(location.href);
            location.href = 'http://www.itcast.cn';
        })
        var timer = 5;
        setInterval(function() {
            if (timer == 0) {
                location.href = 'http://www.itcast.cn';
            } else {
                div.innerHTML = '您将在' + timer + '秒钟之后跳转到首页';
                timer--;
            }
        }, 1000);
    </script>
```


#### 案例：获取URL参数


![1551322622640.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828739078-908f6372-433f-4ada-890c-79c9aa7f1127.png#align=left&display=inline&height=105&margin=%5Bobject%20Object%5D&name=1551322622640.png&originHeight=105&originWidth=637&size=19405&status=done&style=none&width=637)
![1551322639241.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828774627-8cd5fb52-ccb6-4b2f-8d22-4274be2fb308.png#align=left&display=inline&height=250&margin=%5Bobject%20Object%5D&name=1551322639241.png&originHeight=250&originWidth=721&size=23439&status=done&style=none&width=721)
```javascript
    <div></div>
	<script>
        console.log(location.search); // ?uname=andy
        // 1.先去掉？  substr('起始的位置'，截取几个字符);
        var params = location.search.substr(1); // uname=andy
        console.log(params);
        // 2. 利用=把字符串分割为数组 split('=');
        var arr = params.split('=');
        console.log(arr); // ["uname", "ANDY"]
        var div = document.querySelector('div');
        // 3.把数据写入div中
        div.innerHTML = arr[1] + '欢迎您';
    </script>
```


#### location对象的常见方法


![1551322750241.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828794470-21b6035a-306d-41b0-9871-83263573d64c.png#align=left&display=inline&height=153&margin=%5Bobject%20Object%5D&name=1551322750241.png&originHeight=153&originWidth=728&size=54822&status=done&style=none&width=728)


```javascript
    <button>点击</button>
    <script>
        var btn = document.querySelector('button');
        btn.addEventListener('click', function() {
            // 记录浏览历史，所以可以实现后退功能
            // location.assign('http://www.itcast.cn');
            // 不记录浏览历史，所以不可以实现后退功能
            // location.replace('http://www.itcast.cn');
            location.reload(true);
        })
    </script>
```


### 1.8. navigator对象


	navigator 对象包含有关浏览器的信息，它有很多属性，我们最常用的是 userAgent，该属性可以返回由客户机发送服务器的 user-agent 头部的值。


下面前端代码可以判断用户那个终端打开页面，实现跳转


```javascript
if((navigator.userAgent.match(/(phone|pad|pod|iPhone|iPod|ios|iPad|Android|Mobile|BlackBerry|IEMobile|MQQBrowser|JUC|Fennec|wOSBrowser|BrowserNG|WebOS|Symbian|Windows Phone)/i))) {
    window.location.href = "";     //手机
 } else {
    window.location.href = "";     //电脑
 }
```


### 1.9 history对象


	window对象给我们提供了一个 history对象，与浏览器历史记录进行交互。该对象包含用户（在浏览器窗口中）访问过的URL。


![1551322885216.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828816010-893dcde6-1c7e-40dc-aece-77a1ee0c25fd.png#align=left&display=inline&height=148&margin=%5Bobject%20Object%5D&name=1551322885216.png&originHeight=148&originWidth=731&size=31824&status=done&style=none&width=731)


history对象一般在实际开发中比较少用，但是会在一些 OA 办公系统中见到。


![1551322959148.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828836319-9516fe77-4d5f-42b0-9a54-baf0f4a4f4a0.png#align=left&display=inline&height=176&margin=%5Bobject%20Object%5D&name=1551322959148.png&originHeight=176&originWidth=705&size=52673&status=done&style=none&width=705)


## 2. JS执行机制


以下代码执行的结果是什么？


```javascript
 console.log(1);
 
 setTimeout(function () {
     console.log(3);
 }, 1000);
 
 console.log(2);
```


以下代码执行的结果是什么？


```javascript
 console.log(1);
 
 setTimeout(function () {
     console.log(3);
 }, 0);
 
 console.log(2);
```


### 2.1 JS 是单线程


![1551415019322.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828848758-5acef082-9a33-4fca-9fc8-20365860e4a2.png#align=left&display=inline&height=90&margin=%5Bobject%20Object%5D&name=1551415019322.png&originHeight=90&originWidth=726&size=15333&status=done&style=none&width=726)


```javascript
	单线程就意味着，所有任务需要排队，前一个任务结束，才会执行后一个任务。如果前一个任务耗时很长，后一个任务就不得不一直等着。
	这样所导致的问题是： 如果 JS 执行的时间过长，这样就会造成页面的渲染不连贯，导致页面渲染加载阻塞的感觉。
```


### 2.2 同步任务和异步任务


	单线程导致的问题就是后面的任务等待前面任务完成，如果前面任务很耗时（比如读取网络数据），后面任务不得不一直等待！！


	为了解决这个问题，利用多核 CPU 的计算能力，HTML5 提出 Web Worker 标准，允许 JavaScript 脚本创建多个线程，但是子线程完全受主线程控制。于是，JS 中出现了**同步任务**和**异步任务**。


#### 同步


	前一个任务结束后再执行后一个任务，程序的执行顺序与任务的排列顺序是一致的、同步的。比如做饭的同步做法：我们要烧水煮饭，等水开了（10分钟之后），再去切菜，炒菜。


#### 异步


	你在做一件事情时，因为这件事情会花费很长时间，在做这件事的同时，你还可以去处理其他事情。比如做饭的异步做法，我们在烧水的同时，利用这10分钟，去切菜，炒菜。


![1551434295074.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828879249-77518c92-0202-4912-ae67-2a519aa80587.png#align=left&display=inline&height=43&margin=%5Bobject%20Object%5D&name=1551434295074.png&originHeight=43&originWidth=686&size=3248&status=done&style=none&width=686)


> ```javascript
JS中所有任务可以分成两种，一种是同步任务（synchronous），另一种是异步任务（asynchronous）。

同步任务指的是：
	在主线程上排队执行的任务，只有前一个任务执行完毕，才能执行后一个任务；
异步任务指的是：
	不进入主线程、而进入”任务队列”的任务，当主线程中的任务运行完了，才会从”任务队列”取出异步任务放入主线程执行。
```



![1551434972778.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828911059-a0ffd02c-647f-46c3-b062-ea6955f80316.png#align=left&display=inline&height=432&margin=%5Bobject%20Object%5D&name=1551434972778.png&originHeight=432&originWidth=746&size=32510&status=done&style=none&width=746)


### 2.3 JS执行机制（事件循环）
![1551435335464.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828953176-4348c8aa-fc5b-4100-ad1a-81416d05410e.png#align=left&display=inline&height=390&margin=%5Bobject%20Object%5D&name=1551435335464.png&originHeight=390&originWidth=768&size=34470&status=done&style=none&width=768)
![1551435398306.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828966036-7e9a1b97-f2ee-41ba-b6b7-51834d5ce308.png#align=left&display=inline&height=379&margin=%5Bobject%20Object%5D&name=1551435398306.png&originHeight=379&originWidth=819&size=60097&status=done&style=none&width=819)
![1551435449634.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600828979372-0a557f99-e26b-467f-88fb-4689be4c642c.png#align=left&display=inline&height=44&margin=%5Bobject%20Object%5D&name=1551435449634.png&originHeight=44&originWidth=838&size=6366&status=done&style=none&width=838)
### 2.4 代码思考题


```javascript
 console.log(1);
 document.onclick = function() {
   console.log('click');
 }

 setTimeout(function() {
   console.log(3)
 }, 3000)
 console.log(2);
```


