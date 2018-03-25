# js
###问题： js中使用typeof 能得到的哪些类型

typeof undefined //undefined

typeof 'abc'  //string

typeof 123 //number

typeof true // boolean

typeof {} //object 

typeof [] //object

typeof null //object

typeof consolr.log //function

###问题：js中有哪些内置函数--数据封装类对象

Object

Array

Boolean

Number

String

Function

Date

RegExp

Error

//js变量按照存储方式区分为哪些类型，并描述其特点

//值类型

var a =10

var b=a

a =11

console.log(b) //10

//引用类型

var obj1={x:100}

var obj2=obj1

obj1.x=200

console.log(obj2.x)

//问题：如何理解JSON

//JSON是一个js的对象

JSON.stringify({a:10,b:20})

json.parse('{a:10,b:20}')

### 问题：js中有哪些内置函数-数据封装内函数

Object

Array

Boolean

Number

String

Function

Date

RegExp

Error

### js变量按照存储方式区分为哪些类型，并描述其特点

#### 值类型

    var a= 10
    
    var b=a
    
    a=11
    
    console.log(b)//20
    
    
    //引用类型
    
    var obj1={x:100}
    
    var obj2=obj1
    
    obj1.x=200
    
    console.log(obj2.x)//200
    

### 如何准确判断一个变量是数组类型

判断一个变量是否为‘数组’

var a=[];

a instanceof Array

返回true

### 写一个原型链继承的列子

//动物

function Animal(){


this.eat=function(){
  

console.log('animal eat')



}



}

//狗

function Dog(){


this.bark=function(){



console.log('dog bark')



}
   

}

Dog.prototype = new Animal()

var hashiqi = new Dog()


### 描述new一个对象的过程

创建一个新对象

this指向这个新对象

指向代码，即对this赋值

返回this


### zepto(或其他框架)源码中如何使用原型链

#### 知识点

构造函数


function Foo(name,age){



this.name=name
    

this.age=age
    

this.class ='class-1'



}
  

var f= new Foo('zhangsan',20)
  

var f= new Foo('lisi',22)
   
构造函数 - 扩展


var a={} 其实是var a= new Object()的语法糖
   

var a=[]其实是var a = new Array()的语法糖
   

function Foo(){...}其实是var Foo = new Function(...)
   

使用instanceof判断一个哈去念书是否是一个变量的构造函数
   
原型规则和示例
   

所有的引用类型（数组、对象、函数），都具有对象特性，即可自由扩展属性（除了“null”意外）
   

var obj = {}; obj.a=100
   

var arr=[]; arr.a=100;



function fn(){}
   

fn.a=100;
   

所有的引用类型（数组、对象、函数）都有一个__proto__（隐世原型）属性，属性值是一个普通的对象
   

console.log(obj.__proto__)
   

console.log(arr.__proto__)
   

console.log(fn.__proto__)
   

所有的函数，都有一个prototype（显示原型）属性，属性值也是一个普通的对象
   

console.log(fn.prototype)
   

所有的引用类型（数组、对象、函数），__proto__属性值指向它的构造函数的“prototype”属性值
   

console.log(obj.__proto__===Object.prototype)    
     
原型链
  

当试图得到一个对象的某个属性时，如果这个对象本身没有这个属性，那么回去它的__proto__(既他的构造函数的prototype)中寻找
  

//构造函数
  

function Foo (name,age){
  

this.name=name
    

}

Foo.prototype.alertName=function(){
  

alert(this.name)
    

}

//创建实例

var f= new Foo('zhangsan')
  

f.printName=function(){ 
  

console.log(this.name)
    

}
  

//测试
  

f.pringName()
  

f.alertName()

instanceof

f instanceof Foo的判断逻辑是：

f的__proto__一层一层网上，能否对应到Foo.prototype

再试着判断 f instanceof object

### 循环对象自身的属性

var item

for(item in f){

if(f.hasOwnProperty(item)){
  

console.log(item)
    

}
  
}

### 实战中原型

function Elem(id){


this.elem=document.getElementById(id)
  
}

Elem.protype.html=function(val){


var elem = this.elem
  

if(val){
  

elem.innerHTML=val
    

}
  
}else{


return elem.innerHTML
   
}

Elem.prototype.html=function(val){


var elem = this.elem
    

if(val){
    

elem.innerHTML=val
       

return this //链式操作  
       

}else{
    

return elem.innerHTML
       

}
    
}


Elem.prototype.on=function (type,fn){


var elem = this.elem
   

elem.addEventListener(type,fn)
   
}

var div=new ELem('div')

### 执行上下文


范围：一段<script>或者一个函数
    

全局：变量定义、函数声明
 

函数：变量定义、函数声明、this、arguments
 
### this

作为构造函数执行

function Foo(name){


this.name=name
  

return this
  
}

var f = new Foo('zhangsan')

作为对象属性执行

var obj={


name:'A',
  

pringtName:function(){
  

console.log(this.name)
     

}
  
}

作为普通函数执行

function fn(name){


console.log(this)
   
}


fn('zhangsan')
 
call apply bind

function fn(name){


console.log(this)
   
}

fn.call({x:100},'zhangsan')

function fn(name){


console.log(this)
   
}

fn.apply({x:100},['zhangsan','haha'])

var fn1=function (name) {


console.log(this)
   
}.bind({y:200})

### 作用域

//无块级作用域

if(true){


var name='zhangsan'
  
}

console.log(name)

//函数和全局作用域

var a=100

function fn(){


var a=200
  

console.log('fn',a)
  
}

console.log('gloabal',a)

### 作用域链

 var a=100;
 

function fn(){
 

var b=200
    
    //当前作用域没有定义的变量，即"自由变量"
    

console.log(a)
    

console.log(b)
 

}

### 闭包

这个函数内定义了变量

全局变量无法修改函数内的变量

### 如何理解作用域 

自由变量

作用域链，即自由变量的查找

闭包的两个场景

### 闭包世界应用中主要用于封装变量，收敛权限

function isFirstLoad(){

var _list = []

return function (id){

if(_list.indexOf(id)>=0){

return fasle

}else{

_list.push(id)

return true

}

}

}

var firstLOad=isFirstLoad()

firstLoad(10) //true

firstLoad(10) //false

firstLoad(20) //true

## 异步和单线程

### 什么是异步（对比同步）

异步

console.log(100)

setTImeout(function(){

console.log(200)

},1000)

console.log(300)

同步

console.log(100)

alert(200)

console.log(300)

### 前段使用异步的场景

定时任务：setTimeout，setInverval

网络请求：ajax请求，动态<img>加载

console.log('start')

$.get('./data1.json',function(data1){

console.log(data1)

})

console.log('end')

console.log('start')

var img=document.createElement('img')

img.onload=function(){

console。log('loaded')

}

img.src="/xxx.png"

console.log('end')

事件绑定

console.log('start')

document.createElement('img').onclick=function(){

alert('sdads')

}

console.log('end')

### 异步和单线程

console.log(100)

setTImeout(function(){

console.log(200)

},1000)

console.log(300)

执行第一行，打印100

执行setTimeout后，传入setTimeout的函数会被暂停存起来不会立即执行（单线程的特点，不能同时干两件事）

执行最后一行，打印300

待所有的程序执行完，处于空闲状态时，会立马看有没有暂存起来的要执行

发现暂存起来的setTimeout中的函数无需等待时间，就立即来过来执行

### 同步和异步的区别是什么

同步会阻塞代码执行，而异步不会

alert是同步，setTimeout是异步 


获取2017-06-10格式的日期

new Date()

获取随机数，要求市场都一直的字符串格式

Math.random()

写一个能遍历对象和数组的通用forEach函数

数组Api

forEach 遍历所有元素

eveny判断所有元素是否都符合条件

some判断是否有至少一个元素符合条件

sort排序

map对元素重新组装，生成新数组

filter过滤符合条件的一元素

对象api

var obj={

x:100,

y:200,
 
z:300

}
var key

for (key in obj) {
   
if (obj.hasOwnProperty(key)) {
 
console.log(key,obj[key])

}

}
