## windows下启动Nginx的方式  
   Nginx安装目录下运行 start nginx
## 启动之后闪退，查看log报如下错误
2017/03/17 13:51:11 [emerg] 4504#4656: CreateFile() 
"D:\安装包\nginx-1.10.3/conf/nginx.conf" failed (1113: 
No mapping for the Unicode character exists in the target multi-byte code page)
解决方案： 因为安装目录中有中文，故使安装路径都是中文即可
## 修改路径之后仍然闪退，报如下错误
2017/03/17 13:59:41 [emerg] 9084#12628: "root" directive is duplicate in D:\nginx-1.10.3/conf/nginx.conf:46
