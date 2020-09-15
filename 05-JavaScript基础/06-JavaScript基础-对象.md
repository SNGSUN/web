# 06-JavaScript基础-对象

<a name="15dc5516"></a>
## 1 - 内置对象


<a name="9de1ea17"></a>
### 1.1 内置对象

<br />		 JavaScript 中的对象分为3种：**自定义对象 、内置对象、 浏览器对象**<br />		前面两种对象是JS 基础 内容，属于 ECMAScript；  第三个浏览器对象属于 JS 独有的， JS API 讲解内置对象就是指 JS 语言自带的一些对象，这些对象供开发者使用，并提供了一些常用的或是**最基本而必要的功能**（属性和方法），内置对象最大的优点就是帮助我们快速开发<br />
<br />	 	JavaScript 提供了多个内置对象：Math、 Date 、Array、String等<br />

<a name="b7b14ba2"></a>
### 1.2 查文档

<br />		查找文档：学习一个内置对象的使用，只要学会其常用成员的使用即可，我们可以通过查文档学习，可以通过MDN/W3C来查询。<br />		Mozilla 开发者网络（MDN）提供了有关开放网络技术（Open Web）的信息，包括 HTML、CSS 和万维网及 HTML5 应用的 API。<br />		MDN:[https://developer.mozilla.org/zh-CN/](https://developer.mozilla.org/zh-CN/)<br />

<a name="2e5437bb"></a>
### 1.3 Math对象

<br />		Math 对象不是构造函数，它具有数学常数和函数的属性和方法。跟数学相关的运算（求绝对值，取整、最大值等）可以使用 Math 中的成员。

| 属性、方法名 | 功能 |
| --- | --- |
| Math.PI | 圆周率 |
| Math.floor() | 向下取整 |
| Math.ceil() | 向上取整 |
| Math.round() | 四舍五入版 就近取整   注意 -3.5   结果是  -3 |
| Math.abs() | 绝对值 |
| Math.max()/Math.min() | 求最大和最小值 |
| Math.random() | 获取范围在[0,1)内的随机值 |


<br />	注意：上面的方法使用时必须带括号<br />
<br />	**获取指定范围内的随机整数**：<br />

```javascript
function getRandom(min, max) {
  return Math.floor(Math.random() * (max - min + 1)) + min; 
}
```


<a name="b61627fa"></a>
### 1.4 日期对象

<br />	 	Date 对象和 Math 对象不一样，Date是一个构造函数，所以使用时需要实例化后才能使用其中具体方法和属性。Date 实例用来处理日期和时间<br />

- 使用Date实例化日期对象
   - 获取当前时间必须实例化：
```javascript
var now = new Date();
```

   - 获取指定时间的日期对象
```javascript
var future = new Date('2019/5/1');
```

注意：如果创建实例时并未传入参数，则得到的日期对象是当前时间对应的日期对象

- 使用Date实例的方法和属性

![图片1.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600179620937-c0c61466-b35b-4746-90f0-10d0e54ec56d.png#align=left&display=inline&height=285&margin=%5Bobject%20Object%5D&name=%E5%9B%BE%E7%89%871.png&originHeight=285&originWidth=706&size=67951&status=done&style=none&width=706)

- 通过Date实例获取总毫米数
   - 总毫秒数的含义<br />	基于1970年1月1日（世界标准时间）起的毫秒数
   - 获取总毫秒数```javascript
// 实例化Date对象
var now = new Date();
// 1. 用于获取对象的原始值
console.log(date.valueOf())	
console.log(date.getTime())	
// 2. 简单写可以这么做
var now = + new Date();			
// 3. HTML5中提供的方法，有兼容性问题
var now = Date.now();
```




<a name="15ca41d2"></a>
### 1.5 数组对象


<a name="94e7e806"></a>
#### 创建数组的两种方式


- 字面量方式
   - 示例代码如下：```javascript
var arr = [1,"test",true];
```

- new Array()
   - 示例代码如下：```
var arr = new Array();
```
<br />	注意：上面代码中arr创建出的是一个空数组，如果需要使用构造函数Array创建非空数组，可以在创建数组时传入参数<br />	参数传递规则如下：
      - 如果只传入一个参数，则参数规定了数组的长度
      - 如果传入了多个参数，则参数称为数组的元素



<a name="77f4923a"></a>
#### 检测是否为数组


- instanceof 运算符
   - instanceof 可以判断一个对象是否是某个构造函数的实例```javascript
var arr = [1, 23];
var obj = {};
console.log(arr instanceof Array); // true
console.log(obj instanceof Array); // false
```

- Array.isArray()
   - Array.isArray()用于判断一个对象是否为数组，isArray() 是 HTML5 中提供的方法```javascript
var arr = [1, 23];
var obj = {};
console.log(Array.isArray(arr));   // true
console.log(Array.isArray(obj));   // false
```




<a name="2a8dce22"></a>
#### 添加删除数组元素的方法


- 数组中有进行增加、删除元素的方法，部分方法如下表<br />![图片2.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600179634637-fa6a22d0-321a-455e-a50b-9c849183214b.png#align=left&display=inline&height=209&margin=%5Bobject%20Object%5D&name=%E5%9B%BE%E7%89%872.png&originHeight=209&originWidth=734&size=88254&status=done&style=none&width=734)<br />注意：push、unshift为增加元素方法；pop、shift为删除元素的方法



<a name="d4c8995b"></a>
#### 数组排序


- 数组中有对数组本身排序的方法，部分方法如下表<br />![图片3.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600179643163-023b5902-a7d9-49b9-a9f0-63c9a67e401a.png#align=left&display=inline&height=108&margin=%5Bobject%20Object%5D&name=%E5%9B%BE%E7%89%873.png&originHeight=108&originWidth=696&size=43359&status=done&style=none&width=696)<br />注意：sort方法需要传入参数来设置升序、降序排序
   - 如果传入“function(a,b){ return a-b;}”，则为升序
   - 如果传入“function(a,b){ return b-a;}”，则为降序



<a name="13ba8ed0"></a>
#### 数组索引方法


- 数组中有获取数组指定元素索引值的方法，部分方法如下表

![图片4.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600179652766-af4e685c-1d7d-4b00-9298-c33699bbfb32.png#align=left&display=inline&height=112&margin=%5Bobject%20Object%5D&name=%E5%9B%BE%E7%89%874.png&originHeight=112&originWidth=716&size=39832&status=done&style=none&width=716)<br />

<a name="1f3d6f30"></a>
#### 数组转换为字符串


- 数组中有把数组转化为字符串的方法，部分方法如下![图片5.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600179662771-45e19e93-c8ac-46f8-9941-b46bca6e0a06.png#align=left&display=inline&height=116&margin=%5Bobject%20Object%5D&name=%E5%9B%BE%E7%89%875.png&originHeight=116&originWidth=706&size=37915&status=done&style=none&width=706)<br />注意：join方法如果不传入参数，则按照 “ , ”拼接元素



<a name="947356c1"></a>
#### 其他方法


- 数组中还有其他操作方法，同学们可以在课下自行查阅学习

![图片6.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600179674434-502f8deb-203c-4bd7-9791-5e2f0d8d98b9.png#align=left&display=inline&height=144&margin=%5Bobject%20Object%5D&name=%E5%9B%BE%E7%89%876.png&originHeight=144&originWidth=706&size=55647&status=done&style=none&width=706)<br />

<a name="d192a1cd"></a>
### 1.6 字符串对象


<a name="e20416ec"></a>
#### 基本包装类型

<br />		为了方便操作基本数据类型，JavaScript 还提供了三个特殊的引用类型：String、Number和 Boolean。<br />
<br />		基本包装类型就是把简单数据类型包装成为复杂数据类型，这样基本数据类型就有了属性和方法。<br />

```javascript
// 下面代码有什么问题？
var str = 'andy';
console.log(str.length);
```

<br />		按道理基本数据类型是没有属性和方法的，而对象才有属性和方法，但上面代码却可以执行，这是因为<br />
<br />		js 会把基本数据类型包装为复杂数据类型，其执行过程如下 ：<br />

```javascript
// 1. 生成临时变量，把简单类型包装为复杂数据类型
var temp = new String('andy');
// 2. 赋值给我们声明的字符变量
str = temp;
// 3. 销毁临时变量
temp = null;
```


<a name="6195e6f7"></a>
#### 字符串的不可变

<br />		指的是里面的值不可变，虽然看上去可以改变内容，但其实是地址变了，内存中新开辟了一个内存空间。<br />
<br />		当重新给字符串变量赋值的时候，变量之前保存的字符串不会被修改，依然在内存中重新给字符串赋值，会重新在内存中开辟空间，这个特点就是字符串的不可变。<br />		由于字符串的不可变，在**大量拼接字符串**的时候会有效率问题<br />

<a name="8fec1c55"></a>
#### 根据字符返回位置

<br />		字符串通过基本包装类型可以调用部分方法来操作字符串，以下是返回指定字符的位置的方法：<br />
<br />![图片7.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600179689478-49874890-1387-463d-a5d2-885ef105d1b7.png#align=left&display=inline&height=137&margin=%5Bobject%20Object%5D&name=%E5%9B%BE%E7%89%877.png&originHeight=137&originWidth=717&size=39652&status=done&style=none&width=717)<br />
<br />		案例：查找字符串"abcoefoxyozzopp"中所有o出现的位置以及次数<br />

1. 先查找第一个o出现的位置
2. 然后 只要indexOf 返回的结果不是 -1 就继续往后查找
3. 因为indexOf 只能查找到第一个，所以后面的查找，利用第二个参数，当前索引加1，从而继续查找



<a name="e6d76848"></a>
#### 根据位置返回字符

<br />		字符串通过基本包装类型可以调用部分方法来操作字符串，以下是根据位置返回指定位置上的字符：<br />
<br />![图片8.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600179701437-991f6ed3-d2a8-4ad5-bdd5-0821030ac756.png#align=left&display=inline&height=141&margin=%5Bobject%20Object%5D&name=%E5%9B%BE%E7%89%878.png&originHeight=141&originWidth=714&size=52723&status=done&style=none&width=714)<br />
<br />		在上述方法中，charCodeAt方法返回的是指定位置上字符对应的ASCII码，ASCII码对照表如下：<br />
<br />![图片9.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600179712120-5f1becdd-75f9-4a50-9de9-8e57298d9933.png#align=left&display=inline&height=390&margin=%5Bobject%20Object%5D&name=%E5%9B%BE%E7%89%879.png&originHeight=390&originWidth=577&size=457586&status=done&style=none&width=577)<br />
<br />		案例：判断一个字符串 'abcoefoxyozzopp' 中出现次数最多的字符，并统计其次数<br />

1. 核心算法：利用 charAt(） 遍历这个字符串
2. 把每个字符都存储给对象， 如果对象没有该属性，就为1，如果存在了就 +1
3. 遍历对象，得到最大值和该字符<br />	注意：在遍历的过程中，把字符串中的每个字符作为对象的属性存储在对象总，对应的属性值是该字符出现的次数



<a name="99178230"></a>
#### 字符串操作方法

<br />		字符串通过基本包装类型可以调用部分方法来操作字符串，以下是部分操作方法：<br />
<br />![图片10.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600179722997-769abf29-40f1-49e0-a2d7-c12a245a68f9.png#align=left&display=inline&height=207&margin=%5Bobject%20Object%5D&name=%E5%9B%BE%E7%89%8710.png&originHeight=207&originWidth=736&size=83961&status=done&style=none&width=736)<br />

<a name="cc86598d"></a>
#### replace()方法

<br />		replace() 方法用于在字符串中用一些字符替换另一些字符，其使用格式如下：<br />

```
字符串.replace(被替换的字符串， 要替换为的字符串)；
```


<a name="c8747110"></a>
#### split()方法

<br />		split()方法用于切分字符串，它可以将字符串切分为数组。在切分完毕之后，返回的是一个新数组。<br />
<br />		其使用格式如下：<br />

```
字符串.split("分割字符")
```


<a name="3520fe2d"></a>
## 2 - 简单数据类型和复杂数据类型


<a name="93d3c460"></a>
### 2.1 简单数据类型

<br />		**简单类型**（**基本数据类型**、**值类型**）：在存储时变量中存储的是值本身，包括string ，number，boolean，undefined，null<br />

<a name="d88260a6"></a>
### 2.2 复杂数据类型

<br />		**复杂数据类型（引用类型）**：在存储时变量中存储的仅仅是地址（引用），通过 new 关键字创建的对象（系统对象、自定义对象），如 Object、Array、Date等；<br />

<a name="7552cafb"></a>
### 2.3 堆栈


- 堆栈空间分配区别：


<br />1、栈（操作系统）：由操作系统自动分配释放存放函数的参数值、局部变量的值等。其操作方式类似于数据结构中的栈；<br />
<br />简单数据类型存放到栈里面<br />
<br />2、堆（操作系统）：存储复杂类型(对象)，一般由程序员分配释放，若程序员不释放，由垃圾回收机制回收。<br />
<br />![图片11.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600179736722-7b366dce-edb3-4581-a893-7f5511aa56f2.png#align=left&display=inline&height=165&margin=%5Bobject%20Object%5D&name=%E5%9B%BE%E7%89%8711.png&originHeight=165&originWidth=288&size=5751&status=done&style=none&width=288)<br />

- 简单数据类型的存储方式<br />		值类型变量的数据直接存放在变量（栈空间）中


<br />![图片12.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600179744037-d066d7f0-e75c-486c-8b2b-66b5834c4797.png#align=left&display=inline&height=130&margin=%5Bobject%20Object%5D&name=%E5%9B%BE%E7%89%8712.png&originHeight=130&originWidth=525&size=4994&status=done&style=none&width=525)<br />

- 复杂数据类型的存储方式<br />		引用类型变量（栈空间）里存放的是地址，真正的对象实例存放在堆空间中

![图片13(1).png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600179753162-c207d76d-72fd-4792-bd74-2f1a92b9072f.png#align=left&display=inline&height=179&margin=%5Bobject%20Object%5D&name=%E5%9B%BE%E7%89%8713%281%29.png&originHeight=179&originWidth=407&size=5233&status=done&style=none&width=407)<br />

<a name="c25d04e6"></a>
### 2.4 简单类型传参

<br />		函数的形参也可以看做是一个变量，当我们把一个值类型变量作为参数传给函数的形参时，其实是把变量在栈空间里的值复制了一份给形参，那么在方法内部对形参做任何修改，都不会影响到的外部变量。<br />

```javascript
function fn(a) {
    a++;
    console.log(a); 
}
var x = 10;
fn(x);
console.log(x)；
```

<br />		运行结果如下：<br />
<br />![图片14.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600179762448-b8277f00-d94f-42c8-8c10-926ea1d7c6c6.png#align=left&display=inline&height=103&margin=%5Bobject%20Object%5D&name=%E5%9B%BE%E7%89%8714.png&originHeight=103&originWidth=233&size=1596&status=done&style=none&width=233)<br />

<a name="4a7af1b6"></a>
### 2.5 复杂数据类型传参

<br />		函数的形参也可以看做是一个变量，当我们把引用类型变量传给形参时，其实是把变量在栈空间里保存的堆地址复制给了形参，形参和实参其实保存的是同一个堆地址，所以操作的是同一个对象。<br />

```javascript
function Person(name) {
    this.name = name;
}
function f1(x) { // x = p
    console.log(x.name); // 2. 这个输出什么 ?    
    x.name = "张学友";
    console.log(x.name); // 3. 这个输出什么 ?    
}
var p = new Person("刘德华");
console.log(p.name);    // 1. 这个输出什么 ?   
f1(p);
console.log(p.name);    // 4. 这个输出什么 ?
```

<br />		运行结果如下：<br />
<br />![图片15.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1600179769021-38de07ba-6cdf-428e-871b-a96bfc49480a.png#align=left&display=inline&height=211&margin=%5Bobject%20Object%5D&name=%E5%9B%BE%E7%89%8715.png&originHeight=211&originWidth=460&size=9809&status=done&style=none&width=460)
