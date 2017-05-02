# border笔记

1. border-width不支持百分比
2. border-width支持关键字 thin：1px medium：3px thick 5px border-width默认值是medium3px因为borderstyledouble至少3px才有效果
## border-style类型
1. silod
2. dashed
3. dotted
4. double,计算规则
默认下是1+1+1
1px 0+1+0
2px 1+0+1
3px 1+1+1
4px 1+2+1
5px 2+1+2
6px 2+2+2
7px 2+3+2
5. inset 内凹，基本没有使用场景，兼容性差，风格过时

## border-color 和 color
1. border-color就是color，当没有指定border-color时，会使用color作为边框色，没有指定color时，字的颜色不继承border-color
2. 用途 hover与图形变色，transition时也可以只transition一个color
## border与background定位
1. background-position定位默认是相对于左上角定位的。想背景相对于右下角。实现方式：给右边框一个透明宽度，因为100%右侧定位不计算border区域

      border-right:50px solid transparent;
      background-postion:100% 40px;
## border与三角等图形

1. dotted ie7/ie8圆角
2. double 三道杠图标
3. solid 三角和梯形
## border与透明边框
始于ie7，兼容性好

