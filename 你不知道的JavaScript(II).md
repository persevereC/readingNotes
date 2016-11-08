##You Don't Konw Javascript(II)
###一.类型和语法
####1.类型
* 内置类型：null undefined boolean number string object symbol(es6)； 
* typeof null==='object'  
  typeof function(){}==='funciton'(funciton是object的子类型)；
* undefined != undeclared，由于typeof的安全防范机制，所以没声明的也不会报错，都返回undefined。
####2.值
* 数组通过数字进行索引，但有趣的是它们也是对象，所以也可以包含字符串键值和属性（但这些并不计算在数组长度内）；
* 类数组转换：Array.prototype.slice.call(arguments)；es6中可用Array.from()；
* 字符串不可变是指字符串的成员函数不会改变其原始值，而是创建并返回一个新的字符串；而数组的成员函数都是在其原始值上进行操作。
* toExponential() 指数格式  
toFixed() 小数部分的显示位数  
toPrecision() 有效数位的显示位数
* 可以使用 Number.EPSILON 来比较两个数字是否相等（在指定的误差范围内return Math.abs( n1 - n2 ) < Number.EPSILON）； 
* 整数检测(es6)：Number.isInteger()；  
  是否安全(es6)：Number.isSafeInteger()；
* undefined 指从未赋值；null 指曾赋过值，但是目前没有值；null 是一个特殊关键字，不是标识符，我们不能将其当作变量来使用和赋值。然而
undefined 却是一个标识符，可以被当作变量来使用和赋值。
* typeof NaN==='number' NaN!=NaN；es6中Number.isNaN()判断是否NaN；
* JavaScript 对值和引用的赋值 / 传递在语法上没有区别，完全根据值的类型来决定。
####3.原生函数
####4.强制类型转换
####5.语法
