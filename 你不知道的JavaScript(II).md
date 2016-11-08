##You Don't Konw Javascript(II)  

###一.类型和语法  

####1.类型  

* 内置类型：null undefined boolean number string object symbol(es6)； 
* typeof null==='object'  typeof function(){}==='funciton'(funciton是object的子类型)；
* undefined != undeclared，由于typeof的安全防范机制，所以没声明的也不会报错，都返回undefined。  

####2.值  

* 数组通过数字进行索引，但有趣的是它们也是对象，所以也可以包含字符串键值和属性（但这些并不计算在数组长度内）；
* 类数组转换：Array.prototype.slice.call(arguments)；es6中可用Array.from()；
* 字符串不可变是指字符串的成员函数不会改变其原始值，而是创建并返回一个新的字符串；而数组的成员函数都是在其原始值上进行操作。
* toExponential() 指数格式  toFixed() 小数部分的显示位数  toPrecision() 有效数位的显示位数
* 可以使用 Number.EPSILON 来比较两个数字是否相等（在指定的误差范围内return Math.abs( n1 - n2 ) < Number.EPSILON）； 
* 整数检测(es6)：Number.isInteger()；  
是否安全(es6)：Number.isSafeInteger()；
* undefined 指从未赋值；null 指曾赋过值，但是目前没有值；null 是一个特殊关键字，不是标识符，我们不能将其当作变量来使用和赋值。然而undefined 却是一个标识符，可以被当作变量来使用和赋值。
* typeof NaN==='number' NaN!=NaN；es6中Number.isNaN()判断是否NaN；
* JavaScript 对值和引用的赋值 / 传递在语法上没有区别，完全根据值的类型来决定。

####3.原生函数  
* new String("abc") 创建的是字符串 "abc" 的封装对象，而非基本类型值 "abc" ；
* 如果想要得到封装对象中的基本类型值，可以使用 valueOf() 函数；
* 建议使用常量形式（如 /^a*b+/g ）来定义正则表达式，这样不仅语法简单，执行效率也更高，因为 JavaScript 引擎在代码执行前会对它们进行预编译和缓存；
* 创建日期对象必须使用 new Date()；Date()返回日期字符串；
* 对于简单标量基本类型值，比如 "abc" ，如果要访问它的 length 属性或 String.prototype方法，JavaScript 引擎会自动对该值进行封装（即用相应类型的封装对象来包装它）来实现对这些属性和方法的访问。

####4.强制类型转换  
* 类型转换发生在静态类型语言的编译阶段，而强制类型转换则发生在动态类型语言的运行时（runtime）；
*  ToString负责处理非字符串到字符串的强制类型转换；
####5.语法
