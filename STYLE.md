## 设置合适的属性声明顺序
> 作为最佳实践，我们应该遵循以下顺序声明样式：
> - 结构性属性
>> 1. display
>> 2. position, left, top, right etc.
>> 3. overflow, float, clear etc.
>> 4. margin, padding
> - 表现型属性
>> 1. background, border etc.
>> 2. font, text

```
// good
.box {
  display: block;
  position: absolute;
  left: 30%;
  right: 30%;
  overflow: hidden;
  margin: 1em;
  padding: 1em;
  background-color: #eee;
  border: 3px solid #ddd;
  font-family: 'Arial', sans-serif;
  font-size: 1.5rem;
  text-transform: uppercase;
}
```

## 合理的使用ID
> 一般情况下ID不应该被用于样式，并且ID的权重很高，所以不使用ID解决样式的问题，而是使用class

```
// bad
#content .title {
  font-size: 2em;
}

// good
.content .title {
  font-size: 2em;
}
```

## css选择器中避免使用标签名
> 从结构、表现、行为分离的原则来看，应该尽量避免css中出现HTML标签，并且在css选择器中出现标签名会存在潜在的问题。

```
// bad
input, div {
    color: red;
}
```

## 使用子选择器
> css结构尽量使用**直接子选择器**。否则这会很耗费性能已经会导致令人头疼的设计问题。

```
// bad
.content .title {
  font-size: 2rem;
}

// good
.content > .title {
  font-size: 2rem;
}
```

## 尽量使用缩写属性
> 尽量使用缩写属性对于代码效率和可读性是很有用的.

```
// bad
border-top-style: none;
font-family: palatino, georgia, serif;
font-size: 100%;
line-height: 1.6;
padding-bottom: 2em;
padding-left: 1em;
padding-right: 1em;
padding-top: 0;

// good
border-top: 0;
font: 100%/1.6 palatino, georgia, serif;
padding: 0 1em 2em;
```

## 0后面不带单位

```
// bad
padding-bottom: 0px;
margin: 0em;

// good
padding-bottom: 0;
margin: 0;
```