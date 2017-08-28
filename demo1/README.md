# iframe的一些属性

## iframe 
## child.html是最简单的iframe嵌套

## 以下是一些属性

### iframe好像自带box-sizing:border-box属性

- src 嵌套页面的URL地址。使用遵守同源策略的  'about:blank' 来嵌套空白页。
- srcdoc 该属性值可以是HTML代码，这些代码会被渲染到iframe中，如果同时指定了src属性，srcdoc会覆盖src所指向的页面。该属性最好能与sandbox和seamless属性一起使用。
- height 以CSS像素格式HTML5，或像素格式HTML 4.01，或百分比格式指定frame的高度。(ps:百分比好像不起作用。。)
- width  以CSS像素格式HTML5，或以像素格式HTML 4.01，或以百分比格式指定frame的宽度。
- frameboder 取值为1时（默认值），告诉浏览器在当前iframe与其他iframe之间绘制边框，取0时则无需绘制此边框。
- marginheight 框架内容到框架的上下边距，以像素格式表示。 //类似于上下padding     
- marginwidth 框架内容到框架的左右边距，以像素格式表示。
- scrolling 三个值 auto yes no
- allowfullscreen 设置全屏属性 谷歌 和火狐对应不同api
- name 嵌入的浏览上下文（框架）的名称。该名称可以用作<a>标签，<form>标签的target属性值，或<input> 标签和 <button>标签的formtaget属性值。
- sandbox ...
- seamless 没明白。。。