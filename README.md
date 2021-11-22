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
