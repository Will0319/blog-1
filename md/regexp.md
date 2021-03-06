# 正则匹配

### 创建正则表达式
```js
let regex = new RegExp("a")

let regex = new RegExp("^[a-zA-Z]", "g")

let regex = new RegExp(/^[a-zA-Z]/, 'gi')
```


### 正则表达式参数

* g 全局匹配（找到所有的，而不是找到第一个后就停了）
* i 匹配全部大小写
* m 多行  开始和结束（^和$）分别匹配每一行
* s 和 m 相反，单行匹配


### 正则中常用方法，字符串中与正则相关的方法

1. test() 方法检索字符串中的值是否与正则匹配，返回boolean  

```js
// 检索"ab"是否在 "abcd" 里面

/^[a-z]/.test("ab")
```

2. exec() 方法检索指定值，如果匹配返回结果数组，反之返回 null

```js
// 检索 /abc/是否在 "defaabc" 有匹配到

/abc/.exec("defaabc") // arr 

// 检索 /qqq/是否在 "defaabc" 有匹配到

/qqq/.exec("defaabc") // null
```

3. compile() 方法用于改变正则匹配内容

```js
// /abc/改成/def/

/abc/.compile('def')
```


4. split() 将字符串分割成数组

```js
// 将 "abcd" 以/b/分割

"abcd".split(/b/)
```

5. replace() 在字符串中替换

```js
// 用 /\d\d\d/去匹配字符串 "12345abcde" 将匹配内容换成 * ,并返回

"12345abcde".replace(/\d\d\d/g, '*')

// 去掉字符串的引号，换成空

"12345abcde".replace(/"/g, '')

// 去掉所有空格，tab。换行，换页

" 12 345ab cd   e  ".replace(/\s/g, '')
```

6. search() 匹配指定字符串，返回匹配字符串的起始位置的索引，反之返回-1

```js
"abcdefg".search(/d/g)

"abcdefg".search(/x/g)
```


7. match() 在字符串中检索指定的值，找到一个或者多个

```js
// 返回指定索引的值

"aabbbbbccbbaab".match(/b+/g)
```


### 常用正则规则

1. 字符类规则

<img src="../img/1.png" />

2. 范围符号匹配规则

<img src="../img/2.png" />

3. 分组匹配规则

<img src="../img/3.png" />

4. 重复匹配规则

<img src="../img/4.png" />

### 常用正则匹配  

<strong>(1) 手机号</strong>

* 移动号段: 134 135 136 137 138 139 147 148 150 151 152 157 158 159 172 178 182 183 184 187 188 198
* 联通号段: 130 131 132 145 146 155 156 166 171 175 176 185 186
* 电信号段: 133 149 153 173 174 177 180 181 189 199
* 虚拟运营商: 170

<strong>匹配 13* 的手机号</strong>
```js
/^(1)3(\d){9}$/.test(13131121111)
```

<strong>匹配 15* 的手机号</strong>

```js
/^(1)5[^4]{9}$/.test(15531121989)
```

<strong>匹配 16* 的手机号</strong>

```js
/^(1)66(\d){8}$/.test(16631121989)
```

<strong>匹配 17* 的手机号</strong>

```js
/^(1)7[0-8]{1}(\d){8}$/.test(17199121989)
```

<strong>匹配 18* 的手机号</strong>

```js
/^(1)8(\d){9}$/.test(18131121989)
```

<strong>匹配 19* 的手机号</strong>

```js
/^(1)9[8-9](\d){8}$/.test(19831121989)
```

<strong>匹配所有的手机号</strong>

```js
/^(1)(3(\d){9}$)|(4[5-9]{1}(\d){8}$)|(5[^4]{9})|(66(\d){8})|(7[0-8]{1}(\d){8})|(8(\d){9}$)|(9[8-9](\d){8}$)/.test(19931121989)
```

<strong>(2) 邮箱</strong>

* 126规则：6~18个字符，可使用字母、数字、下划线，需以字母开头
* 163规则：6~18个字符，可使用字母、数字、下划线，需以字母开头 允许手机号
* qq邮箱：数字5-10个数字
* 新浪邮箱规则：4-16个字符，可使用英文小写，数字，下划线，下划线不可在首位
* 搜狐邮箱规则：4-16位，英文、数字、下划线，小写字母开头

<strong>匹配126邮箱</strong>

```js
/((^([a-zA-Z])){1}(\w){5,17})@126.com$/.test("AA3333333333333333@126.com")
```

<strong>匹配163邮箱</strong>

```js
/((^([a-zA-Z])){1}(\w){5,17}$)|(^(1)(3(\d){9}$)|(4[5-9]{1}(\d){8}$)|(5[^4]{9})|(66(\d){8})|(7[0-8]{1}(\d){8})|(8(\d){9}$)|(9[8-9](\d){8}$))@163.com$/.test("15132221989@163.com")
```

<strong>匹配qq邮箱</strong>

```js
/(^[1-9]){5,10}@qq.com$/.test("115511@qq.com")
```

<strong>匹配新浪邮箱</strong>

```js
/(^([a-z])|^(\d)){1}(\w){3,15}@sina.(cn)|(com)$/.test("223dddddddfasddw@sina.com")
```

<strong>匹配搜狐邮箱</strong>

```js
/(^[a-z]){1}(\w){3,15}@sohu.com$/.test("dddddddfw@sohu.com")
```

<strong>中文</strong>

```js
/^[\u4e00-\u9fa5]$/g.test("我")   
```
