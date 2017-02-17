# notes
http://www.cnblogs.com/Nightsky-Dec/p/5864160.html

# 关于document.wirte的笔记
使用这个方法会碰到两个状态：1、添加内容到页面中；2、重写页面

页面在生成时有一个输入流的状态。在页面加载时这个状态是自动打开的，这时内容会从上至下添加内容。

此时调用document.write会把内容写进页面里面，但我们不能准确控制加载的位置，只能根据write()方法调用的位置使其内容放入页面大概的位置。
而当页面加载完成后即window.onload后，会自动的运行document.close()方法关闭这个输入流，如果此时我们再运行document.write会打开一个新的输入流在页面，此时会重写页面。
