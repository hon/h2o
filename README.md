# h2o
a css framework

Guide
=====

前言
----
1. 定义css和html的规范，最小限度实现UI
2. 提供扩展机制, 充分利用css

CEM(Component Element Modifier)，基于[RSCSS(https://github.com/rstacruz/rscss "R
--------------------------------------------------------------------------------
SCSS")], 并集合BEM, SMACSS, OOCSS进行了扩展。
-------------------------------------------
##扩展目标
  - 提高开发效率;
  - 提高加载速度;
  - 提高执行效率.

##说明
BEM的意义
  1. 模块化css
  2. 避免命名冲突
  3. 提高了浏览器的解析速度
BEM的缺点
  1. 繁琐，写法冗余
  2. 基于前一点，影响开发速度
  3. 页面数据增多

CSS本身就有命名空间的特点：
```css
.text.gray{
  color: red;  /*红色文字*/
}
.button.gray{
  color: gray  /*灰色文字按钮*/
}
.modal .title{
  color: red;  /*弹窗标题*/
}
```

```stylus
  .parent
    //浏览器解析器，从右向左解析，层级不易过深
    &.modifier
    .children
    > .direct-children
```

解决办法
  1. shadow dom
  2. web component
  3. css module
目前能支持很好支持的方式是css module

结合bem和css命名空间的优点
  1. bem 避免了命名冲突，优化了渲染速度
  2. css命名空间的优点：简洁，结构性强

如何解决
 1. 在写法上任然使用常规css的方式, 充分利用css命名空间的优点
 2. 在开发环境，没有太多的性能需求， 到生产环境，可以通过postcss生成最终的css文件
 3. html中的class命名
   3.1 传统html文件，可通过node进行处理和优化
   3.2 js生成的dom, 如react可在开发是进行声明
   3.3 考虑不进行css module解析的类名，css文件中不包含该类名，则dom里的类名也不进行hash
   [react-css-modules] (https://github.com/gajus/react-css-modules)
   [posthtml-postcss-modules] (https://github.com/posthtml/posthtml-postcss-modules)
   [posthtml-css-modules] (https://github.com/posthtml/posthtml-css-modules)
 4. 在写法上是module-css去兼容css, 而不是相反。写css的时候，没有必要考虑module_css的规则，
    否则会增加使用难度
 5. 将css进行module_css进行转换，应该有外部工具去做，而不在本css框架内， 否则会限制本
    框架的适用范围


## 命名指南
命名统一使用小写字母, 多个字母用一个中线链接, 在语义明确，且单词过长的情况下可进行缩写，
比如：implement -> impl, button -> btn等
```html
  <div class="SearchBox">
    <input type="input" name="name" value="" class="input">
    <button class="button searching is-disabled red">搜索</button>
  </div>
  <div class="Card article">
    <h3 class="title recommend">Article title</h3>
    <article class="content">
      Article title
    </article>
  </div>
```

- Component: 将一系列的UI当成组件来对待，组件名推荐单词首字母大写，如：
  * 搜索框：  .SearchBox
  * 文章卡片  .article.card 或 .Card.article, 但推荐使用第二种，顺序应该也能表示层级
    关系
- Element: 组件元素
  * 搜索按钮         .SearchBox .button
  * 文章卡片标题     .Card.article .title
- Modifier: 修改
  * 红色搜索按钮    .SearchBox button.red
  * 正在搜索中      .SearchBox button.searching
  * 推荐标题        .Card.article .recommend
  * 禁止搜索 .SearchBox button.is-disabled


命名空间
-------
t-  theme 皮肤，不同应用的长相
u-  utils 某些功能性的，和特定ui不相关的css语句
l-  layout 布局
js- javascript  类名被js使用, 但通常情况下，应该适用id, 而不是class
o-  object  不相关组件的通用样式，增加css的复用性
_   hack hack样式
is- status 表示某种状态

ITCSS
-----
Settings:   Global variables, config switches, brand colors, etc;
Tools:      default mixins and functions;
Generic:    ground-zero styles (normalize.css, resets, box-sizing)
Base:       unclassed html elements(type selectors);
Objects:    cosmetic-free design patterns;
Components: designed componets, chunks of ui
Trumps:     helpers and overides


CSS 语句声明顺序
---------------
```
  .selector {
    /* Display & Box Model */
    display: inline-block;
    overflow: hidden;
    box-sizing: border-box;
    width: 100px;
    height: 100px;
    padding: 10px;
    border: 10px solid #333;
    margin: 10px;

    /* Positioning */
    position: absolute;
    z-index: 10;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;

    /* Other */
    background: #000;
    color: #fff;
    font-family: sans-serif;
    font-size: 16px;
    text-align: right;
  }
```

# 设计和模块化理念
  atomic-design

# 处理器
  pre: stylus
  post: postcss

# 组件列表
## 基础(reset, modifier, utils)
## 元素(html中的基础元素)
  button
  table
  form
  radiobox
  checkbox
  select
  title
  box
  image
  font
  color
  code
  input
  media query
## 组件(页面中常用的组件)
  video
  icon
  tab
  modal
  card
  toggle
  checkbox
  radiobox
  range
  select
  menu
  message
  nav
  pagination
  panel
  autocomplete
  datepicker
  slider
  transfer
  carousel
  rate
  upload
  list
    tree
    menu
    dropdown
  badge
  accordion
  calendar
  tooltip
  notification
  scroller
  affix
  backtotop
  popover
  progress
  timeline
  breadcrumb
  steps
  spin


## 布局（layout, grid模板）
## 页面(theme, 主题)


# 扩展

# 工具


#Links
[Css Namespace](http://csswizardry.com/2015/03/more-transparent-ui-code-with-namespaces/)
[ITCSS](https://speakerdeck.com/dafed/managing-css-projects-with-itcss)
[Rscss](https://github.com/rstacruz/rscss)
[TitleCss](https://github.com/cuth/Title-CSS)
[Suitcss](https://github.com/suitcss/suit)
[SMACSS](https://smacss.com/)
[OOCSS](http://oocss.org/)
[Idiomatic Css](https://github.com/necolas/idiomatic-css)
[Atomic OOBEMITSCSS](http://www.sitepoint.com/atomic-oobemitscss/)
[cssguidelin](http://cssguidelin.es/)
[poormansstyleguide](http://www.poormansstyleguide.com/?browser=&points=6)
[html vocabulary](http://apps.workflower.fi/vocabs/html/en#attribute-name)
[High performance HTML](https://samdutton.wordpress.com/2015/04/02/high-performance-html/?utm_source=ourjs.com)
[CSS, SVG & UI Addict](http://iamvdo.me/en)
