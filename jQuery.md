## jQuery

jQuery 是一个 JavaScript 库，极大地简化了 JavaScript 编程

## 一、使用方式

jQuery 库是一个 JavaScript 文件，可以使用 HTML 的 <script> 标签引用它

```js
<head>
<script src="jquery-1.10.2.min.js"></script>
</head>
```

从 CDN 中载入 jQuery

```js
<script src="https://apps.bdimg.com/libs/jquery/2.1.4/jquery.min.js">
</script>
```

## 二、选择器

### 1.元素选择器

jQuery 使用 CSS 选择器来选取 HTML 元素

$("p") 选取 <p> 元素

$("p.intro") 选取所有 class="intro" 的 <p> 元素

$("p#demo") 选取所有 id="demo" 的 <p> 元素



### 2.属性选择器

$("[href]") 选取所有带有 href 属性的元素

$("[href='#']") 选取所有带有 href 值等于 "#" 的元素

$("[href!='#']") 选取所有带有 href 值不等于 "#" 的元素

$("[href$='.jpg']") 选取所有 href 值以 ".jpg" 结尾的元素



### 选择器实例

| 语法                 | 描述                                                 |
| :------------------- | :--------------------------------------------------- |
| $(this)              | 当前 HTML 元素                                       |
| $("p")               | 所有 <p> 元素                                        |
| $("p.intro")         | 所有 class="intro" 的 <p> 元素                       |
| $(".intro")          | 所有 class="intro" 的元素                            |
| $("#intro")          | id="intro" 的元素                                    |
| $("ul li:first")     | 每个 <ul> 的第一个 <li> 元素                         |
| $("[href$='.jpg']")  | 所有带有以 ".jpg" 结尾的属性值的 href 属性           |
| $("div#intro .head") | id="intro" 的 <div> 元素中的所有 class="head" 的元素 |



## 三、事件

页面对不同访问者的响应叫做事件

事件处理程序指的是当 HTML 中发生某些事件时所调用的方法

页面中指定一个点击事件：

```js
$("p").click(function(){
	alert('点击了')
});
```

**常用的 jQuery 事件方法**

| 鼠标事件   | 键盘事件 | 表单事件 | 文档/窗口事件 |
| :--------- | :------- | :------- | :------------ |
| click      | keypress | submit   | load          |
| dblclick   | keydown  | change   | resize        |
| mouseenter | keyup    | focus    | scroll        |
| mouseleave |          | blur     | unload        |
| hover      |          |          |               |

## 四、效果

### 1. 显示隐藏

可以使用 hide() 和 show() 方法来隐藏和显示 HTML 元素

```js
$("button").click(function(){
  $("p").hide();
});

$("button").click(function(){
  $("p").show();
});
```

#### 语法：

```js
//speed  规定隐藏/显示的速度
//callback  隐藏或显示完成后所执行的函数

$(selector).hide(speed,callback);

$(selector).show(speed,callback);
```

#### toggle()

可以使用 toggle() 方法来切换 hide() 和 show() 方法

```js
$("button").click(function(){
  $("p").toggle();
});
// 语法
// $(selector).toggle(speed,callback);
```



### 2.淡入淡出

通过 fade ，可以实现元素的淡入淡出效果。

四种 fade 方法，都可接收2个参数：

**speed** 规定效果的时长
**callback** 完成后所执行的函数

- **fadeIn()**   淡入
- **fadeOut()**   淡出
- **fadeToggle()** 切换
- **fadeTo()**   渐变

#### fadeIn()

fadeIn() 用于淡入已隐藏的元素。

```js
$("button").click(function(){
  $("#div1").fadeIn();
  $("#div3").fadeIn(3000);
});

```

#### **fadeOut()**  

fadeOut() 方法用于淡出可见元素

```js
$("button").click(function(){
  $("#div1").fadeOut();
  $("#div3").fadeOut(3000);
});
```

#### **fadeToggle()**  

fadeToggle() 方法可以在 fadeIn() 与 fadeOut() 方法之间进行切换

如果元素已淡出，则 fadeToggle() 会向元素添加淡入效果

如果元素已淡入，则 fadeToggle() 会向元素添加淡出效果

```js
$("button").click(function(){
  $("#div1").fadeOut();
  $("#div3").fadeOut(3000);
});
```

#### **fadeTo()**  

fadeTo() 方法允许渐变为给定的不透明度（值介于 0 与 1 之间）

```js
$("button").click(function(){
  $("#div3").fadeTo(3000,0.3);
  $("#div3").fadeTo(3000,0.5);
  $("#div3").fadeTo(3000,0.7);
});
```



### 3.滑动

jQuery 拥有以下滑动方法：

都可接收2个参数：

**speed** 规定效果的时长
**callback** 完成后所执行的函数

- slideDown()
- slideUp()
- slideToggle()

#### slideDown()

slideDown() 方法用于向下滑动元素

```js
$("button").click(function(){
  $("#divl").slideDown();
});
```

#### slideUp()

slideUp() 方法用于向下滑动元素

```js
$("button").click(function(){
  $("#divl").slideUp();
});
```

#### slideToggle()

slideToggle() 方法可以在 slideDown() 与 slideUp() 方法之间进行切换。

如果元素向下滑动，则 slideToggle() 可向上滑动它们

如果元素向上滑动，则 slideToggle() 可向下滑动它们

```js
$("button").click(function(){
  $("#divl").slideToggle();
});
```



### 4.动画

animate() 方法用于创建自定义动画

**默认所有 HTML 元素都有一个静态位置，且无法移动。**

**如需对位置进行操作，首先把元素的 CSS position 属性设置为 relative、fixed 或 absolute**

#### **基础使用：**

```js
//必需的 params 参数定义形成动画的 CSS 属性。

//可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。

//可选的 callback 参数是动画完成后所执行的函数名称

$(selector).animate({params},speed,callback);
```

```js
$("button").click(function(){
  $("div").animate({left:'250px'});
}); 
```

#### **操作多个属性：**

```js
$("button").click(function(){
  $("div").animate({
    left:'250px',
    opacity:'0.5',
    height:'150px',
    width:'150px'
  });
}); 
```

nimate() 方法来操作大部分 CSS 属性。当使用 animate() 时，必须使用**驼峰**写所有的属性名，比如，必须使用 paddingLeft 而不是 padding-left，使用 marginRight 而不是 margin-right。

#### 使用相对值

也可以定义相对值（该值相对于元素的当前值）。需要在值的前面加上 += 或 -=

```js
$("button").click(function(){
  $("div").animate({
    left:'250px',
    height:'+=150px',
    width:'+=150px'
  });
});
```

#### 使用预定义的值

以把属性的动画值设置为 "show"、"hide" 或 "toggle"

```js
$("button").click(function(){
  $("div").animate({
    height:'toggle'
  });
});
```

#### 使用队列

jQuery 提供针对动画的队列功能。

如果编写多个 animate() 调用，jQuery 会创建包含这些方法调用的“内部”队列。然后逐一运行这些 animate 调用

```js
$("button").click(function(){
  var div=$("div");
  div.animate({height:'300px',opacity:'0.4'},"slow");
  div.animate({width:'300px',opacity:'0.8'},"slow");
  div.animate({height:'100px',opacity:'0.4'},"slow");
  div.animate({width:'100px',opacity:'0.8'},"slow");
});
```

### 5.停止动画

**stop()** 方法用于停止还在执行的动画或效果

stop() 方法适用于所有 jQuery 效果函数，包括滑动、淡入淡出和自定义动画

```js
//$(selector).stop(stopAll,goToEnd);

$("#stop").click(function(){
  $("#panel").stop();
});
```



## 五、DOM操作

### 1.获得内容

- text() - 设置或返回所选元素的文本内容

- html() - 设置或返回所选元素的内容（包括 HTML 标记）

- val() - 设置或返回表单字段的值

    **text() 和 html() 方法来获得内容**

```js
$("#btn1").click(function(){
  alert("Text: " + $("#test").text());
});
$("#btn2").click(function(){
  alert("HTML: " + $("#test").html());
});
```

**val() 方法获得输入字段的值：**

```js
$("#btn1").click(function(){
  alert("Value: " + $("#test").val());
});
```

### 2.设置内容

- **text()** - 设置或返回所选元素的文本内容
- **html()** - 设置或返回所选元素的内容（包括 HTML 标签）
- **val()** - 设置或返回表单字段的值

```js
$("#btn1").click(function(){
  $("#test1").text("Hello world!");
});
$("#btn2").click(function(){
  $("#test2").html("<b>Hello world!</b>");
});
$("#btn3").click(function(){
  $("#test3").val("Hello world");
});
```

### 3.获取属性

 attr() 方法用于获取属性值

```js
$("button").click(function(){
  alert($("a").attr("href"));
});
```

### 4.设置属性

attr() 方法也用于设置/改变属性值

```js
$("button").click(function(){
  $("a").attr("href","https://www.baidu.com/");
});

//设置多个属性
$("button").click(function(){
  $("a").attr({
      href :"https://www.baidu.com/",
      title : "百度"
  });
});
```

### 5.添加元素

- **append()** - 在被选元素的结尾插入内容

- **prepend()** - 在被选元素的开头插入内容

- **after()** - 在被选元素之后插入内容

- **before()** - 在被选元素之前插入内容

    **4个方法均可接收多个参数**

####  append()

append() 方法在被选元素的结尾插入内容

```js
$("p").append("我是使用append插入的内容");
```

####  prepend()

prepend() 方法在被选元素的开头插入内容

```js
$("p").prepend("我是使用prepend插入的内容");
```

#### after()

after() 方法在被选元素之后插入内容

```js
$("p").after("我是使用after插入的内容");
```

#### before()

before() 方法在被选元素之前插入内容

```js
$("p").before("我是使用before插入的内容");
```



### 6.删除

如需删除元素和内容，一般可使用以下两个 jQuery 方法：

- **remove()** - 删除被选元素（及其子元素）
- **empty()** - 从被选元素中删除子元素

#### remove() 

 remove() 方法删除**被选元素及其子元素**

```js
$("#div1").remove();
```

####  empty() 

 empty() 方法删除被选元素的**子元素**

```js
$("#div1").empty();
//$('#div1').html('')
```

#### 过滤被删除的元素

remove() 方法也可接受一个参数，允许对被删元素进行过滤

```js
$("p").remove(".text");
```



### 7.操作css类

进行 CSS 操作的方法：

- **addClass() -** 向被选元素添加一个或多个类
- **removeClass()** - 从被选元素删除一个或多个类
- **toggleClass()** - 对被选元素进行添加/删除类的切换操作
- **css()** - 设置或返回样式属性

#### addClass()

向不同的元素添加 class 属性

```js
$("button").click(function(){
    // list red
  $("h1,h2,p").addClass("red");
  $("div").addClass("box");
});
```

也可以在 addClass() 方法中规定多个类：

```css
$("button").click(function(){
  $("#div1").addClass("box blue");
});
```

#### removeClass() 

删除指定的 class 属性：

```js
$("button").click(function(){
  $("h1,h2,p").removeClass("red");
});
```

#### toggleClass() 

对被选元素进行添加/删除类的切换操作

```js
$("button").click(function(){
  $("h1,h2,p").toggleClass("red");
});
```

#### css()

css() 方法设置或返回被选元素的一个或多个样式属性

```js
//获取样式
$("p").css();
//设置背景颜色
$("p").css("background-color");

//设置样式
$("p").css("background-color","yellow");
//设置多个样式
$("p").css({"background-color":"yellow","font-size":"200%"});
```

#### 尺寸

jQuery 提供多个处理尺寸的方法：

- width()
- height()
- innerWidth()
- innerHeight()
- outerWidth()
- outerHeight()

##### width()  height() 

width() 方法设置或返回元素的宽度（不包括内边距、边框或外边距）

height() 方法设置或返回元素的高度（不包括内边距、边框或外边距）

```js
$("button").click(function(){
    console.log($("#div1").width())
    console.log($("#div1").height())
});
```

##### innerWidth()  innerHeight()

innerWidth() 方法返回元素的宽度（包括内边距）

innerHeight() 方法返回元素的高度（包括内边距）

```js
$("button").click(function(){
    console.log($("#div1").innerWidth())
    console.log($("#div1").innerHeight())
});
```

##### outerWidth()  outerHeight()

outerWidth() 方法返回元素的宽度（**包括内边距和边框**）

outerHeight() 方法返回元素的高度（**包括内边距和边框**）

```js
$("button").click(function(){
    console.log($("#div1").outerWidth())
    console.log($("#div1").outerHeight())
});
```

outerWidth(true) 方法返回元素的宽度（**包括内边距、边框和外边距**）

outerHeight(true) 方法返回元素的高度（**包括内边距、边框和外边距**）

```js
$("button").click(function(){
    console.log($("#div1").outerWidth(true))
    console.log($("#div1").outerHeight(true))
});
```

##### 指定元素宽度高度

```js
$("button").click(function(){
  $("#div1").width(500).height(500);
});
```



## 六、遍历

### 1.向上遍历 DOM 树

用于向上遍历 DOM 树：

- parent()
- parents()
- parentsUntil()

#### parent() 

parent() 方法返回被选元素的直接父元素。

该方法只会向上一级对 DOM 树进行遍历

```js
$("span").parent().css({"color":"red","border":"2px solid red"}
```

#### parents()

parents() 方法返回被选元素的**所有祖先元素**，它一路向上直到文档的根元素 (<html>)

```js
$("span").parents().css({"color":"red","border":"2px solid red"}
```

#### parentsUntil

parentsUntil() 方法返回介于**两个给定元素之间**的所有**祖先元素**

```js
 $("span").parentsUntil("div").css({"color":"red","border":"2px solid red"});
```



### 2.向下遍历 DOM 树

用于向下遍历 DOM 树的 jQuery 方法：

- children()
- find()

#### children()

children() 方法返回被选元素的所有**直接子元素**

```js
 $("div").children().css({"color":"red","border":"2px solid red"});
//过滤对子元素
 $("div").children("p.1").css({"color":"red","border":"2px solid red"});
```

#### find() 

find() 方法返回被选**元素的后代元素**，一路向下直到最后一个后代

```js
//只选中span
$("div").find("span").css({"color":"red","border":"2px solid red"});
//选中所有
$("div").find("*").css({"color":"red","border":"2px solid red"});
```

### 3.DOM 树中水平遍历

在 DOM 树进行水平遍历：

- siblings()
- next()
- nextAll()
- nextUntil()
- prev()
- prevAll()
- prevUntil()

#### siblings()

siblings() 方法返回被选元素的所有同胞元素

```js
$("h2").siblings().css({"color":"red","border":"2px solid red"});
// <h2> 的同胞元素的所有 <p> 元素
$("h2").siblings("p").css({"color":"red","border":"2px solid red"});
```

#### next()

next() 方法返回被选元素的下一个同胞元素

```js
 $("h2").next().css({"color":"red","border":"2px solid red"});
```

#### nextAll()

nextAll() 方法返回被选元素的所有跟随的同胞元素

```js
$("h2").nextAll().css({"color":"red","border":"2px solid red"});
```

#### nextUntil()

nextUntil() 方法返回介于两个给定参数之间的所有跟随的同胞元素

```js
 $("h2").nextUntil("h6").css({"color":"red","border":"2px solid red"});
```

#### prev()

prev() 获得匹配元素集合中每个元素紧邻的前一个同胞元素

#### prevAll()

prevAll() 获得当前匹配元素集合中每个元素的前面的同胞元素

#### prevUntil()

prevUntil() 方法获得当前匹配元素集合中每个元素的前面的同胞元素



### 4.过滤

过滤允许基于其在一组元素中的位置来选择一个特定的元素:

- **first()**
- **last()** 
- **eq()**
- **filter()**
- **not()** 
- 

#### first()

first() 方法返回被选元素的首个元素

```js
$("div p").first().css("background-color","yellow")
```

#### last()

last() 方法返回被选元素的最后一个元素

```js
$("div p").last().css("background-color","yellow")
```

#### eq()

eq() 方法返回被选元素中带有指定索引号的元素

```js
$("p").eq(1).css("background-color","yellow")
```

#### filter()

filter() 方法允许您规定一个标准,匹配的元素会被返回

```js
$("p").filter(".info").css("background-color","yellow")
```

#### not() 

not() 方法返回不匹配标准的所有元素

```js
$("p").not(".info").css("background-color","yellow")
```



## 七、AJAX

**AJAX 是与服务器交换数据的方法，它在不重载全部页面的情况下，实现了对部分网页的更新**

通过 jQuery AJAX 方法，可以使用 HTTP的 **get** 和  **post**方法， 从远程服务器上请求文本、HTML、XML 或 JSON 同时还能够把这些外部数据直接载入网页的被选元素中

### load() 

**语法：**

```
$(selector).load(URL,data,callback);
```

**URL** 参数规定加载的 URL   **必选**

**data **参数规定与请求一同发送的查询字符串键/值对集合  **可选**

**callback** 参数是 load() 方法完成后所执行的函数名称 **可选**



load() 方法从服务器加载数据，并把返回的数据放入被选元素中

```js
 $("#btn1").click(function(){
 $('#test').load('https://www.fastmock.site/mock/323354e56ef21147c3f550e18435baa1/api/get/myCourse',data,function(){});
  })
```

### get()

$.get() 方法通过 HTTP GET 请求从服务器上请求数据。

```js
//$.get(URL,callback);
 $("button").click(function(){
  $.get('https://www.fastmock.site/mock/323354e56ef21147c3f550e18435baa1/api/get/myCourse',function(data,status){
      console.log(data);
      console.log(status);
    });
  });
```

### post()

$.post() 方法通过 HTTP POST 请求从服务器上请求数据

```js
//$.post(URL,data,callback);

$.post("/example/jquery/demo_test_post.asp",
    {
      page:1,
      name:"Tina"
    },
    function(data,status){
      console.log(data);
      console.log(status);
    });
```





## 八、在线文档  

### https://jquery.cuishifeng.cn/

