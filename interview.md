# 前端开发知识点
## HTML&CSS：
	对Web标准的理解、浏览器内核差异、兼容性、hack、CSS基本功：布局、盒子模型、选择器优先级、
	HTML5、CSS3、Flexbox

## JavaScript：
    数据类型、运算、对象、Function、继承、闭包、作用域、原型链、事件、RegExp、JSON、Ajax、
	DOM、BOM、内存泄漏、跨域、异步装载、模板引擎、前端MVC、路由、模块化、Canvas、ECMAScript 6、Nodejs

## 其他：
    移动端、响应式、自动化构建、HTTP、离线存储、WEB安全、优化、重构、团队协作、可维护、易用性、SEO、UED、架构、职业生涯、快速学习能力

# CSS类
## 假设高度已知，请写出三栏布局，其中左栏、右栏宽度各为300px，中间自适应。
请写出五到七种方案，并说出各种方案的优缺点和兼容性
## 左侧菜单栏占300px，右侧内容可以根据浏览器自适应。根据此要求，编写html css代码

## CSS选择器又哪些？有哪些新特性？有哪些伪类？
###选择器

- 并联选择器：即群组选择器，即以“,”合并多个分组结果
- 简单选择器：标签，ID，类，属性，通配符
- 关系选择器：即派生选择器，亲子，后代，相邻，兄长
- 伪类选择器：动作伪类，目标伪类，语言伪类，状态伪类，结构伪类，取反伪类
###新特性
- ~ 规则同p:not(:nth-of-type(1)),但是权重要低于后者
- [attribute^=value]：选择该属性以特定值开头的元素
- [attribute$=value]：选择该属性以特定值结尾的元素
- [attribute*=value]: 选择该属性中出现了特定值的元素
- :first-of-type与:last-of-type:第一个这个类型的/最后一个这个类型
- :only-of-type:选择仅仅仅有一个此类型的子元素,不包含子元素的子元素;
- :only-child:选择仅有一个子元素的元素;  
- :nth-child(n):选择第n个子元素,可以结合选择器来限制
- :nth-last-child(n):倒数第n个子元素,可以结合选择器来限制
- :nth-of-type(n):nth-of-type计数过滤标签类型,而nth-child计数不过滤;
- :nth-last-of-type(n):与nth-of-type(n)相反
- :last-child:选取父元素中最后一个子元素
- :root:选择文档根节点- -相当于 html {},但是权重要比html高
- :empty:选择没有子元素的标签,额,这个一般没什么大用,因为文本节点也是节点,一般就是表格有空单元格,列表有空项,然后做点处理,用js选择空元素时这个挺有用的
- :target:设置活动的id的样式,其实就是浏览器路径上边缀着#什么,就选着什么
- :enabled与:disabled:用于表单元素是否可用的伪类;
- :not，::selection:被选中文本的样式;:checked:用于多选及单选被选中的伪类;
###伪类
1.动作伪类：:link :hover :focus :hover :active:focus

2.目标伪类：:target

3.语言伪类：:lang

4.状态伪类::checked :enabled :disabled :indeterminate

5.结构伪类::root，:nth-child() :nth-last-child()，:nth-of-type() :nth-of-last-type()
，:first-child，:first-child，:first-of-type，:only-of-child，:only-of-type，:empty

6.取反伪类::not()
## 清除浮动的几种方式，优缺点
####1、给父级设置高度
- 优点：简单，代码少
- 缺点：只适合固定高度的布局，需要精确高度，高度和父级div不一致时会出问题
####2、父级定义overflow：hidden
-优点：简单，代码少
- 缺点：不能和position配合使用，超出尺寸会被隐藏
####3、父级定义after和zoom
- 优点：兼容好，不宜出错
- 缺点：代买多，需要两句代码结合使用才能全部兼容
## 图片如何实现垂直剧中的
1、高=行高（height=line-height）

2、display：table和display：cell模拟table实现

3、绝对定位实现 top，left：50%，width，height：-原本宽高的一半

4、利用flex布局，align-items：center
## css hack你知道哪些？
属性前缀法(即类内部Hack)：例如 IE6能识别下划线"_"和星号" * "，IE7能识别星号" * "，但不能识别下划线"_"，IE6~IE10都认识"\9"，但firefox前述三个都不能认识。

选择器前缀法(即选择器Hack)：例如 IE6能识别*html .class{}，IE7能识别*+html .class{}或者*:first-child+html .class{}。

IE条件注释法(即HTML条件注释Hack)：针对所有IE(注：IE10+已经不再支持条件注释)： <!--[if IE]>IE浏览器显示的内容 <![endif]-->，针对IE6及以下版本： <!--[if lt IE 6]>只在IE6-显示的内容 <![endif]-->。这类Hack不仅对CSS生效，对写在判断语句里面的所有代码都会生效。
## 谈谈你对CSS盒模型的认识
- 标准模型和IE模型的区别?
  - 标准模型中 content 部分不包含其他部分
  - IE 盒子模型的 content 部分包含了 border 和 padding
- CSS是如何设置这两种模型?

- JS如何设置和获取盒模型对应的宽和高?

  文档没有溢出
  - body.scrollWidth：scrollWidth===clientWidth（可读可写）
  - body.scrollHeight：scrollHeight===clientHeight（可读可写）
  
  文档溢出
  - body.scrollWidth：可视窗口宽度+溢出的总距离（scrollLeft最大值）（可读可写）
  - body.scrollHeight：可视窗口高度+溢出的总距离（scrollTop最大值）（可读可写）
- 什么是优雅降级和渐进增强?
  - 渐进增强 progressive enhancement：针对低版本浏览器进行构建页面，保证最基本的功能，然后再针对高级浏览器进行效果、交互等改进和追加功能达到更好的用户体验。
  - 优雅降级 graceful degradation：一开始就构建完整的功能，然后再针对低版本浏览器进行兼容。

## 谈谈你对BFC的了解
- 什么是BFC?
BFC(Block formatting context)直译为"块级格式化上下文"。它是一个独立的渲染区域，只有Block-level box参与， 它规定了内部的Block-level Box如何布局，并且与这个区域外部毫不相干。
- 如何创建BFC?
浮动元素，绝对定位元素，非块级盒子的块级容器（例如inline-blocks，table-cells，and table-captions），以及overflow属性值不是“ visible”（visible是overflow的默认值）的块级盒子（视口除外），这些元素就会为他们的内容创建一个BFC。
- BFC使用场景?

   1、清除元素之间的影响
   - 如果想让一个元素不受另一个元素的影响，可以把其中一个元素放到BFC环境中。

   2、清除内部浮动元素对父级元素的影响

   3、创建自适应布局

# JS类

## DOM事件
- DOM事件级别有哪些?

  0级，1级，2级
- 描述DOM事件捕获和冒泡的具体流程?
  - 捕获事件：事件的处理将从DOM层次的根开始，而不是从触发事件的目标元素开始，事件被从目标元素的所有祖先元素依次往下传递。
  - 冒泡事件：事件冒泡从内到外 当前元素的相关行为click触发时，会导致它的所有上级元素相关行为触发 一直到document（也可以到window）
- `Event`对象的常见应用场景?
 e || window.event
      * e.type 事件类型
      
      * e.target || e.srcElement事件源
      
      * e.clientX 距离窗口的X轴坐标
      
      * e.clientY 距离窗口的Y轴坐标
      
      * e.pageX = e.pageX || (e.clientX + sLeft); 距离body的X轴坐标 
      
      * e.pageY = e.pageY || (e.clientY + sTop) 距离body的Y轴坐标
      
      * e.offsetX 距离当前元素的X轴坐标
      
      * e.offsetY 距离当前元素的Y轴坐标
      
      * e.stopPropagation() || e.cancelBubble = true 阻止冒泡传播
      
      * e.preventDefault() || e.returnValue = false 阻止默认行为
      
      * e.keyCode/e.which 键码值
      
      * e.key 键码符
      
      * e.wheelDelta 滚轮方向

- 事件委托是什么？

利用事件默认会进行冒泡传播的机制 给最外层元素相关行为绑定事件，当里面元素相关行为触发的时候 也会触发最外层元素的行为 然后我们可以根据事件对象中的事件源做出相应的处理
- 事件冒泡,e.target和e.currentTarget的区别

  event.currentTarget指向事件所绑定的元素，而event.target始终指向事件发生时的元素
- 浏览器的兼容问题(js)

## JS原生
- JS中有哪些数据类型
  - 基本数据类型：Number,Boolean,Null,Undefined,String
  - 引用数据类型：Object
- 什么是闭包？闭包作用？在工作中是如何应用的?
  - 闭包：函数执行都会形成一个私有作用域 保护里面私有变量不受外界干扰 这种保护机制叫闭包
  - 作用：可以读取函数内部的变量，可以避免全局污染，方便封装
  - 如何应用：采用函数引用方式的setTimeout调用；将函数关联到对象的实例方法；封装相关的功能集。
- JS实现继承的几种方式?
    1、类式继承；
    
    2、构造函数继承；
    
    3、组合继承；
    
    4、原型式继承；
    
    5、寄生式；
    
    6、寄生组合式继承。
- 创建对象的三种方式?
  字面量创建 ，构造函数创建 ，通过object创建
- `new Person()`时发生了什么?

(1) 创建一个新对象；

(2) 将构造函数的作用域赋给新对象（因此 this 就指向了这个新对象） ；

(3) 执行构造函数中的代码（为这个新对象添加属性） ；

(4) 返回新对象。
- 什么是深拷贝和浅拷贝？自己不用`JSON.parse`实现一个深拷贝的方法

- 手工模拟完整的bind方法
- 什么是节流和防抖？
- 上拉刷新和下拉加载的实现原理？
- 写一个验证邮件的正则表达式
- 事件绑定和普通事件的区别（可以举例说明）
- javascript 模版引擎用过哪些？实现原理是什么？
- 合并两个对象
- 动态向一个div中插入1000个div标签，如何实现？（考性能）
- html5新特性
- 严格模式和非严格模式的区别
- 对于js中浮点数计算会丢失精度的问题，你有什么解决思路？

## JQuery
- jquery.extend , jquery.fn.extend的区别
- 谈一下jquery中的bind，live，delegate，on区别
- document.ready和document.load和$(function(){})有什么区别？
- $.data()和$('#aaa').data()各自作用是什么？有什么区别

## ES6
- 什么时候应该用箭头函数？什么时候不能用？
－ 请写出ES6中Array.isArray()的实现代码
- 如何在项目中解析处理es6和es7代码
- Promise常用方法，Promise.race的作用，then方法里reject和catch的区别

## 工程化
- 什么叫模块化？你用过哪些模块化解决方案？
- 什么叫组件化？你在工作中是如何实现组件化的？
- gulp和webpack的相同点和不同点?
- 什么是热加载?

## 框架
- 前端路由的实现原理
- `MVVM`框架解决了什么问题？带来了什么问题？
- 浏览器地址栏里面的'＃' 如何清楚？mode共有几个参数，参数有什么区别？
- vue中父组件如何给子组件传递值
- react的优缺点
- React组件中props和state有什么区别？
- 什么是JSX
- 说一下angular、vue、react的相同点和不同点?各适用于什么样的项目场景?
- React中不同组件传递数据的方式有哪些？至少说出三种
- 请描述React的组件加载生命周期函数以及`shouldComponentUpdate`方法的实际使用场景?

## HTTP
- HTTP报文的组成部分
- GET和POST的区别
- HTTP常见状态码
- 什么是Restful API?
- HTTPS和HTTP的区别是什么?
- 从在浏览器中输入URL到页面渲染出来都经过了什么过程？
- JSON和JSONP 区别是什么？JSONP的原理是？
- 用过那些跨域技术
- ajax的参数

## 前后端通信
- 什么是同源策略及限制?
- 前后端如何通信?
- 用原生JS模拟一下`jquery`的`ajax`方法
- 跨域通信的几种方式?

## 安全
- `CSRF`的原理以及如何防御
- `XSS`的原生和如何防御

## 渲染机制
- 什么是`DOCTYPE`及作用?标准模式和兼容模式有什么区别?
- 浏览器是如何渲染页面的?
- 什么是重排？什么时候会触发重排?
- 什么是重绘？什么时候会触发重绘?

## JS运行机制
- 如何理解JS的单线程
- 什么是`Event Loop`,请简述其过程

## 服务器
- 如何在web应用中在实现权限控制?
- Web服务器、应用服务器、Web容器、反向代理服务器的区别和联系?

## 错误处理
- 前端错误的分类?
- 程序出现bug了，你是如何调试的?
- 如何分类捕获不同的错误?
- 如何把生产环境的错误上报？

## 页面性能
- 前端性能优化的方法有哪些？至少说出10种以上
- 如何实现JS的异步加载? `async`和`defer`的区别是什么?

## 缓存
- Expires和Cache-Control是如何工作的？
- Last-Modified和Etag是如何工作的？
- 请描述`cookie`、`sessionStorage`和`localStorage`的区别

# 项目问题
- 介绍一下你的项目？这个项目有哪些模块？你负责哪些模块？
- 你在项目中的角色
- 你觉得在项目中做的最出彩的点有哪些？
- 遇到过哪些非常难以解决的问题？最终是如何解决的？
- 如果你是项目负责人，你会如何分配任务？如何保证按时完成？如何让成员够持续成长？

# 正常非技术问题
- 请你自我介绍一下你自己？
- 你觉得你个性上最大的优点是什么？
- 说说你最大的缺点？
- 你对加班的看法？
- 在五年的时间内，你的职业规划？
- 你朋友对你的评价？
- 你还有什么问题要问我的吗？
- 你的业余爱好是什么？
- 你为什么从上家公司离职?

# 故意挖坑的问题
- 你的直属上级和顶级上级对一件事情的意见不一致，你会听谁的意见？
- 如果部门开发的时候和你的主管发生了争吵，你会如何处理？
- 与上级意见不一致，你将怎么办？
- 你喜欢跟什么样的主管共事？
- 我们为什么要聘用你?
- 你没有工作经验如何能胜任这份工作？
- 你最崇拜的人是谁?
- 你有创业的想法吗？

## 代码运行结果，并解释
```javascript
if(!("a" in window)){
  var a = 1;
}
console.log(a);
```

```javascript
function MyObj(){
  this.p.pid++;
}
MyObj.prototype.p = {'pid':0}
MyObj.prototype.getNum = function(num){
  return this.p.pid+num;
}
var _obj1 = new MyObj();
var _obj2 = new MyObj();
console.log(_obj1.getNum(1)+_obj2.getNum(2))
```

```javascript
var func = (function(a){
  this.a = a;
  return function(a){
    a+=this.a;
    return a;
  }
})(function(a,b){
  return a;
}(1,2));
func(4);
```


```javascript
function Foo() {
 getName = function () { alert (1); };
 return this;
}
Foo.getName = function () { alert (2);};
Foo.prototype.getName = function () { alert (3);};
var getName = function () { alert (4);};
function getName() { alert (5);}

//请写出以下输出结果：
Foo.getName();
getName();
Foo().getName();
getName();
new Foo.getName();
new Foo().getName();
new new Foo().getName();
```


```javascript
for(var i=0;i<10;i++){
       alert(i);
       break;
   }
   alert(i);

   for(var i=0;i<10;i++){
      continue;
      alert(i);
   }
   alert(i)
```

```javascript
function C1(name){
	if(name) this.name = name;
}
function C2(name){
this.name =name;
}
function C3(name){
 this.name = name ||'join';
}
C1.prototype.name='Tom';
C2.prototype.name='Tom';
C3.prototype.name='Tom';
alert(new C1().name)+(new C2().name)+(new C3().name);

```

```javascript
var a=1;
Var obj ={
   “name”:”tom”
}
function fn(){
   var a2 = a,
   obj2 = obj,
   a2 =a,
   obj2.name =”jack”
}
fn();
console.log(a);
console.log(obj);
```

每个人必须建立自己的github地址将答案，放到github上，并且将答案抄在纸上（加深记忆 防止粘贴），晚上之前必须`每个人`都交上来，大家不许互相讨论，可以采用google和百度等手段，
目的：校验自己的不足查缺补漏，学会自我查找问题，提升解决问题的能力。
