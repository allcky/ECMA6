# let命令
### let 命令介绍
##### let 与 var
ES6新增了let命令，用来声明变量。用法与var类似，用于声明变量。let声明的变量只会在let所在的块级作用域中生效。
```javascript
{
    let num1 = 10;
    var num2 = 20;
    alert(num1); // 10
}
alert(num1); //undefined num1只会在其所在代码块作用域中生效
alert(num2); //20
```
##### JavaScript中作用域
javascript作用域分为全局作用域、函数作用域，还有块级作用域。   
函数作用域与块级作用域的区别是什么？   
- 函数作用域：变量在定义的函数内以及嵌套的子函数内可访问
- 块级作用域：{}就属于块级作用域,变量在离开定义的块级作用域后马上被收回

有了块级作用域后函数自调用不再需要了，自调用解决的问题就是我们需要一个创建一个独立作用域
```javascript
//自调用函数
(function(){
    var a = 100;
    alert(a)//100
})
alert(a); // error a is not defined

//块级作用域
{
    let a = 10;
    alert(a);// 10
}
alert(a);// error a is not defined
```
----------------
### for循环中使用let定义变化值
在这个案例中通过let声明变量i，i只会在循环体内生效，循环体外访问报错。
```javascript
for(let i =0;i<10;i++){
    console.log(i); // 0 ~ 9
}

alert(i); // undefined
```

---------------------
### for循环中变量i值问题
var方式声明循环变量i：
通过var声明变量i是一个全局变量，所以最后我们调用函数，访问i的时候得到的结果就是i最后的结果10。
```javascript
var arr =[];
for(var i=0;i<10;i++){
    arr[i] = function(){
        alert(i);
    }
}
arr[0](); //10
```
let方式声明循环变量i：
通过let声明的变量i，当前的i只在本轮循环中生效，每次循环都是一个新变量i，所以最终结果 0。
```javascript
var arr =[];
for(let i=0;i<10;i++){
    arr[i] = function(){
        alert(i);
    }
};
arr[0]();// 0
```

-----------
### 使用let声明注意问题
#### 不存在变量提升问题
通过var方式声明变量的时候存在变量提升问题,通过let方式声明的变量不存在变量提升问题
```javascript
alert(num);  //var声明 undefined
alert(name); //报错
var num = 10;
let name  = 'Acker'
```
#### 不允许重复声明
let不允许在相同作用域中声明相同变量。
```javascript
{
    let num = 10;
    let num = 1000; //报错
}
```
let在函数中声明变量不能与形参相同
```javascript
function get(val){
    let val = 100; //报错
    //Identifier 'val' has already been declared
    //标识符 val 已被占用
}
```
#### 块级作用域的嵌套
块级作用域嵌套后在子作用域中可以访问到父级块中的变量。
```javascript
{
    let num = 100;
    {
        console.log(num); //100
    }
}
```
块级作用域中声明的变量、在块级作用域结束后销毁
```javascript
{
    let num = 100;
    {
        let num = 200;
        console.log(num);//200
    }
    console.log(num)//100
}
```
