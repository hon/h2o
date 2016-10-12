# h2o
a css framework

Guide
=====

前言
----
定义css和html的规范，最小限度实现UI

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
.text .gray{
  color: red;  /*红色文字*/
}
.button .gray{
  color: gray  /*灰色文字按钮*/
}
```

解决办法
  1. shadow dom
  2. web component
  3. css module

BEM通过--和__区分Block, Element和Modifier

本命名指南通过Component, Element和Modifier命本事对三者进行区分，各部分通过-连接
三者之间的关系可以通过DOM或CSS信息进行区分。

指南中的“高效写法”指“现阶段”浏览器解析高效
“低效写法”指“现阶段”解析高效，但兼容未来的css或其他规范（解决办法）

## 命名指南
- Component: 将一系列的UI当成组件来对待，用'-'分割单词，如：
  * 喜欢按钮  .like-button
  * 搜索表单  .search-form
  * 文章卡片  .article-card
- Element: 组件元素, 由组件名和元素名组成
  * 喜欢按钮图标     .like-button-icon
  * 搜索表单提交按钮 .search-form-button
  * 文章卡片标题     .article-card-title
- Modifier: 修改
  * 高效写法(推荐)    .message--alert, .message--warn
  * 低效写法(不推荐)  .message .alert, .message .warn
- State：  状态
  * 高效写法 .like-button-is-liked, .like-button-has-liked
  * 低效写法 .like-button .is-liked .like-button .has-liked

命名空间
-------
t-  theme 皮肤，不同应用的长相
u-  utils 某些功能性的，和特定ui不相关的css语句
l-  layout 布局
js- javascript  类名被js使用
o-  object  不相关组件的通用样式，增加css的复用性
_   hack hack样式


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
