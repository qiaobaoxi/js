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


