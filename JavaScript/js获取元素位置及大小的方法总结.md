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
5. Element.getBoundingClientRect()
返回元素的大小及其相对于视口的位置。
返回值是一个 DOMRect 对象，这个对象是由该元素的 getClientRects() 方法返回的一组矩形的集合, 即：是与该元素相关的CSS 边框集合 。

DOMRect 对象包含了一组用于描述边框的只读属性——left、top、right和bottom，单位为像素。除了 width 和 height 外的属性都是相对于视口的左上角位置而言的。
ele.getBoundingClientRect() => {top: 130, right: 390, bottom: 390, left: 130, width: 260}
当浏览器窗口有滚动时
window.scrollY = 143
ele.getBoundingClientRect() => {top: -13, right: 390, bottom: 247, left: 130, width: 260}
