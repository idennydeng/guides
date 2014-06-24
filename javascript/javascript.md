#JavaScrit代码规范

## 基本的格式化
1. **缩进**
    - 行缩进使用4个空格。
    - 不要使用tab键进行缩进。  

2. **行宽**  
    - 每行代码长度限制在80个字符。

3. **换行**  
	- 当一行代码长度超过单行最大字符限制时换行。
	    - 换行后增加两个缩进层级
	    - 并只在下面所列的标点符或运算符之后换行：','(逗号), '.'(圆点), ';'(分号), ':'(冒号), '{'(左大括号), '}', '('(左小括号), '[', '=', '<', '>', '?', '!', '+'(加号), '-'(减号), '*', '/', '%', '~', '^', '|', '&', '==', '!=', '<=', '>=', '+=', '-=', '\*=', '/=', '%=', '^=', '\=', '&=', '<<', '>>', '||', '&&', '===', '!==', '<<==', '>>==', '>>>', '>>>='
		
	```
	// bad 
	callAFun(document, element, windwos, 'some string value', true, 123,
		navigator);
		
	// bad 
	callAFun(document, element, windwos, 'some string value', true, 123
			, navigator);
		
	// good 
	callAFun(document, element, windwos, 'some string value', true, 123,
			navigator);
			
	// good 		
	if (isLeapYear && isFebruary && day == 29 && itsYourBirthday && 
			noPlans) {
			
		waitAnotherFourYears();
	}
	```
	
	- 变量赋值时，换行后应和当前赋值运算符保持对齐；  
	
	```	
	// good
	var results = something + anotherThing + yetAnotherThing + somethingEles +
				  adotherSomerthingEles;
	```

4. **空行**  
	- 在方法之间;
	- 在方法内的逻辑片段之间；  
	- 在方法中的局部变量和第一条语句之间；  
	- 在多行或单行注释之前；
	
5. **空格**
    - 调用函数的时候，函数名与左括号之间没有空格。

    ```
    // bad
    fun1 (params1, params2);
    
    // good
    fun1(params, params2);    
    ```

    - 所有其他语法元素在左括号之前、右括号之后都有各添加一个空格。
    
    ```
    // bad
	if (condition){
	    doSomething();
	}	

    // bad
    if(condition) {
	    doSomething();
	}
	
    // good
	if (condition) {
	    doSomething();
	}
    ```

    - 除了'.'（圆点）之外，所有二元操作符，都应该使用一个空格将其和操作数隔开。
        
    ```
    // bad
	1+1；
	1*1;
	1<2;
    2===2;
	var a=1;
	

    // good
	1 + 1;
	1 * 1;
	1 < 2;
	2 === 2;
	var a = 1;
    ```

    - 每个','（逗号）之后应增加一个空格。
    
    ```
    // bad
    var obj = {name: 'denny',count: 1};
    var a = 1,b = 1;
    console.log(obj,a,b);
    
    // good
    var obj = {name: 'denny', count: 1};
    var a = 1, b = 1;
    console.log(obj, a, b);
    ```

    - for语句控制部分的每一个';'(分号)之后应增加一个空格。
    
    ```
    // bad
    for (var i = 1, len = 10;i < len; i += 1; ) {
        doSomething();
    }
    
    // good
    for (var i = 1, len = 10; i < len; i += 1) {
        doSomething();
    }
    ```

5. **语句结尾**
    - 不要省略句末的分号

    ```
    // bad
	var i = 10
	
	// good
	var i = 10;
	```

6. **命名**  
	- 变量和函数命名，遵循小驼峰式大小写(Camel Case)命名法。
	    - 由小写字母开头，后续每个单词首字母大写；
	    - 变量名前缀应当是名词，函数名前缀应当是动词； 
	    - 对象的私有属性和私有方法名，应以下划线开头； 

	```
    // bad
	var getCount = 10;

	// bad
	function theName() {
		return name;
	}
	
	// good
	var count = 10
	
	// good
	function getName() {
		return name;
	}
	```
  
    - 构造函数命名，遵循大驼峰式大小写(Pascal Case)命名法。
        - 由大写字母开头，后续每个单词首字母大写；  
    
    ```	
	// bad
	function user() {
		this.name = 'admin';
	}
  
	var admin = new user();
	
	
	// good
	function User() {
		this.name = 'admin';
	}
	
	var admin = new User();
	```

    - 常量命命名，每个字母都必须大写，每个单词用下划线分隔；
        
    ```		
	// good
    var PI = 3.1415926;
    var MAX_VALUE = 100;
    var URL = "http://www.knet.cn";
	```	  

7. **字面量**
	- 字符串
	    - 字符串都必须单引号括起来  
	    - 不允许使用多行字符串
	
	```
	// bad
	var text = 'hello \
	world';

	// good
	var text = 'hello world'
	```
	    
	- 在代码中禁止使用八进制字面量；  
	- 当一个变量将用于保存一个对象时，可以使用null初始化（对象占位符）；

## 注释
1. **单行注释**
    - '//'(双斜杠)之后必须增加一个空格。
    
    ```
    // bad
    var count = 10; //count value
    
    // good
    var count = 10; // count value
    ```
    
    - 独占一行的注释，用来解释下一行代码。
        - 注释之前总是有一个空行
        - 且缩进层级和下一行代码保持一致；
    
    ```
    // bad
    if (condition) {
        // security check
        allowed();
    }
    
    // bad
    if (condition) {
    
    // security check
        allowed();
    }
    
    // good
    if (condition) {
    
        // security check
        allowed();
    }
    ```

    - 在代码行尾部的注释。
        - 代码结束到注释之间至少一个空格或缩进
        - 本行不应超过单行最大字符限制，如果超过了，就将其置放在当前代码行上方
    
    ```
    // bad
    var result = something + somethingElse;// somethingElse not be Null

    // good
    var result = something + somethingElse;  // somethingElse not be Null
    ```

    - 被注释掉的大段代码。

2. **多行注释**
	- 多行注释至少包含三行.
		- 第一行是/\*\*，
		- 第二行是\*开始且和上一行的*保持左对齐
		- 最后一行是\*/;
	
	```
	/**
	 * good
	 *
	 * Multi-line comments
	 */
	```

	- 代码行尾部不要是用多行注释;
	
	```
	// bad
    var result = something + somethingElse; /* somethingElse not be Null */
    
    // good
    var result = something + somethingElse; // somethingElse not be Null
    
    // somethingElse not be Null
    var result = something + somethingElse; 
	```

3. **使用注释**
    - 代码很明了时不应当增加注释；
	- 难于理解的代码应当增加注释；
	- 可能被误解的代码应当增加注释；
	- 浏览器特性hack代码应当增加注释；
	- 修改代码逻辑，应该同步修改注释；
	
## 语句和表达式

1. **大括号**

    - 所有的块语句都应该使用大括号，包括：
	    - if
	    - for
	    - while
	    - do...while
	    - try...catch...finally  
	
	```
	// bad
	if (condition)
	    doSomething();
	
	// bad
	if (condition) doSomething();
	
	// bad
	if (condition) { doSomething(); }
	
	// good
	if (condition) {
	    doSomething();
	}	
    ```

    - 表示区块起首的大括号，不要另起一行。
    
    ```
    // bad
    if (condition) 
    { 
    	doSomething();
    } 
    else 
    {
    	doSomethingElse();
    }
    
    // good
	if (condition) { 
    	doSomething();
    } else {
    	doSomethingElse();
    }
    ```

    - 不允许出现空的语句块。
    
    ```
    // bad
    if (condition) { 
    } 
    ```
    
2. **不要使用with语句。**

3. **for语句**  
    - 使用for in语句遍历对象时，应防止遍历从原型链中继承的属性。for in语句的主体都应该包裹在一个用于过滤的if语句中。
    
    ```
    // good
    for (name in object) {
        if (object.hasOwnProperty(name)) {
            doSomething();
        }
    }
    ```
    
4. **不要将不同目的的语句，合并成一行。**

    ```
    // bad
    var a = b = 0;
    
    // good
    var a = 0, b = 0;
        
    // bad
    if (a = b) {
        doSomething();
    }
    
    // good
    a = b;
    
    if (a) {
        doSomething();
    }
    ```

## 变量、函数和运算符

1. **变量声明**
    - 所有变量声明都放在函数体的头部。

    ```
    // bad
    function doSomethingWithItmes(items) {
    
        for (var i = 0, len = items.length; i < len; i++) {
            doSomething(items[i]);
        }
    }

    // good
    function doSomethingWithItmes(items) {
        
        var i, len;

        for (i = 0, len = items.length; i < len; i++) {
            doSomething(items[i]);
        }
    }
    ```
    - 函数参数不需要用var再次进行声明。
    
    ```
    // bad
    function doSomethingWithItmes(items) {
        var items = items;
	    doSomething(items[i]);
    }

    // good
    function doSomethingWithItmes(items) {
	    doSomething(items[i]);
    }
    ```
    
    - 避免使用全局变量；如果不得不使用，用大写字母表示变量名，比如UPPER_CASE。

2. **函数声明**
    - 所有函数都必须用字面量方式声明。
    
    ```
    // bad
    function doSomething() {
		alert("Hello world!");
    }

    // good
    var doSomething = function() {
		alert("Hello world!");
    }
    ```  

3. **禁止使用位操作符**

4. **禁止使用一元递增（"++"）和递减（"--"）运算符**

5. **相等**
    - 不要使用"相等"（==）运算符，只使用"严格相等"（===）运算符。
    
    ```
    // bad
    0 == '';           // true
    0 == '0';          // true
    1 == true;         // true
    false == '0';      // true
    false == 'false';  // false
  
    // good
    0 === '';          // false
    1 === true;        // false
    0 === '0';         // false
    false === '0';     // false
    false === 'false'; // false
    ```
   
6. **eval()**
    - 严禁使用eval()和Function。
    
    ```
    // bad
    eval('alert("hello")');
    var fun = new Function('alert("hello")');    
    ```
    
    - 禁止给setTimeout()和setInterval()传入字符串参数。
    
    ```
    // bad
    setTimeout('alert("hello")', 50);
    setInterval('alert("hello")', 1000);
    
    // good
    setTimeout(function() {
        alert("hello");
    }, 50);
    
    setInterval(function() {
        alert("hello");
    }, 100);    
    ```
    
7. **原始包装类型**
    - 禁止使用原始包装类型。
    
    ```
    // bad
    var isSuccess = new Boolean(true);
    var name = new String('denny');
    var count = new Number(10);
    
    // good
    var isSuccess = true;
    var name = 'denny';
    var count = 10;
    ```
