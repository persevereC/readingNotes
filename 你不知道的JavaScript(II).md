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
* ToString负责处理非字符串到字符串的强制类型转换；  
JSON.stringify(..) 在对象中遇到 undefined 、 function 和 symbol 时会自动将其忽略，在数组中则会返回 null （以保证单元位置不变）； 如果对象中定义了 toJSON() 方法，JSON 字符串化时会首先调用该方法，然后用它的返回值来进行序列化。 toJSON() 应该“返回一个能够被字符串化的安全的 JSON 值” ，而不是“返回一个 JSON 字符串” 。可以向 JSON.stringify(..) 传递一个可选参数 replacer，它可以是数组或者函数，用来指定对象序列化过程中哪些属性应该被处理，哪些应该被排除，和 toJSON() 很像;
* 假值：undefined null false +0  -0 NaN ""；
* 日期转时间戳：Date.now()；
* 如果 indexOf(..) 返回 -1 ， ~ 将其转换为假值 0 ，其他情况一律转换为真值；
* parseInt(..) 针对的是字符串值，返回整数；
* 如果 + 的其中一个操作数是字符串（或者通过以上步骤可以得到字符串），则执行字符串拼接；否则执行数字加法。
* 对于 || 来说，如果条件判断结果为 true 就返回第一个操作数（ a 和 c ）的值，如果为false 就返回第二个操作数（ b ）的值；  
&& 则相反，如果条件判断结果为 true 就返回第二个操作数（ b ）的值，如果为 false 就返回第一个操作数（ a 和 c ）的值；
* == 允许在相等比较中进行强制类型转换，而 === 不允许；
*  如果 Type(x) 是数字， Type(y) 是字符串，则返回 x == ToNumber(y)的结果；  
如果 Type(x) 是字符串， Type(y) 是数字，则返回 ToNumber(x) == y的结果；
* if(!!a){}和if(Boolean(a)){}避免了布尔值的宽松相等；
* 如果 x 为 null(undefined) ， y 为 undefined(null) ，则结果为 true；
* 如果 Type(x) 是字符串或数字， Type(y) 是对象，则返回 x == ToPrimitive(y)的结果；  
如果 Type(x) 是对象， Type(y) 是字符串或数字，则返回 ToPromitive(x) == y的结果。
* "0" == false; false == 0; false == ""; false == []; "" == 0; "" == []; 0 == []

####5.语法
* [] + {}; // "[object Object]" []看做''，{}强制转换为[object Object]； 
{} + []; // 0   {} 被当作一个独立的空代码块（不执行任何操作），+ [] 将 [] 显式强制类型转换为0；
* && 运算符先于 || 执行，而且执行顺序并非我们所设想的从左到右；
* 自动分号插入（ASI）只在换行处起作用， do..while 循环后面必须带 ; ，而 while 和 for 循环后则不需要，break、continue、return和yield（ES6）等关键字；
* 暂时性死区（TDZ）指的是由于代码中的变量还没有初始化而不能被引用的情况；
* 向函数传递参数时， arguments 数组中的对应单元会和命名参数建立关联（linkage）以得到相同的值；相反，不传递参数就不会建立关联；
* 如果 finally 中抛出异常（无论是有意还是无意），函数就会在此处终止；finally 中的 return 会覆盖 try 和 catch 中 return 的返回值；
* JavaScript 中有很多错误类型，分为两大类：早期错误（编译时错误，无法被捕获）和运行时错误（可以通过 try..catch 来捕获） 。所有语法错误都是早期错误，程序有语法错误则无法运行。
