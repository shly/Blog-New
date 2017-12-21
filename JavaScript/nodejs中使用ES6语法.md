1.安装babel依赖

    npm install babel-core --save-dev
    
2. 安装babel-register

    npm install babel-register --save-dev
    
3. babel转换配置,项目根目录添加.babelrc 文件

    {
     "presets" : ['es2015']
    }
    
4. 

    npm install babel-preset-es2015 --save-dev
 
5. 项目根目录添加入口文件 index.js

    require('babel-register');
