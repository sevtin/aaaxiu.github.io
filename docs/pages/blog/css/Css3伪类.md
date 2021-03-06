# CSS3伪类
<br />

> css3 中添加了很多了伪类选择器，这里要讲的主要是 `:nth-of-type()` 和 `:nth-child()` 。因为经常会出现两个选择器的功能不清楚，或者设置样式无效的问题。

### :nth-child()

> MDN: :nth-child(an+b) 这个 CSS 伪类首先找到所有当前元素的兄弟元素，然后按照位置先后顺序从1开始排序，选择的结果为 CSS 伪类 `:nth-child` 括号中表达式（an+b）匹配到的元素集合（n=0，1，2，3...）。

先来一个直接的栗子：

``` html
<span>1</span>
<p>2</p>
<p>3</p>
<span>4</span>
<p>5</p>
```
 
``` css
/* 匹配 p 元素的所有兄弟元素，从第二个元素开始（包含第二个）后面的所有 p 元素 */
/* 效果：2，3，5 高亮 */
p:nth-child(n + 2) {
  color: lime;
}
```


### :nth-of-type()

借用上面的 DOM 在来看看 :nth-of-type() 的效果。

``` css
/* 匹配 p 元素所有的兄弟 p 元素，从第二个 p 元素开始（包含第二个）后面所有的 p 元素 */
/* 效果：3，5 高亮 */
p:nth-of-type(n + 2) {
  color: lime;
}
```

从这个例子可以看出：**虽然它们渲染的都是 p 元素的样式**。但两个选择器还是有区别的：

+ `:nth-child()` 匹配的是所有当前元素的兄弟元素，然后按照位置先后顺序从 1 开始排序；
+ `:nth-of-type()` 匹配的是所有当前元素**同类型的兄弟元素**，然后排序。 

::: warning
需要注意的是，DOM 节点是从1开始排序的，而 n 是从0开始赋值的。也就是说，假若像上面代码这样的需求：需要设置后几位 DOM 的样式，n + 1 是等效于 n 的，因为没有第零号元素。
:::





<Vssue :title="$title" />
