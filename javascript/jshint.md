#JSHint

##Introduction
JSHint 是一个 JavaScript 的代码质量检查工具，主要用来检查代码质量以及找出一些潜在的代码缺陷。

项目主页: [http://jshint.com/](http://jshint.com/)  

GitHub: [https://github.com/jshint/jshint](https://github.com/jshint/jshint)


##Usage

1. 安装jshint

    ```
    $ npm install jshint -g
    ```

2. 检查代码

    ```
    $ jshint source.js
    ```

##Options

###enforcing options
 
#### * bitwise
    
    作用：值为true时，禁止使用位操作符，如'^', '|', '&'等.
    
#### * camelcase
  
    作用：值为true时，所有的变量名必须使用驼峰风格(如"loginStatus")或UPPER_CASE风格(如"LOGIN_STATUS").
    
#### * curly
    
    作用：值为true时，不能省略循环和条件语句后的大括号.
    
    备注：如"if (con) ..."，需要写成"if (con) { ... }".
    
#### * eqeqeq
    
    作用：值为true时，禁止使用"=="和"!="，而应该使用"==="和"!==".
    
#### * es3
    
    作用：值为true时，表示你的代码需要遵守ECMAScript 3规范.
    
#### * forin
    
    作用：值为true时，在所有"for in"循环中，必须使用hasOwnPropery过滤掉对象继承来的成员.

#### * freeze

    作用：值为true时，禁止覆盖原生的对象,如Array, Date等的原型.
    
#### * immed
    
    作用：值为true时，表示立即执行函数必须包裹在括号内.

#### * indent
    
    作用：该选项要求你的代码必须使用指定的缩进宽度，如"indent:4".
    
#### * latedef
    
    作用：值为true时，禁止在变量定义之前使用它.
    
#### * newcap
    
    作用：值为true时，构造函数名需要大写. 
    
    备注：经测试，该选项是否激活，JSHint都不会检查构造函数名.
    
#### * noarg
    
    作用：值为true时，禁止使用arguments.caller与arguments.callee.
    
#### * noempty
    
    作用：值为true时，不允许代码中出现空的语句块（"{}"）.
    
#### * nonew
    
    作用：值为true时，禁止使用产生副作用的构造器调用方式，如"new MyConstructor();".
    
#### * plusplus
    
    作用：值为true时，禁止使用一元递增（"++"）和递减（"--"）运算符.
    
#### * quotmark
    
    作用：该选项用于统一代码中的引号风格，可选的值有三个：
          (1) single -- 只能使用单引号；
          (2) double -- 只能使用双引号；
          (3) true   -- 两者任选其一，但不能同时出现.
    
#### * undef
    
    作用：值为true时，禁止使用未定义的变量.
    
#### * unused
    
    作用：该选项激活后，对于"已定义却未使用的变量"会给出警告，可选的值有三个：
          (1) vars -- 只检查变量，不检查函数形参；
          (2) strict -- 检查变量和函数形参；
          (3) true -- 检查变量和函数形参，但允许这种情况：一个未使用的形参后紧随一个被使用的形参.
          
    示例：strict与true的区别
          (1) strict
              function show(x,y) {alert(y);}  // jshint校验结果：'x' is defined but never used
              show(1);
          
          (2) true
              function show(x,y) {alert(y);} // jshint校验结果：pass
              show(1); 
        
#### * strict
    
    作用：值为true时，该选项会要求所有函数在ECMAScript 5的严格模式中运行.
    
    备注：该选项激活后，仅在函数作用域中启用严格模式（如果在全局作用域中启用，可能会影响页面中的第三方JS）.

#### * trailing

    作用：值为true时，禁止在代码的末尾出现空白.
    
#### * maxparams

    作用：该选项用于设置每个函数形参数量的上限，如"maxparams:3".
    
#### * maxdepth

    作用：该选项用于设置每个函数中代码块嵌套层级的上限，如"maxdepth:1".
    
    示例：/* jshint maxdepth:1 */
          function show() {
            if (1) {
              if (2) { // jshint校验结果：Blocks are nested too deeply. (2)
                alert('the second nested');
              }
            }
          }
    
#### * maxstatements

    作用：该选项用于设置每个函数中语句数量的上限，如"maxstatements:4".
    
    备注：函数声明被看作一个语句.
    
    示例：/* jshint maxstatements:4 */
          function main() { // jshint校验结果：This function has too many statements. (5)
            var i = 0;
            var j = 0;

            // 函数声明被看作一个语句
            function inner() {
              var i2 = 1;
              var j2 = 1;
              return i2 + j2;
            }

            j = i + j;
            return j;
          }

#### * maxcomplexity

    作用：???
    
#### * maxlen

    作用：该选项用于设定每行的最大字符长度.


###relaxing options

#### * asi

    作用：值为false时，如果代码末尾省略了分号，则JSHint会给出警告；值为true时，则不会.

#### * boss

    作用：值为false时，如果预期为条件表达式的地方使用了赋值表达式，则JSHint会给出警告；值为true时，则不会.
    
    示例：/* jshint boss:false */
             
        // 例1: if条件判断中存在赋值操作
        var a;
        if (a = 1) { // jshint校验结果：Expected a conditional expression and instead saw an assignment.
            alert(1);
        }
        
        // 例2: for循环的条件判断中存在赋值操作
        for (var i = 0, j; j = i; i++) { // jshint校验结果：同上
            alert(j);
        }
        
#### * debug

    作用：值为false时，如果代码中有debugger语句，则JSHint会给出警告；值为true时，则不会.
    
    示例：/* jshint debug:false */

        function show() {
            alert(1);
            debugger; // jshint校验结果：Forgotten 'debugger' statement?
        }
    
#### * eqnull

    作用：值为false时，如果代码中使用"=="来比较变量与null，则JSHint会给出警告；值为true时，则不会.
    
    示例：/* jshint eqnull:false */
    
        var a;
        alert(a == null); // Expected '===' and instead saw '=='.

#### * esnext

    作用：值为true时，JSHint会使用ECMAScript 6的语法来校验你的代码.
    
#### * evil

    作用：值为false时，不允许在代码中使用eval.
    
#### * expr

    作用：值为false时，只允许在函数调用或赋值时使用表达式.
    
    示例：/* jshint expr:false */
    
        // JSHint校验结果：Expected an assignment or function call and instead saw an expression.
        2 > 1 ? (alert(1)) : (alert(2));
        
#### * funcscope

    作用：值为false时，如果在控制语句中定义了变量，却在控制语句之外使用变量，则JSHint会给出警告.
    
    备注：JS中只有两种作用域：全局作用域与函数作用域.
    
    示例：/* jshint funcscope:false */
    
    function test() {
        if (true) {
            var x = 0;
        }
        
        x = x + 1; // JSHint校验结果：'x' used out of scope.
    }

#### * globalstrict

    作用：值为false时，不允许使用全局级别的严格模式.
    
    备注：在全局中使用严格模式，会影响到第三方的JS，因此不建议这么做.
    
    示例：/* jshint globalstrict:false */
    
        "use strict"; // JSHint校验结果：Use the function form of "use strict".
        function show() {
            alert(1);
        }
        
#### * iterator

    作用：???
    
#### * lastsemic

    作用：值为true时，允许单行语句块中最后一条语句不写分号；值为false时，则会给出警告.
    
    示例：值为true和false时，校验结果对比（return语句未写分号）
    
        /* jshint lastsemic:true */
        var a = function() {alert(1);return 'hehe'}(); // JSHint校验结果：pass
    
        /* jshint lastsemic:false */
        var a = function() {alert(1);return 'hehe'}(); // JSHint校验结果：Missing semicolon.
        
#### * laxbreak

    作用：值为true时，允许代码中存在大多数不安全的换行（不包括逗号出现在行首的情况）；值为false时，会给出警告.
    
    示例：暂无（哪些换行是不安全滴???）.
    
#### * laxcomma

    作用：值为true时，允许逗号出现在行首的换行方式；值为false时，会给出警告.
    
    示例：值为true和false时，校验结果对比
    
        /* jshint laxcomma:true */
        var obj = {
            name: 'haha'
            ,age: 24 // JSHint校验结果：pass
        };
        
        /* jshint laxcomma:false */
        var obj = {
            name: 'haha'
            ,age: 24 // JSHint校验结果：Bad line breaking before ','.
        };
        
#### * loopfunc

    作用：值为true时，允许在循环中定义函数；值为false时，会给出警告.
    
    示例：值为false
    
        /* jshint loopfunc:false */
        var nums = [];
        for (var i = 0; i < 10; i++) {
            nums[i] = function (j) { // JSHint校验结果：Don't make functions within a loop.
                return i + j;
            };
        }
        nums[0](2);
    
#### * moz

    作用：该选项告诉JSHint，你的代码中使用了Mozilla JavaScript扩展.
    
#### * multistr

    作用：值为true时，允许多行字符串；值为false时，则会给出警告.

    备注：当值为true时，如果多行之间缺少转义字符，或者转义字符与新行之间有空白，JSHint依然会给出警告.
    
    示例1：值为true
    
        /* jshint multistr:true */
        var text = "hello\
        world"; // JSHint校验结果：pass
        
    示例2：值为true，但缺少转义字符
    
        /* jshint multistr:true */
        var text = "hello
        world"; // JSHint校验结果：Unclosed string.
        
    示例3：值为true，有转义字符，但转义字符与新行之间有空白
    
        /* jshint multistr:true */
        var text = "hello\ 
        world"; // JSHint校验结果：Bad or unnecessary escaping.
        
    示例4：值为false，有转义字符
    
        /* jshint multistr:false */
        var text = "hello\ 
        world"; // JSHint校验结果：Bad escaping of EOL. Use option multistr if needed.   
        
#### * proto

    作用：值为true时，允许在代码中使用__proto__属性；值为false时，则会给出警告.
    
#### * scripturl

    作用：值为true时，允许在代码中使用"javascript:..."这样的url；值为false时，则会给出警告.
    
    示例：值为false时
    
        /* jshint scripturl:false */
        var link = document.createElement('a');
        link.href = 'javascript:void()'; // JSHint校验结果：Script URL.
        
#### * smarttabs

    作用：???
    
#### * shadow

    作用：
    
#### * sub

    作用：值为true时，允许用obj['name']和obj.name两种方式访问对象的属性；值为false时，不允许使用obj['name']方式，
          除非只能使用这种方式访问.
    
    示例：值为false
    
        /* jshint sub:false */
        var obj = {name: 'he'};
        alert(obj['name']);  // JSHint校验结果：['name'] is better written in dot notation.
        
#### * supernew

    作用：是否允许使用像"new function() {...}"这样怪异的构造器，true -- 允许，false -- 不允许.
    
    示例：值为false
    
        /* jshint supernew:false */
        var obj = new function() { // JSHint校验结果：Weird construction. Is 'new' unnecessary?
            return {name: 'ha'};
        };
    
#### * validthis

    作用：是否允许在严格模式下的非构造函数中使用this，true -- 允许，false -- 不允许.
    
    备注：该选项只能用于函数作用域中.
    
    示例：值为false
    
        function show() {
            /* jshint validthis:false */
            'use strict';
            this.name = 'haha';
            alert(this.name); // JSHint校验结果：Possible strict violation.
        }

###legacy options
    
#### * nomen

    作用：是否允许变量名以"_"开头或结尾，false -- 允许，true -- 不允许.
    
    示例：值为true时
    
        /* jshint nomen:true */
        var _a = 1;
        alert(_a); // JSHint校验结果：Unexpected dangling '_' in '_a'.
        
        /* jshint nomen:true */
        var a_ = 1;
        alert(a_); // JSHint校验结果：Unexpected dangling '_' in 'a_'.
        
        /* jshint nomen:true */
        var a_b = 1; 
        alert(a_b); // JSHint校验结果：ok
        
#### * onevar

    作用：允许每个函数中只有一个var语句（如var a,b,c;）.
    
#### * passfail

    作用：让JSHint停在第一个错误/警告处，true -- 启用，false -- 不启用.
    
    示例：启用
    
        /* jshint passfail:true */
        function show() {
            var b = 1;
            alert(a); // JSHint校验结果：Stopping. (87% scanned).
        }

#### * white

    作用：让JSHint检查你的代码是否违反道格拉斯的JS编码风格.

###environments options

    说明：这些选项用于预定义来自流行JS库（如JQuery）和运行时环境（如Node）中的全局变量.
    
#### * browser

    作用：该选项定义了现代浏览器暴露出来的全局变量（不包括alert和console），true -- 启用，false -- 关闭.
    
    示例：未启用    
        /* jshint browser:false */
        var elem = document.getElementById('#aa'); // JSHint校验结果：'document' is not defined.
    
#### * couch

    作用：该选项定义了CouchDB暴露出来的全局变量，true -- 启用，false -- 关闭.
    
#### * devel

    作用：该选项定义了用于调试的全局变量（如alert，console），true -- 启用，false -- 关闭.
    
    示例：未启用   
        /* jshint devel:false */
        alert('log...'); // JSHint校验结果：'alert' is not defined.
        
#### * dojo

    作用：该选项定义了dojo暴露出来的全局变量，true -- 启用，false -- 关闭.
    
#### * jquery

    作用：该选项定义了jquery暴露出来的全局变量，true -- 启用，false -- 关闭.
    
    示例1：未启用    
        /* jshint jquery:false */
        var a = jQuery('#a'); // JSHint校验结果：'jQuery' is not defined.
        
    示例2：启用    
        /* jshint jquery:true */
        var a = jQuery('#a'); // JSHint校验结果：ok        
    
#### * mootools

    作用: 该选项定义了mootools暴露出来的全局变量，true -- 启用，false -- 关闭.
    
#### * node

    作用：该选项定义了Node环境中的全局变量.
    
#### * nonstandard

    作用：该选项定义了一些非标准但广泛使用的全局变量，像"escape"和"unescape".
    
#### * prototypejs

    作用：该选项定义了Prototype中暴露出来的全局变量.
    
#### * rhino

    作用：该选项定义了Rhino环境中的全局变量.
    
#### * worker

    作用：???
    
#### * wsh

    作用：???
    
#### * yui

    作用：该选项定义了YUI中暴露出来的全局变量.