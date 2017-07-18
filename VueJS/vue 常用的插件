# vue 常用的插件
1. http-server 本地启动一个服务器
2. vue-clipboard2 剪贴板等辅助功能
3. highlighter.js 在vue中的使用如下：

            import hljs from 'highlight.js'
            import 'highlight.js/styles/googlecode.css'
            Vue.directive('highlight', function (el) {
            let blocks = el.querySelectorAll('pre code')
            blocks.forEach((block) => {
              hljs.highlightBlock(block)
            })
            })
            
            <p v-highlight>
            <pre>
              <code v-html="markdownhtml">
              </code>
            </pre>
            </p>
