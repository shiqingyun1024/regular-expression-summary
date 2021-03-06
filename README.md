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

var rg2 = /^[a-z]$/;  // 26个英文小写字母任何一个字母都会返回true
rg2.test('a');   // true
rg2.test('z');   // true
rg1.test('A');   // false
rg1.test(1);     // false

3. 字符组合
var rg3 = /^[a-zA-Z]$/;  // 26个英文大小写字母任何一个字母都会返回true
var rg4 = /^[a-zA-Z0-9_-]$/;  // 26个英文大小写字母和数字_,-任何一个都会返回true

4. ^放在[]中表示取反的意思，千万别和 边界符^(也就是放在[]外面的)相混淆。
var rg5 = /^[^a-zA-Z0-9_-]$/;  // 26个英文大小写字母和数字_,-任何一个都会返回false

```
### 3.4 量词符
```
量词符用来设定某个模式出现的次数。

量词      说明
*        重复零次或更多次
+        重复一次或更多次
?        重复零次或一次
{n}      重复n次
{n,}     重复n次或更多次
{n,m}    重复n到m次

举例：
简单理解：就是让下面的a这个字符重复多少次
var reg = /^a$/;

1. * 相当于 >= 0 可以出现0次或者很多次
var reg1 = /^a*$/;
reg1.test('');      // true
reg1.test('a');     // true
reg1.test('aaaa');  // true

2. + 相当于 >= 1 可以出现1次或者很多次
var reg2 = /^a+$/;
reg2.test('');      // false
reg2.test('a');     // true
reg2.test('aaaa');  // true

3. ? 相当于 1 || 0
var reg3 = /^a+$/;
reg3.test('');      // true
reg3.test('a');     // true
reg3.test('aaaa');  // false

4. {3}就是重复3次  {}更精确指定重复多少次
var reg4 = /^a{3}$/;
reg4.test('');      // false
reg4.test('a');     // false
reg4.test('aaa');  // true
reg4.test('aaaa');  // false

5. {3,} 大于等于3
var reg5 = /^a{3,}$/;
reg5.test('');      // false
reg5.test('a');     // false
reg5.test('aaa');   // true
reg5.test('aaaa');  // true

6. {3,6} 大于等于3 并且 小于等于6 中间不要有空格，{3, 6}这样不对
var reg6 = /^a{3,6}$/;  
reg6.test('');      // false
reg6.test('a');     // false
reg6.test('aaa');   // true
reg6.test('aaaa');  // true
reg6.test('aaaaaaa');  // false

综合举例：
用户名验证
var reg7 = /^[a-zA-Z0-9_-]{6,16}$/;
reg7.test('aa');        // false
reg7.test('aady-red');  // true
reg7.test('aady007');   // true
```
### 3.5 括号总结
```
1. 中括号  字符集合 匹配方括号中的任意字符
var reg = /^[abc]$/;  // 多选一，a也可以，b也可以，c也可以 a || b || c

2. 大括号  量词符   里面表示重复次数
var reg1 = /^abc{3}$/;  // 它只是让c重复三次  abccc
reg1.test('abc');  // false
reg1.test('abcabcabc');  // false
reg1.test('abccc');  // true

3. 小括号  表示优先级
var reg2 = /^(abc){3}$/;  // 它是让abc重复三次  abcabcabc
reg2.test('abc');  // false
reg2.test('abcabcabc');  // true
reg2.test('abccc');  // false

```
### 3.6 预定义类
```
预定义类指的是某些常见模式的简写方式

预定义类     说明
\d          匹配0-9之间的任一数字，相当于[0-9]
\D          匹配所有0-9以外的字符，相当于[^0-9]
\w          匹配任意的字母、数字和下划线，相当于[A-Za-z0-9_]
\W          除所有字母、数字和下划线以外的字符，相当于[^A-Za-z0-9_]
\s          匹配空格（包括换行符、制表符、空格符等），相当于[\t\r\n\v\f]
\S          匹配非空格的字符，相当于[^\t\r\n\v\f]

举例：座机号码验证：全国座机号码 有两种格式：010-12345678 或者 0530-1234567
<!-- 正则里面的或者符号是 | -->
var reg = /\d{3}-\d{8}|\d{4}-\d{7}/g 
或者
var reg = /^\d{3,4}-\d{7,8}$/ 
```
## 4.正则表达式中的替换
### 4.1 replace替换
```
replace()方法可以实现替换字符串操作，用来替换的参数可以是一个字符串或是一个正则表达式。

stringObject.replace(regexp/substr,replacement)

替换字符串
let str = 'andy和red';
str.replace('andy','bady');
换成正则表达式
str.replace(/andy/,'bady');
1. 第一个参数：被替换的字符串或者正则表达式
2. 第二个参数：替换为的字符串
3. 返回值是一个替换完毕的新字符串
```
### 4.2 正则表达式参数
```
/表达式/[switch]
switch(也称为修饰符)按照什么样的模式来匹配，有三种值：
g: 全局匹配
i: 忽略大小写
gi: 全局匹配 + 忽略大小写
```