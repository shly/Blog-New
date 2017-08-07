首先看这样一个盒子

        .box{
              border: 10px solid red;
              width: 200px;
              height: 200px;
              padding: 20px;
              margin: 30px;
              position:absolute;
              top:100px;
              left:100px;
            }
            
接下来通过这个例子说明几种获取位置及大小的方式
一 client

1. Element.clientTop
  一个元素顶部边框的宽度（以像素表示）。不包括顶部外边距或内边距。clientTop 是只读的。
在这个例子中
    ele.clientTop => 10px
2. Element.clientLeft
表示一个元素的左边框的宽度，以像素表示。如果元素的文本方向是从右向左（RTL, right-to-left），
并且由于内容溢出导致左边出现了一个垂直滚动条，则该属性包括滚动条的宽度。clientLeft 不包括左外边距和左内边距。clientLeft 是只读的。
    ele.clientLeft => 10px
3. Element.clientHeight
返回元素内部的高度(单位像素)，包含内边距，但不包括水平滚动条、边框和外边距。
    ele.clientHeight => 240px    (height+padding*2)
4. Element.clientWidth
表示元素的内部宽度，以像素计。该属性包括内边距，但不包括垂直滚动条（如果有）、边框和外边距。
该属性值会被四舍五入为一个整数。如果你需要一个小数值，可使用 element.getBoundingClientRect()。
     ele.clientWidth => 240px  (width + padding*2)
     
二 getClientRects

1. Element.getBoundingClientRect()
返回元素的大小及其相对于视口的位置。
返回值是一个 DOMRect 对象，这个对象是由该元素的 getClientRects() 方法返回的一组矩形的集合, 即：是与该元素相关的CSS 边框集合 。

DOMRect 对象包含了一组用于描述边框的只读属性——left、top、right和bottom，单位为像素。除了 width 和 height 外的属性都是相对于视口的左上角位置而言的。
ele.getBoundingClientRect() => {top: 130, right: 390, bottom: 390, left: 130, width: 260}
当浏览器窗口有滚动时
window.scrollY = 143
ele.getBoundingClientRect() => {top: -13, right: 390, bottom: 247, left: 130, width: 260}

三 offset

1. HTMLElement.offsetHeight
它返回该元素的像素高度，高度包含该元素的垂直内边距和边框，且是一个整数。
ele.offsetHeight => 260px     (height + padding-left + padding-right + border-left + border-right + 水平滚动条的高度)
<span color="red">offsetHeight与clientHeight的区别是clientHeight不包含边框和水平滚动条</span>

2. HTMLElement.offsetWidth 与offsetHeight类似

3. HTMLElement.offsetParent

返回一个指向最近的（closest，指包含层级上的最近）包含该元素的定位元素。如果没有定位的元素，则 offsetParent 为最近的 table cell 元素对象或根元素（标准模式下为 html；quirks 模式下为 body）。当元素的 style.display 设置为 "none" 时，offsetParent 返回 null。offsetParent 很有用，因为 offsetTop 和 offsetLeft 都是相对于其内边距边界的。
ele.offsetParent => <body>...</body>

4. HTMLElement.offsetLeft

ele.offsetLeft => 130
返回当前元素左上角相对于HTMLElement.offsetParent 节点的左边界偏移的像素值。

5. HTMLElement.offsetTop
返回当前元素相对于其 offsetParent 元素的顶部的距离。

ele.offsetTop => 130

四 scroll

1. Element.scrollTop
可以设置或者获取一个元素距离他容器顶部的像素距离

2. Element.scrollLeft
可以读取或设置元素滚动条到元素左边的距离。

3. Element.scrollHeight
是计量元素内容高度的只读属性，包括overflow样式属性导致的视图中不可见内容。没有垂直滚动条的情况下，scrollHeight值与元素视图填充所有内容所需要的最小值clientHeight相同。包括元素的padding，但不包括元素的margin.

4. Element.scrollWidth
元素的scrollWidth只读属性以px为单位。返回元素的内容区域宽度或元素的本身的宽度中更大的那个值。若元素的宽度大于其内容的区域（例如，元素存在滚动条时）, scrollWidth的值要大于clientWidth。

