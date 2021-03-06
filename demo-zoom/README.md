jQuery--放大镜插件
---
预览地址: [放大镜](https://alcantara6.github.io/demo-component/demo-zoom/zoom.html)，[图片异步加载的测试](https://alcantara6.github.io/demo-component/demo-zoom/analyse_of_image_loading.html)  
[博客：用jQuery编写放大镜效果以及图片异步加载的测试](http://blog.csdn.net/alcantara/article/details/78117956 '点击查看博文')这是一篇关于本人编写的放大镜demo的详细博文，包含对关键点、bug的分析，以及针对图片异步加载的测试。  
![放大镜插件效果图](./images/demo展示效果.jpg '效果图')  

#### 插件使用方法
1. html结构为
    ```html
    /* 缩略图和放大图都放在./images文件夹，a中的href为大图地址、img中的src为小图地址 */
    <div id="product-zoom">
      <a href="" title="">
        <img src="" alt="">
      </a>
    </div>
    ```
2. `<script>`内：选择缩略图div: $("#product-zoom"),调用插件封装的zoom()方法，传入参数：缩略图宽度尺寸(默认320px)和放大镜尺寸(默认120px)
    ```javascript
    $('#product-zoom').zoom({
        thumbWidth: 300,
        zoomSize: 100
    });
    ```
    
#### 项目特点
1. 封装为插件，添加任意尺寸图片都可使用。
2. 函数封装良好，代码层次清晰、简洁，总共不足70行（还可再优化）。
3. 使用jQuery定位方法，图片自适应窗口大小。

#### 技术应用
* jQuery定位放大镜元素：`outerWidth()`, `outerHeight()`, `width()`,`height()`,`offset`, `event.pageX`, `event.pageY`,
* 创建、插入、移除放大镜、放大图：创建jQuery对象`$(HTML)`、jQuery对象插入DOM `appendTo()`、`show()`、`hide()`、`remove()`
* 图片的load事件：`$('img').on('load', callback)` 在图片加载完成后执行回调函数
* 放大镜位置和放大图位置：`Math.min(Math.max(a,b),c)`方式计算
* 放大镜鼠标事件：阻止冒泡，`mouseenter()`, `mousemove()`注意绑定元素，`mouseleave()`注意鼠标是否能离开放大镜