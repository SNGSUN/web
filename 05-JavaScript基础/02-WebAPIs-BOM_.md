# 02-WebAPIs-BOM

<a name="16c1b309"></a>
## 1. BOM

<a name="bb12862d"></a>
### 1.1. 什么是BOM

​	BOM（Browser Object Model）即浏览器对象模型，它提供了独立于内容而与浏览器窗口进行交互的对象，其核心对象是 window。

​	BOM 由一系列相关的对象构成，并且每个对象都提供了很多方法与属性。

​	BOM 缺乏标准，JavaScript 语法的标准化组织是 ECMA，DOM 的标准化组织是 W3C，BOM 最初是Netscape 浏览器标准的一部分。

![](images/1551319264407.png#alt=1551319264407)

<a name="a354a44f"></a>
### 1.2. BOM的构成

BOM 比 DOM 更大，它包含 DOM。

![](images/1551319344183.png#alt=1551319344183)

<a name="c52f630f"></a>
### 1.3. 顶级对象window

![](images/1551319372909.png#alt=1551319372909)

<a name="c2e21437"></a>
### 1.4. window对象的常见事件

<a name="26157127"></a>
#### 页面（窗口）加载事件（2种）

**第1种**

![](images/1551319525109.png#alt=1551319525109)

window.onload 是窗口 (页面）加载事件，**当文档内容完全加载完成**会触发该事件(包括图像、脚本文件、CSS 文件等), 就调用的处理函数。

![](images/1551319600263.png#alt=1551319600263)

**第2种**

![](images/1551319620299.png#alt=1551319620299)

​	DOMContentLoaded 事件触发时，仅当DOM加载完成，不包括样式表，图片，flash等等。

​	IE9以上才支持！！！

​	如果页面的图片很多的话, 从用户访问到onload触发可能需要较长的时间, 交互效果就不能实现，必然影响用户的体验，此时用 DOMContentLoaded 事件比较合适。

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

<a name="b6190a6a"></a>
#### 调整窗口大小事件

![](images/1551319803117.png#alt=1551319803117)

​	window.onresize 是调整窗口大小加载事件,  当触发时就调用的处理函数。

注意：

1. 
只要窗口大小发生像素变化，就会触发这个事件。

2. 
我们经常利用这个事件完成响应式布局。 window.innerWidth 当前屏幕的宽度


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

<a name="59291e71"></a>
### 1.5. 定时器（两种）

window 对象给我们提供了 2 个非常好用的方法-定时器。

- 
setTimeout()

- 
setInterval()


<a name="ff31098a"></a>
#### setTimeout() 炸弹定时器

<a name="a680af8b"></a>
##### 开启定时器

![](images/1551320279307.png#alt=1551320279307)

![](images/1551320408854.png#alt=1551320408854)

![](images/1551320298981.png#alt=1551320298981)


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

<a name="81120d81"></a>
##### 案例：5秒后关闭广告

![](images/1551320924828.png#alt=1551320924828)

![](images/1551320959756.png#alt=1551320959756)

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

<a name="f0e4c797"></a>
##### 停止定时器

![](images/1551321051001.png#alt=1551321051001)

![](images/1551321064154.png#alt=1551321064154)

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

<a name="3bc0105d"></a>
#### setInterval() 闹钟定时器

<a name="a680af8b-1"></a>
##### 开启定时器

![](images/1551321162158.png#alt=1551321162158)

```javascript
    <script>
        // 1. setInterval 
        setInterval(function() {
            console.log('继续输出');
        }, 1000);
    </script>
```

<a name="63cbbb30"></a>
##### 案例：倒计时

![](images/1551321298787.png#alt=1551321298787)

![](images/1551321322188.png#alt=1551321322188)

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

<a name="f0e4c797-1"></a>
##### 停止定时器

![](images/1551321444559.png#alt=1551321444559)

<a name="fe535ff3"></a>
#### 案例：发送短信倒计时

​	点击按钮后，该按钮60秒之内不能再次点击，防止重复发送短信。

![](images/1551321540676.png#alt=1551321540676)

![](images/1551321564247.png#alt=1551321564247)

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

<a name="b9119bd6"></a>
### 1.6. this指向问题

​	this的指向在函数定义的时候是确定不了的，只有函数执行的时候才能确定this到底指向谁，一般情况下this的最终指向的是那个调用它的对象。

现阶段，我们先了解一下几个this指向

1. 
全局作用域或者普通函数中this指向全局对象window（注意定时器里面的this指向window）

2. 
方法调用中谁调用this指向谁

3. 
构造函数中this指向构造函数的实例


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

<a name="124bf70b"></a>
### 1.7. location对象

<a name="9d3d45e0"></a>
#### 什么是 location 对象

![](images/1551322091638.png#alt=1551322091638)

<a name="URL"></a>
#### URL

![](images/1551322373704.png#alt=1551322373704)

![](images/1551322387201.png#alt=1551322387201)

<a name="409b6c66"></a>
#### location 对象的属性

![](images/1551322416716.png#alt=1551322416716)

![](images/1551322438200.png#alt=1551322438200)

<a name="1b7fbcec"></a>
#### 案例：5分钟自动跳转页面

![](images/1551322496871.png#alt=1551322496871)

![](images/1551322517605.png#alt=1551322517605)

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

<a name="4691d3e1"></a>
#### 案例：获取URL参数

![](images/1551322622640.png#alt=1551322622640)

![](images/1551322639241.png#alt=1551322639241)

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

<a name="00ab6232"></a>
#### location对象的常见方法

![](images/1551322750241.png#alt=1551322750241)

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

<a name="03d16a6d"></a>
### 1.8. navigator对象

​	navigator 对象包含有关浏览器的信息，它有很多属性，我们最常用的是 userAgent，该属性可以返回由客户机发送服务器的 user-agent 头部的值。

下面前端代码可以判断用户那个终端打开页面，实现跳转

```javascript
if((navigator.userAgent.match(/(phone|pad|pod|iPhone|iPod|ios|iPad|Android|Mobile|BlackBerry|IEMobile|MQQBrowser|JUC|Fennec|wOSBrowser|BrowserNG|WebOS|Symbian|Windows Phone)/i))) {
    window.location.href = "";     //手机
 } else {
    window.location.href = "";     //电脑
 }
```

<a name="2ddbbcfb"></a>
### 1.9 history对象

​	window对象给我们提供了一个 history对象，与浏览器历史记录进行交互。该对象包含用户（在浏览器窗口中）访问过的URL。

![](images/1551322885216.png#alt=1551322885216)

history对象一般在实际开发中比较少用，但是会在一些 OA 办公系统中见到。

![](images/1551322959148.png#alt=1551322959148)

<a name="1f6671c7"></a>
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

<a name="16cc5c49"></a>
### 2.1 JS 是单线程

![](images/1551415019322.png#alt=1551415019322)

```javascript
	单线程就意味着，所有任务需要排队，前一个任务结束，才会执行后一个任务。如果前一个任务耗时很长，后一个任务就不得不一直等着。
	这样所导致的问题是： 如果 JS 执行的时间过长，这样就会造成页面的渲染不连贯，导致页面渲染加载阻塞的感觉。
```

<a name="8331071e"></a>
### 2.2 同步任务和异步任务

​	单线程导致的问题就是后面的任务等待前面任务完成，如果前面任务很耗时（比如读取网络数据），后面任务不得不一直等待！！

​	为了解决这个问题，利用多核 CPU 的计算能力，HTML5 提出 Web Worker 标准，允许 JavaScript 脚本创建多个线程，但是子线程完全受主线程控制。于是，JS 中出现了**同步任务**和**异步任务**。

<a name="6a620e3c"></a>
#### 同步

​	前一个任务结束后再执行后一个任务，程序的执行顺序与任务的排列顺序是一致的、同步的。比如做饭的同步做法：我们要烧水煮饭，等水开了（10分钟之后），再去切菜，炒菜。

<a name="8b5a247d"></a>
#### 异步

​	你在做一件事情时，因为这件事情会花费很长时间，在做这件事的同时，你还可以去处理其他事情。比如做饭的异步做法，我们在烧水的同时，利用这10分钟，去切菜，炒菜。

![](images/1551434295074.png#alt=1551434295074)


> ```javascript
JS中所有任务可以分成两种，一种是同步任务（synchronous），另一种是异步任务（asynchronous）。

同步任务指的是：
	在主线程上排队执行的任务，只有前一个任务执行完毕，才能执行后一个任务；
异步任务指的是：
	不进入主线程、而进入”任务队列”的任务，当主线程中的任务运行完了，才会从”任务队列”取出异步任务放入主线程执行。
```



![](images/1551434972778.png#alt=1551434972778)

<a name="7bb3c027"></a>
### 2.3 JS执行机制（事件循环）

![](images/1551435335464.png#alt=1551435335464)

![](images/1551435398306.png#alt=1551435398306)

![](images/1551435449634.png#alt=1551435449634)

<a name="9cc6216c"></a>
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
