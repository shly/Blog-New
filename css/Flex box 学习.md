# Flex box 学习

  Flexbox模块提供了一个有效的布局方式，即使不知道视窗大小或者未知元素情况之下都可以智能的，灵活的调整和分配元素和空间两者之关的关系。
  简单的理解，就是可以自动调整，计算元素在容器空间中的大小。
  ## 创建
  通过给父元素设置display:flex或display:inline-flex创建Flex box格式化上下文（FFC）。之后，父元素成为一个Flex容器，其内部的元素都变为Flex项目，即使原来是行内元素。
  ## 属性
   ### Flex容器的属性
   flex-direction || flex-wrap || flex-flow || justify-content || align-items || align-content
   ### Flex项目的属性
   order || flex-grow || flex-shrink || flex=basis
  ## 备注
  justify-content 相当于主轴上的align
  align-items和 align-content 相当于侧轴上的align <b> align-items作用于单行元素， align-content作用于多行元素</b>，即如果flex项目有多行时，align-content起作用，align-items不起作用，反之亦然。
  
  
  

 
