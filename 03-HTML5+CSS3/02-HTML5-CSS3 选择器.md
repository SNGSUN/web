# 02-HTML5-CSS3 选择器

###### 七、`CSS3` 属性选择器(上)


1. 什么是 `CSS3`
   - 在 `CSS2` 的基础上拓展、新增的样式



2. `CSS3` 发展现状
   - 移动端支持优于 `PC` 端
   - `CSS3` 目前还草案，在不断改进中
   - `CSS3` 相对 `H5`，应用非常广泛



3. 属性选择器列表

![attrcanshu.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1597836028439-5728ba1f-a808-4155-9925-af7528bbf31e.png#align=left&display=inline&height=402&margin=%5Bobject%20Object%5D&name=attrcanshu.png&originHeight=402&originWidth=1090&size=72762&status=done&style=none&width=1090)

4. 属性选择器代码演示```css
button {
  cursor: pointer;
}
button[disabled] {
  cursor: default
}
```




###### 八、`CSS3` 属性选择器(下)


1. 代码演示```css
input[type=search] {
  color: skyblue;
}

span[class^=black] {
  color: lightgreen;
}

span[class$=black] {
  color: lightsalmon;
}

span[class*=black] {
  color: lightseagreen;
}
```




###### 九、结构伪类选择器


1. 属性列表 

 ![jiegouweilei.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1597836048937-c40b6dc6-64aa-4464-a184-19234d00e5b9.png#align=left&display=inline&height=373&margin=%5Bobject%20Object%5D&name=jiegouweilei.png&originHeight=373&originWidth=1003&size=55049&status=done&style=none&width=1003)

2. 代码演示```css
ul li:first-child {
  background-color: lightseagreen;
}

ul li:last-child {
  background-color: lightcoral;
}

ul li:nth-child(3) {
  background-color: aqua;
}
```




###### 十、`nth-child` 参数详解


1. nth-child 详解
   - 注意：本质上就是选中第几个子元素
   - n 可以是数字、关键字、公式
   - n 如果是数字，就是选中第几个
   - 常见的关键字有 `even` 偶数、`odd` 奇数
   - 常见的公式如下(如果 n 是公式，则从 0 开始计算)
   - 但是第 0 个元素或者超出了元素的个数会被忽略    

![nthchildcanshu.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1597836088198-478544d2-de50-459e-8bcf-1b9cd0adbf53.png#align=left&display=inline&height=324&margin=%5Bobject%20Object%5D&name=nthchildcanshu.png&originHeight=324&originWidth=1014&size=30414&status=done&style=none&width=1014)

2. 代码演示



```css
<style>
  /* 偶数 */
  ul li:nth-child(even) {
    background-color: aquamarine;
  }

  /* 奇数 */
  ul li:nth-child(odd) {
    background-color: blueviolet;
  }

  /*n 是公式，从 0 开始计算 */
  ul li:nth-child(n) {
    background-color: lightcoral;
  }

  /* 偶数 */
  ul li:nth-child(2n) {
    background-color: lightskyblue;
  }

  /* 奇数 */
  ul li:nth-child(2n + 1) {
    background-color: lightsalmon;
  }

  /* 选择第 0 5 10 15, 应该怎么选 */
  ul li:nth-child(5n) {
    background-color: orangered;
  }

  /* n + 5 就是从第5个开始往后选择 */
  ul li:nth-child(n + 5) {
    background-color: peru;
  }

  /* -n + 5 前五个 */
  ul li:nth-child(-n + 5) {
    background-color: tan;
  }
</style>
```


###### 十一、`nth-child` 和  `nt-of-type` 的区别


1. 代码演示



```css
<style>
  div :nth-child(1) {
    background-color: lightblue;
  }

  div :nth-child(2) {
    background-color: lightpink;
  }

  div span:nth-of-type(2) {
    background-color: lightseagreen;
  }

  div span:nth-of-type(3) {
    background-color: #fff;
  }
</style>
```


2. 区别
   - `nth-child`  选择父元素里面的第几个子元素，不管是第几个类型
   - `nt-of-type`  选择指定类型的元素



###### 十二、伪元素选择器


1. 伪类选择器  

 ![weiyuansu.png](https://cdn.nlark.com/yuque/0/2020/png/1483858/1597836129443-5a12437d-8ed5-4af9-9900-a9f165df7f4c.png#align=left&display=inline&height=179&margin=%5Bobject%20Object%5D&name=weiyuansu.png&originHeight=179&originWidth=1097&size=26526&status=done&style=none&width=1097)

2. 伪类选择器注意事项
   - `before` 和 `after` 必须有 `content` 属性
   - `before` 在内容前面，after 在内容后面
   - `before` 和 `after` 创建的是一个元素，但是属于行内元素
   - 创建出来的元素在 `Dom` 中查找不到，所以称为伪元素
   - 伪元素和标签选择器一样，权重为 1
3. 代码演示```css
<style>
    div {
      width: 100px;
      height: 100px;
      border: 1px solid lightcoral;
    }

    div::after,
    div::before {
      width: 20px;
      height: 50px;
      text-align: center;
      display: inline-block;
    }
    div::after {
      content: '时';
      background-color: lightskyblue;
    }

    div::before {
      content: '光';
      background-color: mediumaquamarine;
    }
  </style>
```




###### 十三、伪元素的案例


1. 添加字体图标```css
p {
   width: 220px;
   height: 22px;
   border: 1px solid lightseagreen;
   margin: 60px;
   position: relative;
}
p::after {
  content: '\ea50';
  font-family: 'icomoon';
  position: absolute;
  top: -1px;
  right: 10px;
}
```






