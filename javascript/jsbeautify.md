#JS Beautifier

##Introduction
js-beautify 是一个代码格式化工具。

项目主页: [http://jsbeautifier.org/](http://jsbeautifier.org/)  

GitHub: [https://github.com/beautify-web/js-beautify](https://github.com/beautify-web/js-beautify)

##Usage

1. 安装jshint

    ```
    $ npm install js-beautify -g
    ```

2. 检查代码

    ```
    $ js-beautify source.js
    ```

##Options

#### * indent_char
    
    作用：设置缩进字符, 如: "indent_char": " ".

#### * indent_size
    
    作用：设置缩进字符个数, 如: "indent_size": 4.
    
#### * indent_level
    
    作用：设置缩进级别, 如: "indent_level": 0.
    
    备注：通过测试没有发现具体用处.
    
#### * indent_with_tabs
    
    作用：值为true时, 缩进使用tab(制表符);
    
#### * preserve_newlines
    
    作用：值为true时, 保留空行.
    
#### * max_preserve_newlines
    
    作用：设置缩最大保留空行个数, 如: "max_preserve_newlines": 2.
    
#### * jslint_happy
    
    作用：值为true时, 启用JSLint风格
    
#### * brace_style
    
    作用：大括号格式化风格(代码块), 支持三种值: [collapse|expand|end-expand].
    
#### * keep_array_indentation
    
    作用：值为true时, 保持数组原有缩进.
    
#### * keep_function_indentation
    
    作用：值为true, 保持函数原有缩进.
    
    备注：经过测试和查看源码的单元测试，发现设置成true或false结果一直.
    
#### * space_before_conditional
    
    作用：值为true时, 在条件语句前增加空格.
    
    事例：space_before_conditional: true
    
         if(true);
         
         if (true); // formatted

    备注：经过测试，发现设置成true或false结果一直
    
#### * unescape_strings
    
    作用：值为true时, 将代码中的 xNN 符号转为可打印字符
    
    事例：unescape_strings: true
    
         var str = '\x65\x78\x61\x6d\x70\x6c\x65';
         
         var str = 'example'; // formatted
    
#### * wrap_line_length
    
    作用：设置行字符个数限制,超出换行, 如: "wrap_line_length": 80.
      
#### * eval_code
    
    作用：？
    


    







    






