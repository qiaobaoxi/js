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
