## 使用严格相等
> 总是使用 === 精确的比较操作符，避免在判断的过程中，由 JavaScript 的强制类型转换所造成的困扰
> ==， 两边值类型不同的时候，要先进行类型转换，再比较。
> ===，不做类型转换，类型不同的一定不等。

### ==操作符
- 如果两个值具有相同类型，会进行===比较，返回===的比较值
- 如果两个值不具有相同类型，也有可能返回true 
- 如果一个值是null另一个值是undefined，返回true 
- 如果一个值是string另个是number，会把string转换成number再进行比较 
- 如果一个值是true，会把它转成1再比较，false会转成0

```
console.log( false == null )      // false
console.log( false == undefined ) // false
console.log( false == 0 )         // true
console.log( false == '' )        // true
console.log( false == NaN )       // false

console.log( null == undefined ) // true
console.log( null == 0 )         // false
console.log( null == '' )        // false
console.log( null == NaN )       // false

console.log( undefined == 0)   // false
console.log( undefined == '')  // false
console.log( undefined == NaN) // false

console.log( 0 == '' )  // true
console.log( 0 == NaN ) // false
```

### ===操作符
- 要是两个值类型不同，返回false 
- 要是两个值都是number类型，并且数值相同，返回true 
- 要是两个值都是stirng，并且两个值的String内容相同，返回true 
- 要是两个值都是true或者都是false，返回true 
- 要是两个值都是指向相同的Object，Arraya或者function，返回true 
- 要是两个值都是null或者都是undefined，返回true


## 不要省略分号
> 每个语句必须以分号结尾。不允许依赖于JS自动添加分号的功能。

```
// bad
let luke = {}
let leia = {}
[luke, leia].forEach(jedi => jedi.father = 'vader')
// good
let luke = {};
let leia = {};
[luke, leia].forEach((jedi) => {
  jedi.father = 'vader';
});
```

## 不推荐代码水平对齐
> 对代码进行水平对齐会在代码中添加若干多余的空格，这让相邻两行的字符看上去处于一条垂直线上。

```
// bad
{
  tiny:   42,  
  longer: 435, 
};
// good
{
  tiny: 42, 
  longer: 435,
};
```

## 尽可能避免使用var
> 使用const或let来声明所有局部变量。如果变量不需要被重新赋值，默认应该使用const。应该拒绝使用关键字var。

```
// bad
var example = 42;
// good
const example = 42;
```

## 多多使用箭头函数
> 箭头函数提供了一种简洁的语法，并且避免了一些关于this指向的问题。相比较与function关键字，开发者应该优先使用箭头函数来声明函数，尤其是声明嵌套函数。


```
// bad
[1, 2, 3].map(function (x) {
  const y = x + 1;
  return x * y;
});

// good
[1, 2, 3].map((x) => {
  const y = x + 1;
  return x * y;
});
```

## 使用模板字符串取代连接字符串
> 在处理多行字符串时，模板字符串比复杂的拼接字符串要表现的更出色。

```
// bad
function sayHi(name) {
  return 'How are you, ' + name + '?';
}

// bad
function sayHi(name) {
  return ['How are you, ', name, '?'].join();
}

// bad
function sayHi(name) {
  return `How are you, ${ name }?`;
}

// good
function sayHi(name) {
  return `How are you, ${name}?`;
}
```

### 不要使用eval语句, 除非你明确知道自己在做什么
> 除非是在code loader中，否则不用使用eval或是Function(...string)结构。这个功能具有潜在的危险性，并且在CSP环境中无法起作用。MDN中有一节专门提到不要使用eval语句

```
// bad
let obj = { a: 20, b: 30 };
let propName = getPropName();  // returns "a" or "b"
eval( 'var result = obj.' + propName );
// good
let obj = { a: 20, b: 30 };
let propName = getPropName();  // returns "a" or "b"
let result = obj[ propName ];  //  obj[ "a" ] is the same as obj.a
```

### 常量的命名规范
> 常量命名应该使用全大写格式，并用下划线分割
> 如果你确定一定以及肯定一个变量值以后不会被修改，你可以将它的名称使用全大写模式改写，暗示这是一个常量，请不要修改它的值。
> 遵守这条规则时需要注意的一点是，如果这个常量是一个函数，那么应该使用驼峰式命名法。

```
// bad
const constNumber = 5;
// good
const CONST_NUMBER = 5;
```

### 每次只声明一个变量
> 每一个变量声明都应该只对应着一个变量。不应该出现像let a = 1,b = 2;这样的语句。

```
// bad
let a = 1, b = 2, c = 3;
// good
let a = 1;
let b = 2;
let c = 3;
```

### 使用单引号
> 只允许使用单引号包裹普通字符串，禁止使用双引号。如果字符串中包含单引号字符，应该使用模板字符串。
> 这个规则在typescript中也是这样的。或者有人觉得ts更像Java。但是，请记住typescript依旧是JavaScript。所以我们还是应该保持与JavaScript的一致性。否则在写HTML字符串拼接的时候。你会痛苦的。并且在于.js文件混合时。这两种方式会让人烦躁。


```
// bad
let directive = "No identification of self or mission."
// bad
let saying = 'Say it ain\u0027t so.';
// good
let directive = 'No identification of self or mission.';
// good
let saying = `Say it ain't so`;
```

### delete的使用
> 可以用。但是不是很推荐

```
// not recommend
delete window.variate;
// good
window.variate = null;
```

### If永远使用括号
> 如果你的if判断只有一句。也请用{}包裹起来。

```
// bad
if (true) return a = 1;
// good
if (true) {
    return a = 1;
}
```