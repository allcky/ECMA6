# const命令
### const命令介绍
const是用来声明一个只读的常量。只要声明后，常量的值就不能改变，否则报错。
```javascript
const PI = 3.1415926;
console.log(PI);
PI = 3; //error  Assignment to constant variable  常量不能赋值
```
*注意：conset因为声明后值不能改变，因此声明的常量时必须赋值。* 如下:
```javascript
const num; //Missing initializer in const declaration
```

### const作用域
const命令也是有作用域的只有在当前声明的作用域中生效。
```javascript
//函数作用域
(function(){
    const val = 100;
    alert(val)
})();
alert(val);

//块级作用域
{
    const port = 80;
    alert(port)
}
alert(port)
```
### const不存在变量提升
const命令声明变量，只能在声明之后访问。不存在变量提升。  
[ 不会预解析const，因此const只有执行的时候才会在内存中创建该常量 ]
```javascript
alert(val); //error  val is not defined
const val = 100;
```
### const不能重复声明
只要通过var、let、const声明的变量，不能再次声明，比如：
```javascript
//var const
var num = 100;
const num = 200; //error  Identifier 'num' has already been declared 标识符“num”已被声明

//let const
let val = 1;
const val = 20; //error Identifier 'val' has already been declared 标识符“val”已被声明

//var let
var n = 10;
let n =300; //error Identifier 'val' has already been declared 标识符“n”已被声明
```
### const命令与变量引用类型
const声明的变量对于引用类型的数据，只是指向其地址，不会指向数据。因此，const只能保证指向内存地址不变化，不能保证变量数据不变。
```javascript
//Obect
const foo = {
    name:'张三',
    age:29
}
foo.name = "lisi"; //修改对象foo的name值 没有报错
console.log(foo);  //{name: "lisi", age: 29}
alert(foo.name);   //lisi

//Array
const nums = [];
nums.push(10);//success
nums.push(20);//success
console.log(nums); // [10,20]
nums = ['a','b','c']; //error
```
##### 保证引用类型数据不变
当我们要保证对象的数据不能修改，我们可以使用`Object.freeze()`方法来确保对象的数据不变。
```javascript
const foo = Object.freeze({name:'zhangsan',age:29});
foo.name = 'lisi'; // 未报错
console.log(foo); //修改未生效 {name: "zhangsan", age: 29}
```
