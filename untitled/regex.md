# Regex

* Tools

  [Regexper](https://regexper.com/)

  [Online regex tester and debugger: PHP, PCRE, Python, Golang and JavaScript](https://regex101.com/)

  [RegexPlanet: online regular expression testing for JavaScript](http://www.regexplanet.com/advanced/javascript/index.html)

## Flags

`g` global 查找所有匹配项，在查找到第一个时不会停止，会继续查找

`i` ignoreCase 对大小写**不**敏感

`m` multiline 允许多行匹配

`y` 开启粘连

`u` 允许使用 Unicode 点转义符

## 操作符

`[abc]` 表示 a、b、c 中点任意字符

`[^abc]` 表示除了 a、b、c 以外的任意字符

`[a-m]` 表示匹配 a 和 m 之间的小写字母

`^` 表示匹配字符串的开头

`$` 表示匹配字符串的结束

`/^test$/` 表示匹配真个字符串

`?` 出现 0 次或 1 次

`+` 出现 1 次或多次

`*` 出现任意次

`{4}` 出现 4 次

`{4,10}` 出现 4 ~ 10 次

`a|b` 匹配 a 或 b

默认贪婪模式，可以匹配所有可能字符

在运算符后添加 ？变为非贪婪模式

`.` 匹配任意换行字符之外的任意字符

`\d` 匹配任意十进制数字 `[0-9]`

`\D` 匹配任何除了十进制数字之外的字符 `[^0-9]`

`\w` 匹配任何字母、数字和下划线 `[A-Za-z0-9]`

`\W` 匹配除了字母、数字和下划线 `[^A-Za-z0-9]`

`\s` 匹配任意空白字符

`\S` 匹配除空白字符外的

`\b` 匹配单词边界

`\B` 匹配非单词边界

![Regex/Untitled.png](../.gitbook/assets/untitled%20%282%29.png)

