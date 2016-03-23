#块级作用域

## 1、ES6必须在严格模式下才可以正常使用；
#### 严格模式和普通模式的区别
    - 1、严格模式会将JavaScript陷阱直接变成明显的错误
    - 2、严格模式修正了一些引擎难以优化的错误,同样的代码有些时候严格模式会比非严格模式下更快。
    - 3、严格模式禁用了一些有可能在未来版本中定义的语法。
    
#### 因为我们使用ES6时候，必须在严格模式下才可以正常使用，不会报错；
    - 严格模式可以应用到整个script标签或某个别函数中。
    
    - 1、为整个script标签开启严格模式； 需要在所有语句之前放一个特定语句 "use strict"; （或 'use strict';）
    // 整个语句都开启严格模式的语法
    "use strict";
    let v = "Hi!  I'm a strict mode script!";
    
    - 2、要给某个函数开启严格模式，得把 "use strict"; (或 'use strict'; )声明放在函数体所有语句之前。
    // 函数级别严格模式语法
    function strict(){
      'use strict';
      return "Hi!  I'm a strict mode function!" ;
    }
    
    function notStrict() { 
      return "I'm not strict.";
    }
    
## 2、let的使用（var的升级版）
    ES6里增加了一个let，可以在{}， if， for里声明。用法同var，但作用域限定在块级，let声明的变量不存在变量提升（var有变量提升的效果）；
    let 允许把变量的作用域限制在块级域中。与 var不同处是：var 申明变量要么是全局的，要么是函数级的，而无法是块级的。
    
##### let vs var     （let的作用域是块，而var的作用域是函数）
    'use strict';
    var a = 5;
    var b = 10;
    if (a === 5) {
      let a = 4; // 这个作用域在if的作用域里；
      var b = 1; // 这个作用域是在栈内存里的；
      console.log(a);  // 4
      console.log(b);  // 1
    } 
    console.log(a); // 5
    console.log(b); // 1
    
##### let在循环中 （可以使用let关键字绑定变量在循环的范围；而不是使用一个全局变量(使用var)定义。）

    'use strict';
    for (let i = 0; i < 10; i++) {
      console.log(i); // 0, 1, 2, 3, 4 ... 9
    }
    console.log(i); // i is not defined
    上面报错，因为变量i不存在于for语句外的作用域中。let创建块级作用域变量的，使用var创建一个全局变量。
## 3、const的用法（常量不可以被重新赋值,并且不能被重复声明.）

    const这个声明创建一个常量,可以全局或局部的函数声明。
    
    一个常量可以是全局的或者是局部的,常量遵循与变量相同的作用域规则。
    
    一个常量不可以被重新赋值,并且不能被重复声明.所以,虽然可以在声明一个常量的时候不进行初始化,但这样做是没有意义的,因为这个常量的值永远会保持undefined。
    
    一个常量不能和它所在作用域内的其他变量或函数拥有相同的名称。
    
    下面的例子演示了常量的行为。
    const num = 10;
    num =20;
    console.log(num); // 10
    
    如果我们在上面声明常量num，在声明var num，这时会报错，num已经声明。
    const num = 10;
    var num = 20;
    console.log(num); // 'num' has already been declared
    
## 4、块级作用域  （let声明可以把作用域限制在块级，同时const可以保证常量不被重复赋值和声明）
    很多语言中都有块级作用域，JavaScript使用var声明变量，以function来划分作用域，大括号“{}” 却限定不了var的作用域。用var声明的变量具有变量提升（declaration hoisting）的效果。
    
    ES6里增加了一个let，可以在{}， if， for里声明。用法同var，但作用域限定在块级，let声明的变量不存在变量提升。
    'use strict';
    function f1() {
      var a = 1;
      let n = 2;
      if (true) {
          var a = 20;
          let n = 10;
      }
      console.log(n); // 2
      console.log(a); // 20
    }
    f1();