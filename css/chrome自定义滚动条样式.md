# chrome自定义滚动条样式
滚动条的组成

     ::-webkit-scrollbar         滚动条整体部分
     ::-webkit-scrollbar-thumb             滚动条里面的小方块，能上下左右移动（取决于是垂直滚动条还是水平滚动条）
     ::-webkit-scrollbar-track      滚动条的轨道（里面装有thumb）
     ::-webkit-scrollbar-button      滚动条轨道两端的按钮，允许通过点击微调小方块的位置
     ::-webkit-scrollbar-track-piece    内层轨道，滚动条中间部分（除去）
     ::-webkit-scrollbar-corner     边角，及两个滚动条的交汇处
     ::-webkit-resizer       两个滚动条的交汇处上用于通过拖动调整元素大小的小控件
     
 自定义滚动条示例

    /*定义滚动条宽高及背景，宽高分别对应横竖滚动条的尺寸*/
    .scrollbar::-webkit-scrollbar{
        width: 16px;
        height: 16px;
        background-color: #f5f5f5;
    }
    /*定义滚动条的轨道，内阴影及圆角*/
    .scrollbar::-webkit-scrollbar-track{
        -webkit-box-shadow: inset 0 0 6px rgba(0,0,0,.3);
        border-radius: 10px;
        background-color: #f5f5f5;
    }
    /*定义滑块，内阴影及圆角*/
    .scrollbar::-webkit-scrollbar-thumb{
        /*width: 10px;*/
        height: 20px;
        border-radius: 10px;
        -webkit-box-shadow: inset 0 0 6px rgba(0,0,0,.3);
        background-color: #555;
    }
