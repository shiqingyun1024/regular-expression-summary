# regular-expression-summary
正则表达式相关的总结

## 1.正则表达式概述
### 1.1 什么是正则表达式
```
正则表达式（Regular Expression）是用于匹配字符串中字符组合的模式。在JavaScript中，正则表达式也是对象。
正则表达式通常被用来检索、替换那些符合某个模式（规则）的文本，例如验证表单：用户名表单只能输入英文字母
、数字或者下划线，昵称输入框中可以输入中文（匹配）。此外，正则表达式还常用于过滤掉页面内容中的一些敏感
词（替换），或从字符串中获取我们想要的特定部分（提取）等。
所以正则表达式的作用可以用三个关键词来表示：匹配、替换、提取。
```
### 1.2 正则表达式的特点
```
1.灵活性、逻辑性和功能性非常的强。
2.可以迅速地用极简单的方式达到字符串的复杂控制。
3.对于刚接触的人来说，比较晦涩难懂。比如：^\W+([-+.]\W+)
```
## 2.正则表达式在JavaScript中的使用
### 2.1 创建正则表达式
```
在JavaScript中，可以通过两种方式创建一个正则表达式。
1. 通过调用RegExp对象的构造函数创建
var 变量名 = new RegExp(/表达式/)
2. 利用字面量创建 正则表达式
var rg = /123/;
```
### 2.2 测试正则表达式test
```
test()正则对象方法，用于检测字符串是否符合该规则，该对象会返回true或false，其参数是测试字符串。
regexObj.test(str)
1. regexObj是写的正则表达式
2. str 我们要测试的文本
3. 就是检测str文本是否符合我们写的正则表达式规范
```
## 3.正则表达式中的特殊字符
### 3.1 正则表达式的组成
```
一个正则表达式可以由简单的字符构成，比如/abc/，也可以是简单和特殊字符的组合，比如/ab*c/。其中特殊字
符也被称为元字符，在正则表达式中是具有特殊意义的专用符号，如^、$、+等
```
### 3.2 边界符
```
正则表达式中的边界符（位置符）用来提示字符所处的位置，主要有两个字符。
^  表示匹配行首的文本（以谁开始）
$  表示匹配行尾的文本（以谁结束）
如果^和$在一起，表示必须是精准匹配

var rg = /abc/;  // 只要包含abc这个字符串返回的都是true
rg.test('abc');  // true
rg.test('abcd');  // true
rg.test('aabcd');  // true

var reg = /^abc/;  // 以abc开头
reg.test('abc')  // true
reg.test('abcd')  // true
reg.test('aabcd')  // false

var reg1 = /^abc$/;  // 以abc开头，并且以abc结尾，说白了就是只包含abc这个字符串===精准匹配
reg.test('abc')  // true
reg.test('abcd')  // false
reg.test('aabcd')  // false
reg.test('abcabc')  // false
```
### 3.3 字符类
```
1. []  表示有一系列字符可供选择，只要匹配其中一个就可以了。所有可供选择的字符都放在方括号内。

// var rg = /abc/;  // 只要包含abc就可以

var rg = /[abc]/; // 只要包含有a 或者 包含有b 或者包含有c 都返回为true
rg.test('andy');   // true
rg.test('baby');   // true
rg.test('color');   // true
rg.test('red');   // false

var rg1 = /^[abc]$/; // 三选一 只有是a 或者是b 或者是c 这三个字母才返回true
rg1.test('aa');   // false
rg1.test('a');   // true
rg1.test('b');   // true
rg1.test('c');   // true
rg1.test('abc');   // false

2. [-]  方括号内部范围符 - 
```
