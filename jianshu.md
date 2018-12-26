#CSS布局
今天介绍CSS布局的几个小技巧，首先是左右布局：
##左右布局/左中右布局
我们写出来的两个元素（例如两个div）默认是上下布局，要想转变成左右布局，可以在CSS文件里给这两个元素都加上```float:left;```，这样这两个元素会放到同一行里向左靠齐。但是，这时会出现一个bug，那就是下一个元素，即使我们未调整该元素，下一个元素也会跳到这两个元素所在的那一行。为解决此bug，可以在这两个元素的父元素那加一句```class="clearfix;"```。
即，**固定搭配**：```float:left;```+```class="clearfix;"```。
另外，如果不想让这两个元素都向左靠齐，可以一个加```float:left;```，另一个加```float:right;```，一个向左一个向右。这种情况下也别忘了给父元素加```class="clearfix;"```。
以上我们用了两个元素实现了左右布局，假如是三个元素呢？那就是所谓的左中右布局了。
##水平居中
实现水平居中的效果之前，我们应该首先确认一下元素的类型。
如果是块级元素，且没有指定该元素的宽度，那该元素的默认占据一整行，那还居中个毛啊...所以，如果该元素是块级元素，首先在这个元素里加```display: inline-block;```，把这个元素转变成“内联元素”，让这个元素的宽度根据文档流的大小收缩。然而此时会出现bug：该元素的下面莫名其妙多出一行空隙，所以应该在该元素里加上```vertical-align: top;```。即，**固定搭配**：```display: inline-block;```+```vertical-align: top;```。
然后在该元素的**父元素**上加```text-align: center;```即可。
另外，将该元素是指定了宽度的块级元素，在**该元素**上加```margin: 0 auto;```也可以使元素居中。而在inline-block元素上加此语句没有居中效果。注意：```margin: 0 auto;```仅对该块元素起作用，而不居中块元素中的内容。
###text-align
```text-align``` 定义行内内容（例如文字）如何相对它的**块父元素**对齐。```text-align``` 并不控制块元素自己的对齐，只控制它的行内内容的对齐。（与```margin: 0 auto;```刚好相反）
```text-align```可能有以下取值：
```text-align: left;```
行内内容向左侧边对齐。
```text-align: right;```
行内内容向右侧边对齐。
```text-align: center;```
行内内容居中。
```text-align: justify;```
文字向两侧对齐，对最后一行无效。
```text-align: justify-all;```
和justify一致，但是强制使最后一行两端对齐。
```text-align: start;```
如果内容方向是左至右，则等于left，反之则为right。
```text-align: end;```
如果内容方向是左至右，则等于right，反之则为left。
```text-align: match-parent;```
和inherit类似，区别在于start和end的值根据父元素的direction确定，并被替换为恰当的left或right。
```<string>```
第一个出现的该（单字符）字符串被用来对齐。跟随的关键字定义对齐的方向。例如，可用于让数字值根据小数点对齐。

##垂直居中
1. ```height=line-height```可实现居中功能。
line-height 属性设置两段段文本之间的距离，也就是行高，如果我们把一段文本的line-height设置为父容器的高度就可以实现文本垂直居中了。
参考： https://segmentfault.com/a/1190000005122321 。
2. ```vertical-align:middle;```
虽然vertical-align属性只会在inline-block水平的元素上起作用，但是其影响到的元素涉及到inline属性的元素，这里千万记住，inline水平元素受vertical-align属性而位置改变等不是因为其对vertical-align属性敏感或起作用，而是受制于整个line box的变化而不得不变化的。
```vertical-align:middle;```是指该元素与父元素文本的中部对齐。
这一部分参考了 https://www.cnblogs.com/hykun/p/3937852.html 和 https://www.zhangxinxu.com/wordpress/2010/05/%E6%88%91%E5%AF%B9css-vertical-align%E7%9A%84%E4%B8%80%E4%BA%9B%E7%90%86%E8%A7%A3%E4%B8%8E%E8%AE%A4%E8%AF%86%EF%BC%88%E4%B8%80%EF%BC%89/ 。
3. ```background-position: center center;```，这一句通常用于背景图片的居中，第一个```center```是指水平方向的居中，第二个是指竖直方向的居中。


