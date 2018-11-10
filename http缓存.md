一 与缓存相关的一些字段：
1. cache-control: max-age no-cache no-store 
2. etag/if-none-match
3. last-modified/if-modified-since
4. expires

二 http缓存大致可以分为两种，强缓存和协商缓存。

http判断是否使用缓存流程：
 浏览器发送请求之前，会根据Cache-control:max-age=xxxxx 或expires (同时存在时max-age覆盖或expires)判断是否命中强缓存，
  1. 没有过期，命中强缓存，从缓存中取资源，返回200
  2. 过期
    2.1 判断是否有etag， 有则发送请求，携带if-none-match，服务器端对比
       2.1.1 相同则返回304
       2.1.2 不相同返回新资源，200
    2.2 没有etag判断是否有last-modified，没有则返回新资源200，有则发送请求携带if-modified-since
       2.2.1 没有修改则返回304
       2.2.2 有修改返回新资源200
 https://www.cnblogs.com/wonyun/p/5524617.html
