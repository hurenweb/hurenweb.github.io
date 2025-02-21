# vNote使用教程

> 20250220周四

一个舒适的笔记平台！  
VNote是开源的，源代码托管在GitHub。  
[官网](https://app.vnote.fun/zh_cn/)
[github地址](https://github.com/vnotex/)
vnote不支持修改markdown编辑区的行高。
主题定制，自己在月夜的基础上，定制了月夜湖人`moonlight-h`。

# 对比其它笔记软件

+ Effie，收费，目录不方便。
+ MarkText，也不习惯，有很多设置，没有中文版。
+ 有道云笔记，不稳定，不是实时预览的。
+ 语雀，收费，不方便导出。

# 设置菜单的文字大小

代码如下：
```css
// interface.qss
QWidget {
    font-size: 15px;
}
```

# 设置标题的颜色

色值参考`layui.dev`网站。
代码如下：
```cpp
// text-editor.theme
"H2" : {
    "text-color" : "#ffb800"
},
```
