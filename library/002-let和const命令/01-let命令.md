# let命令
### let 命令介绍
ES6新增了let命令，用来声明变量。用于与var类似，用于声明变量。let声明的变量只会在let所在的代码块中生效。
```
{
    let num1 = 10;
    var num2 = 20;
    alert(num1); // 10
}
alert(num1); //undefined num1只会在其所在代码块作用域中生效
alert(num2); //20
```

----------------
### for循环中使用let定义变化值
在这个案例中通过let声明变量i，i只会在循环体内生效，循环体外访问报错。
```
for(let i =0;i<10;i++){
    console.log(i); // 0 ~ 9
}

alert(i); // undefined
```

---------------------
### for循环中变量i值问题
var方式声明循环变量i：
通过var声明变量i是一个全局变量，所以最后我们调用函数，访问i的时候得到的结果就是i最后的结果10。
```
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
```
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
```
alert(num);  //var声明 undefined
alert(name); //报错
var num = 10;
let name  = 'Acker'
```
