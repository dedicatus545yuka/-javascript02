# -javascript02
关于javascript里的-类型转换啊，运算符啊，NaN。。。。还有别问我为啥先传的2我也不知道
### 隐式类型转换  
定义三个变量
```js
var str = 'this is text';
var num = 100;
var boo = false;
```
1. 在变量之前添加一个“+”，`string`类型转换成`number`类型
```js
console.log(+str);// 输出的值为NaN - 文本内容(包含字符)转换成number类型为NaN
console.log(+'100');// 100
var result = +'100';
console.log(typeof result);// 输出的结果为Number,也就是测试出来的类型的确变了
```
2.`boolean`类型转换`number`类型
```js
console.log(+boo);//true 转换成 1 ，false 转换成 0   
```
3. `string`类型转换成`boolean`类型  
##### 注意 在变量之前添加两个“!”
```js
console.log(!!str);// ture
```
4. `number`类型转换成`boolean`类型
```js
console.log(!!num);// ture
```
5. `number`类型转换成`string`类型  
```js
console.log(''+num);// 100
var result = '' + num;
console.log(typeof result);// string 测试出来的类型的确是string
```
6. `boolean`类型转换成`string`类型
```js
console.log('' + boo);// false
var result = boo + '';
console.log(typeof result);// string
```
### 显示类型的转换  
1. 转换为`string`类型  
- `String`(其他数据类型的变量) - 注意：一定要与构造函数`new String()`区分
```js
var str1 = String(100);
console.log(typeof str1);// string
```
- `toString()`
```js
var boo = true;
var str2 = boo.toString();
console.log(typeof str2);// string
```
2. 转换为`number`类型
- `Number`(其他数据类型的变量)
```js
var num1 = Number('text');
console.log(typeof num1);// number
```
- `parseInt()`转换成整数；`parseFloat()`转换成浮点数
```js
var str1 = '100';
var str2 = '10.01';
// 只取整数部分
console.log(parseInt(str1));// 100
console.log(parseInt(str2));// 10
// 有小数取小数没有还是整数
console.log(parseFloat(str1)); 100
console.log(parseFloat(str2)); 10.01
```
3. 转换成`boolean`类型
- `boolean`(其他数据类型)**函数**
```js
var bool = Boolean('this is text');
console.log(typeof bool);// boolean
```
>隐式类型转换的效率高于显示类型转换  
### typeof运算符
- 由于 JavaScript 是弱类型/松散类型的，因此需要有一种手段来检测给定变量的数据类型。typeof 运算符就是负责提供这方面信息，如下述代码:  
```js
var message = "this is message";
console.log(typeof message);// 输出 string
console.log(typeof(message));// 输出 string
```
- typeof 运算符加上圆括号，会像是函数，而不是运算符，并不建议这种写法。    
![](http://a3.qpic.cn/psb?/V118JuTr0BKcy7/yvGK68BGwbJIbQQZgWBM**.*.UhdX5StOTfrjRzYGuc!/m/dD4BAAAAAAAA&bo=aAFuAQAAAAADByQ!&rf=photolist)
### 算数运算符  
```js
var num1 = 30;
var num2 = 20;
console.log(num1 + num2);// 50
console.log(num1 - num2);// 10
console.log(num1 * num2);// 600 - * 乘法
console.log(num1 / num2);// 1.5 - / 除法
console.log(num1 % num2);// 10 - % 求余（得到余数）
```
>注意：  
在所有运算中都是把其他类型的量转换成`number`类型再进行计算  
**若是得不到一个正常的数值，那就会得到NaN**
```js
var result = 'text'/100;// 100/'text'
console.log(result);// NaN
```
>当遇到`string`类型时，**+**不作为算数运算符处理而是作为**字符串连接运算符** 
```js 
console.log(100+'200');// 10020 - 将`number`类型转换成`string`类型
var result = '200' + 100;
console.log(typeof result);
```
### 自增和自减运算符
- 自增运算符  
```js
// 前置自增运算符  
var num = 100;
var result1 = ++num;
console.log(result1);//101
console.log(num);// 101  
// 后置自增运算符  
var result2 = num++;
console.log(result2);// 101
console.log(num);// 102
```
>在前置自增运算符中`num`先进行了++,也就是自增，然后再赋值给了result1,所以结果为101  
在后置自增运算符中，`num`先赋值给了result2，就是101,然后又自增，所以后面`num`变为102  

![自增运算符的解析图](http://a3.qpic.cn/psb?/V118JuTr0BKcy7/xcy14WkiQKNsSV65hmfco.TU9GqdYNQ3Ad2ICCpg6cE!/m/dGoBAAAAAAAA&bo=GwWAAgAAAAADB74!&rf=photolist)  
> 那么自减运算符的用法与上同理，只是计算的不同罢了

### 比较运算符
```js
//当为数值`number`时
var num1 = 100;
var num2 = 200;
console.log(num1 == num2);// false  等于
console.log(num1 != num2);// true   不等于
console.log(num1 > num2);// false   大于
console.log(num1 >=num2);// false   大于等于
console.log(num1 < num2);// true    小于
console.log(num1 <= num2);// true   小于等于
//当为`boolean`类型时
var boo1 = true
var boo2 = false  
console.log(boo1 == boo2);// false
console.log(boo1 > boo2); // true - 在比较时转换为数值来，1>0
//当为`string`类型时
var str1 = 'text';
var str2 = 'string';
// 这里比较的是首字母的排列先后顺序
console.log(str1 == str2);// false
console.1og(str1 > str2);// true

// 全等于`===`和`!==`不全等
 // === - 既要比较值，也要比较类型
// 必须要在值相等，并且类型相同 -> true
console.log(100 === '100');// false
// !== - 值或类型不相等
console.log(1 !== '1');// true
console.log(1 !== 1);// false
```
>注意的是`==`和`!=`这两个只比较值，与量的类型无关 
### 逻辑运算符
#### 逻辑与运算符  
```js
//boolean类型
console.log(true && true);// true
console.log(true && false);// false
console.log(false && true);// false
console.log(false && false);// false
//number类型
console.log(1 && 1);// 1
console.log(1 && 0);// 0
console.log(0 && 1);// 0
console.log(0 && 0);// 0
//string类型
console.log('string' && 'text');// text
console.log('string' && '');// ''
console.log('' && 'text');// ''
console.log('' && '');// ''
```
#### 逻辑或运算符
```js
//boolean
console.log(true || true);// true
console.log(true || false);// true
console.log(false || true);// true
console.log(false || false);// false
//number
console.log(1 || 1);// 1
console.log(1 || 0);// 1
console.log(0 || 1);// 1
console.log(0 || 0);// 0
//string
console.log('string' || 'text');// string
console.log('string' || '');// string
console.log('' || 'text');// text
console.log('' || '');// ''
```
>在逻辑短路原则中  
1. 先将比较的操作数，转换成Boolean类型  
2. 确定运算符前面的运算数为 true 或 false，就可以确定返回结果为 true 或 false  
- 逻辑与运算符
    - 逻辑与运算符前面为false，结果都将返回逻辑与运算符前面的。
    - 逻辑与运算符前面为true，结果都将返回逻辑与运算符后面的值。
- 逻辑或运算符
    - 逻辑或运算符前面为false，结果都将返回逻辑或运算符后面的值。
    - 逻辑或运算符前面为true，结果都将返回逻辑或运算符前面的值。
#### 逻辑非运算符  
```js
//boolean
console.log( !true );// 输出 false
//number
console.log( !1 );// 输出 false
//string
console.log( !'string' );// 输出 false
//其实总体来说就是反向输出，对的就是错的，错的就是对的-_-!!
```
>注意：能被转换为 false 的值有null, 0, NaN, 空字符串("") 和 undefined。  
### 赋值运算符
```js
//赋值运算符不是等于号
var result1 = 100 + 200;
console.log(result1);// 300
var result2 = 100;
//赋值运算符有个简写的方式
result2 += 200;// 就相当于 result2 = result2 + 200;
console.log(result2);// 300
```
### 条件运算符  
>条件运算符又被称为三元运算符，这里涉及到关于运算符的分类(其实就是中文翻译的问题)     
>1. 操作变量的数量来区分
>* 一元（一目）运算符 如 ++,--,!
>* 二元（二目）运算符 如 + - * / % ...等等
>* 三元（三目）运算符
>2. 按照功能进行区分
>* 算数运算符
>* 比较运算符
>* 赋值运算符
>* 逻辑运算符
>* 条件运算符
```js
var result = true && true ? '这是真的' : '这是假的';
console.log(result)// '这是真的'（这里与文本内容无关）
```
![条件运算符的示意图](http://a3.qpic.cn/psb?/V118JuTr0BKcy7/2oGKuMIE9SLuJwe0.sC1q8N5hU5mwJqprGewKLh2K0E!/m/dI4BAAAAAAAA&bo=GwWAAgAAAAADB74!&rf=photolist)
#### 条件运算符的嵌套
```js
var score = 55;
var result = score > 90 ? '优秀' : (score > 80 ? '良好' : (score > 60 ? '及格' : '不及格'));
console.log(result);
```
>条件运算符的嵌套情况
>1. 嵌套的层级在语法结构没有任何要求，实际上建议最多不要超过 3 层
>2. 嵌套结构本身的代码可读性不高，太长不想看的感觉
>3. 嵌套结构本身的性能不够好，因为要一个一个的比较取值  
### NaN
1. NaN与任何值都不相等，甚至与自身也不相等
```js
console.log(NaN == NaN);//false
console.log(NaN == true);// false
```
2. 在Javascript里提供`isNaN()`方法来判断当前值是否是NaN(表示不是一个数字)
```js
console.log(isNaN(NaN));// true
//若是返回false的话那就说明当前值是个数字
console.log(isNaN(100));// false
```
### 有关于代码优化的问题  
>1. 功能实现 - 前提
>2. 代码优化 - 在原有代码实现的功能不变的情况下
>* 代码量越少越好
>* 性能越快越好
>* 代码之间的耦合度越低越好
>* 误区：一次性将代码编写到最好 - 没有最好，只有更好
>    * 个人的技术能力在不断地提高
>    * 软件技术也在不断地更新
### 运算符的优先级别问题
#### 话不多说，一张表说明一切，若是想优先使用某个运算符的话就加括号啊+_+
![运算符优先级别表](http://a3.qpic.cn/psb?/V118JuTr0BKcy7/m5w1JRGpEAl2smhTj1EFTflcnFUT3hhALXoj3dkXEwM!/m/dPIAAAAAAAAA&bo=gAJ6BQAAAAADB98!&rf=photolist)


  




   





 



