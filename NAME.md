**文件夹命名**
- 项目文件夹全部使用**kabab-case**命名方式
- 打包文件夹： build
- 配置文件夹: config
- 源码文件夹： src
- 样式文件夹： css、scss、less、sass
- 图片文件夹： img
- 静态资源文件夹: static
- 视图文件夹: views
- 插件文件夹: plugins
- 组件文件夹: components

 
```
// bad
    folderName

// good
    folder
    folder-name
```

**js文件命名**
- .js文件使用kabab-case命名方式。
- 类文件使用CamelCase命名方式

```
// bad
    jsName.js
// good
    javascript.js
    my-javascript.js
    Class.js
```

**html文件命名**
- html文件使用kabab-case命名方式.包含(.html | .htm)

```
    my.html
    my-html.html
    my.htm
    my-html.htm
```

**style**
- style文件使用kabab-case命名方式.包含(.css | .less | .scss | sass )

```
    my.css
    my-style.css
    my.less
    my-style.less
    my.scss
    my-style.scss
    my.sass
    my-style.sass
```

**ts文件命名**
- typescript文件使用kabab-case命名方式.包含(.ts | .tsx | .d.ts)

```
    my.ts
    my-ts.ts
    my.tsx
    my-ts.tsx
    my.d.ts
    my-ts.d.ts
```

** img文件命名
> 图片命名建议遵循： [图片业务]-图片功能类别-[图片模块名称]-[图片精度]


- 图片业务：
    - tb_：淘宝
    - wx_：微信
    - sq_：手Q
    - jd_：京东商城
    - …

- 图片功能类别：
    - icon：模块类固化的图标
    - logo：LOGO类
    - spr：单页面各种元素合并集合
    - btn：按钮
    - bg：可平铺或者大背景
    - …

- 图片模块名称：
    - goodslist：商品列表
    - goodsinfo：商品信息
    - useravatar：用户头像
    - …

- 图片精度：
    - 普清：@1x
    - Retina：@2x | @3x
    - …

```
// good
tb-btn-goodlist@2x.png
wx-btn-goodlist.png
btn-goodlist.png 
```